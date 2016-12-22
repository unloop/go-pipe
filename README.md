gopipe
=======
  
Golang pipe http response
  
## Installation and usage
 
The import path for the package is github.com/unloop/gopipe.
  
To install it, run: `go get github.com/unloop/gopipe`
  
## Example: pipe to http.ResponseWriter
  
```go
package main

import (
  "github.com/unloop/gopipe"
  "net/http"
  "io"
)


func handler(w http.ResponseWriter, r *http.Request) {

  var readCloser io.ReadCloser

  /* do something */

  defer readCloser.Close()
	
  /* do something */

  stream.New(w).SetBuffer(2048).Pipe(&readCloser)

  return
}

func main() {
  http.HandleFunc("/", handler)
  http.ListenAndServe(":3000", nil)
}
``` 

## Example: pipe to stdout

  
```go
package main

import (
  "github.com/unloop/gopipe"
  "io"
  "fmt"
)

type Writer struct {
	io.Writer
}

func (Writer) Write(p []byte) (int, error) {
	return fmt.Print(string(p))
}

func main() {

  var readCloser io.ReadCloser

  /* do something */

  defer readCloser.Close()
	
  /* do something */

  stream.New(Writer{}).Pipe(&readCloser)

  return
}
```
