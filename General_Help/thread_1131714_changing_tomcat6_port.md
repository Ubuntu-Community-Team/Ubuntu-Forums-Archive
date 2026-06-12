---
title: "changing tomcat6 port"
date: 2009-04-21
forum: General Help
---

### Post by phonethics on 2009-04-21
I installed [tomcat6]("http://packages.ubuntu.com/intrepid/tomcat6") and then [yaws]("http://packages.ubuntu.com/intrepid/yaws") but both use port 8080.
Even though tomcat6 and yaws bash scripts are in /etc/init.d/, I think tomcat6 gets killed after yaws is run - because sudo netstat -plantu doesnt show tomcat6 anywhere.

1. So how do I change the port of tomcat6 to 8085 ?
2. Where else can I keep a track of which applications are using which ports ? Im loosing track of them after installing a number of services.

thanks

---

