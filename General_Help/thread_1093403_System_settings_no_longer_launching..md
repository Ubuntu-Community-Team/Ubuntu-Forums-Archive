---
title: "System settings no longer launching."
date: 2009-03-11
forum: General Help
---

### Post by MickS on 2009-03-11
For some reason, might have been an update or perhaps trying cool iris but suddenly system settings won't launch. I've tried reinstalling which didn't work, any ideas what to try next? I've tried launching it from a terminal and it just reports an awful lot of system settings entries in the file system. I get the impression that somehow a file has gone awol but which one?
I would be grateful if someone could supply some ideas of what to do next, I am not asking for someone to hold my hand just some pointers because I am a bit lost.
Intrepid, KDE4.2
TIA

Mick

---

### Post by MickS on 2009-03-11
Oops should have done this before, this is what I get when I try and launch from a terminal.
mick@mick-desktop:~$ systemsettings
This program is already running.
<unknown program name>(8324)/: Communication problem with  "systemsettings" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 


Mick

---

### Post by MickS on 2009-03-29
Solved. In case anyone is interested all I had to do was Go to ~/.kde/share/apps/ and delete the folder systemsettings then go to ~/.kde/share/config/   and delete systemsettingsrc. Now it launches fine. Found this in a very old thread at Kubuntu forums, thanks to Jukato.

Mick

---

