---
title: "Root and Settings Question"
date: 2005-10-29
forum: Desktop Environments
---

### Post by ArcadePride on 2005-10-29
I just recently installed kubuntu, and man am I impressed. Everything for the most part just works so well, but there are 2 things I can’t seem to figure out, nor find a relevant old forum post or something in the user documentation. 

1) I don’t know how to get to root level for the gui side. I understand the sudo command for the terminal, but when I try to edit things like in the /etc folder, it won’t allow me. And in the setting some of the things that have an "administrator mode" won’t work either. I type in the password I made at install for my user, and it just goes back to before I clicked admin mode. Do I have to make a root password still for the admin mode and to log in for restricted file configuration?

2) I got kubuntu on my laptop and when ever it’s on just batteries, the screen turns off after only 2 minutes of inactivity, and 20 when plugged in. I looked through the settings, and I can’t find were to change this. I see when I right click the power meter the Performance Profile menu with userpace, powersave, ondemand, conservation, and performance. I have userspace selected, but do I have to select one of the others? Where do I go to see their settings/differences and edit them?

Any help at all is greatly appreciated. The community built around this distro is just awesome and I look forward to using kubuntu for more years to come.:D

---

### Post by HermanAB on 2005-10-29
$ sudo kedit

or
$ sudo gedit

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by aysiu on 2005-10-29
Actually, you're probably better off doing ```
kdesu konqueror
``` from the run command (for problem #1).

---

### Post by ArcadePride on 2005-10-29
oh yea, thanks. kdesu konqueror works perfectly. :KS

---

