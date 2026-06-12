---
title: "Problems when not connected to internet"
date: 2005-08-25
forum: Desktop Environments
---

### Post by tflovik on 2005-08-25
I am having a strange problem with my Dell Inspiron 6000 laptop.
When i am away from home and not connected to internet with wireless i can not play mp3,DVD or other video formats(*.avi etc.).
Have tried this with Amarok(mp3) and Noatun/Kaffeine.
Ewerythings work perfect when i come home again and connect to wireless broadband.
Does anybody have a solution please?

---

### Post by nemin on 2005-08-25
[QUOTE=tflovik]I am having a strange problem with my Dell Inspiron 6000 laptop.
When i am away from home and not connected to internet with wireless i can not play mp3,DVD or other video formats(*.avi etc.).
Have tried this with Amarok(mp3) and Noatun/Kaffeine.[/QUOTE]
Strange, what's exactly "can not play"?  Do you get anything like an error message? If not, probably when you execute the program from the terminal?

---

### Post by tonysathre on 2005-08-25
i dont know if this even makes sense, but open synaptic and get w32codecs

---

### Post by tflovik on 2005-08-25
Sorry i didn't mention it before.
I'm running Kubuntu 5.04 with KDE 3.4.2.
Have installed LIBDVDCSS2 and W32CODECS.
Everything works when connected to broadband with wireless.
I can play mp3 and watch DVD and play AVI/DIVX etc.
When i'm not connected to a broadband connection i have to press "Ctrl C"
When stated "Connecting network Services" at bootup to proceed to KDM.
After this when trying to open a DVD or AVI/DIVX Kaffeine yust shut down.
In Amarok when trying to play a mp3 nothing happens.
When i boot up after this connected to broadband everything works again.
Strange.

---

### Post by MartinJ on 2005-08-25
I've got the same problem here.  If I cancel the network configuration I can't play music (system sounds work ok) and my printers disappear from the list in the Control Centre.

If my laptop isn't plugged into the router I have to wait about a minute for it to time-out.  Everything works ok after that.

Is there a way to shorten the timeout period?

---

### Post by tflovik on 2005-08-27
I have allways pressed "Ctrl C" when i have no broadband router to connect to.
Tried to let "Connect network services" time out. It took about 1 and a half minute. After that i could play music and watch movies.
Why do Network services have to start up to be able to play music/video ?

---

### Post by gravestone on 2005-08-29
I'm on a Dell 6000 as well, and have noticed similiar things, but I think it's related to the sound driver. I use XMMS, which is configured to use the OSS sound system. When I press the play button, it appears to hang, which is what I first thought.

I left it one day, and about a minute later it starts playing. On start up, the log in sound plays, and I think it's locking the driver. I usually wait about 5 minutes, either on or of the network, and all works fine.

On boot up I only Ctrl + C the sync with the time server, when not on the net. I have made the ethernet card the primary net card, and don't have wireless configured. This lets the network get configured.

When I need to use the wireless, I drop to a command line, and configure the wireless the easy way with iwconfig and dhclient.

---

