---
title: "How do I rename my computer in Lunix?"
date: 2009-02-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JohnnyStorm on 2009-02-15
Hello everyone.

I was wondering if there was a way that i can rename my computer, because when I loaded Ubuntu I don't think it mattered, but it makes my terminal prompt pretty long. Also is there a command to permanently change the terminal prompt so that I don't have to see the path all of the time?

Thanks for your help,

JohnnyStorm

---

### Post by TCSnyder on 2009-02-15
yea in Administration=>Network 

it's in the General tab labeled "Host name"

---

### Post by fulton on 2009-04-25
I just wanted to add that in 9.04, the System > Administration > Network tab is no longer present. The network tools applet does not seem to have any function for allowing you to change the host name.

Instead, I wouuld recommend following the advise in the following forum thread:

[http://ubuntuforums.org/showthread.php?t=1038905&highlight=rename+host]("http://ubuntuforums.org/showthread.php?t=1038905&highlight=rename+host")

(or, in summary, edit /etc/hostname, and then /etc/host, replacing the name you do not want with the name you want)

---

