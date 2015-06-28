## logrus
----


### example

```
package main

import (
	log "github.com/gogap/logrus"
	"github.com/gogap/logrus/hooks/file"
	"github.com/gogap/logrus/hooks/syslog"
)

func main() {
	//设置输出格式为json
	log.SetFormatter(&log.JSONFormatter{})

	//输出到syslog
	graylog, err := syslog.NewHook("udp", "boot2docker:9002", syslog.LOG_DEBUG, "yijifu")
	if err != nil {
		log.Error(err)
		return
	}
	log.AddHook(graylog)

	//输出到文件
	log.AddHook(file.NewHook("logs/ss.log"))

	log.Errorf("member not login,member is %s", "1001")
}

```

