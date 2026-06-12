---
title: "Amarok 1.3 is out"
date: 2005-08-15
forum: Desktop Environments
---

### Post by !nkubus on 2005-08-15
Is there a package yet  of amarok 1.3 in backports ?

---

### Post by PeP on 2005-08-15
not yet but you might tried the one posted here
[http://ubuntuforums.org/showthread.php?p=303426#post303426](http://ubuntuforums.org/showthread.php?p=303426#post303426)

---

### Post by Mishura on 2005-08-16
That package appears to work nicely, and has the Gstreamer (and aRts) engine built-in.  Just **make sure** that you do a:

```
sudo apt-get remove amarok amarok-engines
```

To remove all of the previous amaroK installation first.  Your settings and your collection will stay put as they are saved in ~/.amarok or ~/.kde/something/amarok.. can't remember which.

---

### Post by f1dave on 2005-08-16
Uncle Rodney says, "10/10, amaroK is seriously super!"

Heh. Serious music player. Well done to the team.

---

### Post by zAo on 2005-08-16
Anyone who can post a backport for Hoary + KDE 3.4.2?

Thanks!

---

### Post by GoA on 2005-08-16
[QUOTE=zAo]Anyone who can post a backport for Hoary + KDE 3.4.2?

Thanks![/QUOTE]
 Why don't you install it by yourself? It's easy and fast operation, jsut follow the directions in amarok 1.3 beta topic. Works fine for me. :)

---

### Post by timczer on 2005-08-16
After you install the new Amarok player how do you get it to play mp3's?  It comes up with an error message saying gstreamer can't play mp3s.  I used to use the xine engine.  If I try to install that, apt-get wants to install amarok and all the other packages again.  Can I get it to install amarok-xine to be used by 1.3, or can I get gstreamer to play mp3s?

---

### Post by timczer on 2005-08-16
Never mind, I must not have had the mp3 plugin for gstreamer installed in the past.  When I installed gstreamer-plugin and reopened amarok it worked fine.

---

### Post by PeP on 2005-08-16
> Originally Posted by zAo
Anyone who can post a backport for Hoary + KDE 3.4.2?
 
 Thanks! 


you're welcome the one in the post linked above is compiled in Hoary+kde3.4.2 .

---

### Post by !nkubus on 2005-08-16
Well but this is just the beta , I would prefer to wait a bit to have a full version on the repository.

---

### Post by alquimista on 2005-08-16
I installed the new version as indicated; yet I get the error (that I'll translate from spanish):

"GStreamer, register missing:
Please make sure all GStreamer plugins are installed (OGG, MP3 for example), and then execute gst-register"


Then arts-engine is loaded; what can I do to make GStreamer work?

Thanx,
Guillermo

---

### Post by timczer on 2005-08-17
Try installing Gstreamer-plugins through synaptic (it's in universe).  This package installs all of the Gstreamer plugins and is a pretty small file.  That made it work for me.

---

