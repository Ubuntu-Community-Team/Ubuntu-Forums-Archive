---
title: "shell script"
date: 2012-12-30
forum: Desktop Environments
---

### Post by hari7673 on 2012-12-30
Can anyone please tell me how to execute a shell script at the start up of desktop.
I mean what commands are to be included in the shell script so as to get it executed without the user interference.
thanks in advance

---

### Post by hari7673 on 2012-12-30
the shell script i am trying to execute contains a link to a media playlist

---

### Post by cariboo on 2012-12-30
You didn't tell us what version you are using, so I'll assume you are using Ubuntu 12.04 or 12.10. Open a terminal and type the following commands:

```
cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

then in the same terminal type:

```
gnome-session-properties
```

you can then add your script to the start-up applications menu.

---

### Post by hari7673 on 2012-12-30
Thank you sir i got hold of that script and executing well.
can you suggest me a online learning page for such script programming.

---

### Post by Kirk Schnable on 2012-12-30
> **hari7673 said:**
> Thank you sir i got hold of that script and executing well.
can you suggest me a online learning page for such script programming.

I really like the Unix Toolbox. It has a lot of command examples, not the most detailed explanations as its intended as a pocket reference, but you could peruse it, and ask Google or the Ubuntu Forums any specific questions you have about new commands you're learning. 

[http://cb.vu/unixtoolbox.xhtml](http://cb.vu/unixtoolbox.xhtml)

Obviously you'd want to be looking at Linux commands. (not the FreeBSD ones, etc)

---

