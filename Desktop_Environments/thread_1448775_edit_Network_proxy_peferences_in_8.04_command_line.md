---
title: "edit Network proxy peferences in 8.04 command line"
date: 2010-04-07
forum: Desktop Environments
---

### Post by Diamond2 on 2010-04-07
How to edit this setting by using command line?

System--->Preferences--->Network Proxy
[img]http://www.ubuntugeek.com/wp-content/uploads/2009/11/22.png[/img]

I want to ssh to another computer and edit this setting for users. Where can I find config file?

Using ubuntu 8.04 hardy

---

### Post by Kljuka on 2010-04-07
Try this:

Edit your /etc/bash.bashrc file as root.
 Put these line at the end of your /etc/bash.bashrc file :
 export http_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.net:port/
You can omit the username:password, if your proxy server has no  password.


You'll probably have to logout and login after these changes (not sure).

---

