---
title: "Need Help with Thunderbird Webmail extension"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Omnios on 2006-09-02
[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

 Hi I installed Thunderbird and am trying to get the Webmail extension working. I got the web mail extention installed but it does not seem to work. The add webmail option in accounts does not appear and all the servers in the property pop up show as not connected. I realy want to get this going for Rogers.Yahoo mail as I get it free with my isp.

 Edit:: K under user the webmail extention server will not  connect. However running thunderbird as root it will connect to the server. Now my question is how do I make it so that thunderbird can connect to the servers as user.

---

### Post by foolsh on 2006-09-02
im not sure how to make normal user mode work but for a work around i edited the menu item so that it reads 
```
kdesu ksystraycmd '/opt/thunderbird/thunderbird'
```
so that it asks for my password to run as root and runs in the system tray too
BTW i installed it from the thunderbird site not with apt-get so thats why its in /opt so dont copy paste the code in its enterity
this works in kubuntu not sure what the equivelent gnome commands wound be but im sure they exist anyone have any?
I dont like running it as root but for now I guess I'll settle for this.

i think its gksudo for the password prompt in ubuntu "gnome"

---

### Post by Omnios on 2006-09-02
K got gksudo set up but now it gives me an error stating 
```

Sending of username did not succeed. Mail localhost responded: rogers.com is a unsupported domain

```

---

### Post by foolsh on 2006-09-03
you shouldn't need the webmail extention for this email account 
in thunderbird click "file" then "new" and finally "account"

follow along filling in your relevent information 

[IMG]http://foolsh.home.insightbb.com/snapshot1.jpg[/IMG]
[IMG]http://foolsh.home.insightbb.com/snapshot2.jpg[/IMG]
[IMG]http://foolsh.home.insightbb.com/snapshot3.jpg[/IMG]
[IMG]http://foolsh.home.insightbb.com/snapshot4.jpg[/IMG]
[IMG]http://foolsh.home.insightbb.com/snapshot5.jpg[/IMG]

for outgoing mail you should configure it like this

[IMG]http://foolsh.home.insightbb.com/outgoing.jpg[/IMG]

try it without the gksudo command i dont think you need it to work.
only for a real yahoo account do need webmail and the yahoo.webmail extention

---

### Post by AmandaKerik on 2007-02-01
> **Omnios said:**
> ... Now my question is how do I make it so that thunderbird can connect to the servers as user.

1.) Low port numbers are either blocked by the OS or need sudo.

2.) Put the port number above 1025
***In the webmail settings first, then the account settings to match.***
Tools > Extensions > webmail > preferences > servers > ports

---

