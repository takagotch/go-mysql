### go-mysql
---
https://github.com/siddontang/go-mysql

```
```

```go
import (
  "gothub.com/siddontang/go-mysql/replication"
  "os"
)

cfg := replication.BinlogSyncerConfig {
  ServerID: 100,
  Flavor: "mysql",
  Host: "127.0.0.1",
  Port: 3306,
  User: "root",
  Password: "",
}
syncer := replication.NewBinLogSyncer(cfg)

streamer, _ := syncer.StartSync(mysql.Position{binlogFile, binlogPos})

for {
  ev, _ := streamer.GetEvent(context.Backgrond())
  
  ev.Dump(so.Stdout)
}

for {
  ctx, cancel := context.WithTimeout(context.Background(), 2*time.Second)
  ev, err := s.GetEvent(ctx)
  cancel()
  
  if err == context.DealineExceeded {
    continue
  }
  
  ev.Dump(os.Stdout)
}


cfg := NewDefaultConfig()
cfg.Addr = "127.0.0.1:3306"
cfg.User = "root"

cfg.Dump.TableDB = "test"
cfg.Dump.Tables = []string{"canal_test"}

c, err := NewCanal(cfg)

type MyEventHandler struct {
  DummyEventHandler
}

func (h *MyEventHandler) OnRow(e *RowEvent) error {
  log.Infof("%s %v\n", e.Action, e.Rows)
  return nil
}

func (h *MyEventHandler) String() string {
  return "MyEventHandler"
}

c.SetEventHandler(&MyEventHandler{})

c.Start()


import (
  "github.com/siddontang/go-mysql/client"
)

conn, _ := client.Connect("127.0.0.1:3306", "root", "", "test")

conn.Ping()

r, _ := conn.Execute(`insert into table (id, name) values (1, "abc")`)

println(r.InsertId)

r, _ := conn.Execute(`select id, name from table where id = 1`)

v, _ := r.GetInt(0, 0)
v, _ = r.GetIntByName(0, "id")


import (
  "github.com/siddontang/go-mysql/server"
  "net"
)

l, _ := net.Listen("tcp", "127.0.0.1:4000")

c, _ := l.Accept()

conn, _ := server.NewConn(c, "root", "", server.EmptyHandler{})

for {
  conn.HandleCommand()
}

package main

import (
  "database/sql"
  
  _ "github.com/siddontang/go-mysql/driver"
)

func main() {
  dsn := "root@127.0.0.1:3306?test"
  db, _ := sql.Open(dsn)
  db.Close()
}
```

```
mysql -h127.0.0.1 -P4000 -uroot -p
```


