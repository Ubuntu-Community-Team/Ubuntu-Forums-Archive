---
title: "guest-session auto.sh java issue"
date: 2015-09-25
forum: Desktop Environments
---

### Post by versoph on 2015-09-25
My goal is to launch a java applicaton when the guests user logs in. I have created an auto.sh file under /etc/guest-session that has this:
#!/bin/bash
cd /opt/foo/bar
java -jar myapp.jar

but when the guest logs in the app does not run

Troubleshooting:

1) I know that /etc/guest-session/auto.sh is called, for when I edit the file this way it works ( I see gedit ):
#!/bin/bash
gedit

2) I know the guest user has permission to run the app. As guest I can bring up a terminal and cd to /opt/foo/bar and run java -jar myapp.jar and all works well

I am not sure what to try next

---

### Post by versoph on 2015-09-25
Found the issue. In this scenario I had to explicitly point to the java executable:

/opt/java/jdk****/bin/java -jar myapp.jar

---

