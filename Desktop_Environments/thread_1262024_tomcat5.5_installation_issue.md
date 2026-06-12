---
title: "tomcat5.5 installation issue"
date: 2009-09-09
forum: Desktop Environments
---

### Post by JimCol on 2009-09-09
hi all,

i just started trying my hand on Ubuntu & ran into an issue while installing tomcat5.5. when i try to run the server using startup.sh, i get following at the terminal...

```
Using CATALINA_BASE:   /usr/local/tomcat5.5
Using CATALINA_HOME:   /usr/local/tomcat5.5
Using CATALINA_TMPDIR: /usr/local/tomcat5.5/temp
Using JRE_HOME:        /usr/lib/jvm/java-6-sun-1.6.0.14
Using CLASSPATH:       /usr/local/tomcat5.5/bin/bootstrap.jar
```

however, when i goto [http://localhost:8080/](http://localhost:8080/) i get Failed to Connect message. i tried [http://localhost:80/](http://localhost:80/) as well, eventhough i haven't changed the default port yet.

tryin to setup tomcat for couple of days...wud really appreciate any help. tried googling my best w/o luck.

thanks.

---

### Post by sgordon on 2009-09-18
Hi there

For some reason, tomcat on ubuntu uses the default port of 8180. Which is different from all the guides you will find when googling for tomcat, unless you're very lucky!

Give that a try. Could be something more fundamental, so no gurantees!

  Si

---

