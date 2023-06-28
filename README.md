# Logger Package
The `logger` package provides a logging utility that allows you to log messages with different severity levels. It includes features for structured logging.
## Usage

1. In your project, open a terminal or command prompt and navigate to the root directory of your Go project.

2. Use the `go get` command followed by the import path to download the package and its dependencies. For example, if the import path is `github.com/passon-engineering/sw-go-logger-lib`, run the following command:
   ```
   go get github.com/passon-engineering/sw-go-logger-lib
   ```

3. After running `go get`, Go will download the package and its dependencies and store them in your local Go workspace.

4. In your Go code, you can import the package using the import path you identified earlier. For example:
   ```go
   import "github.com/passon-engineering/sw-go-logger-lib/logger"
   ```

5. You can now use the functions, types, and other elements provided by the external package in your own code.

### Creating a Logger
To create a new logger instance, use the `NewLogger` function:

```go
	logger := NewLogger([]LogFormat{TIMESTAMP, STATUS, PRE_TEXT, HTTP_REQUEST, ID, SOURCE, DATA, ERROR, PROCESSING_TIME})
```

* Create only one logger object in your project and pass it's reference to your modules. 

### Logging Messages
To log a message, use the `Entry` method of the logger instance:

```go
// Start a time counter from here
startTime := time.Now()

// DO HERE SOME OPERATIONS - USER CODE HERE

// Define and prepare the logger container based on your operations result 
// It is also allowed that a field is left blank or not be considered
// Create a log entry container
container := Container{
    Status:       logger.STATUS_INFO,
    PreText: 	  "SERVER1",
    HttpRequest:  r,
    Id: 		  "5f322ac4ba",
    Source:		  "handler/user",
    Data: 		  "233",	
    Error: 		  "something went wrong",
    ProcessingTime: time.Since(start), // Takes elapsed time since start Time
}

// Necessary to finally write log
logger.Entry(container)
```

Another example:

```go
// Start a time counter from here
startTime := time.Now()

// DO HERE SOME OPERATIONS - USER CODE HERE

// Define and prepare the logger container based on your operations result 
// It is also allowed that a field is left blank or not be considered
container := logger.Container{
    Status:        logger.STATUS_INFO,
    Id:             "fafeeb13",
    Source:         "/handler/users",
    ProcessingTime: time.Since(start), // Takes elapsed time since start Time
    HttpRequest:    r,
}

// Necessary to finally write log
logger.Entry(container)
```

The `Container` struct contains the necessary information for the log entry.

The log message will be printed according to the severity level set during the logger creation. If the severity is set to `NONE`, the message will be ignored.

### Log Output
The log output will be printed to the standard output, file or both. 
## Contributing
Contributions to the logger package are welcome! If you find any issues or have suggestions for improvement, please open an issue or submit a pull request.