---
title: "Bery/VNC"
date: 2006-11-06
forum: Desktop Environments
---

### Post by Spatulas on 2006-11-06
Hello there.

I am attempting to use VNC while beryl is running, but whenever I try I get a blank screen until beryl is killed.  There is a [thread on these forums]("http://ubuntuforums.org/showthread.php?p=1659377") that mentions this issue (and is actually the only resource I could find on the issue), however what worked for the poster there does not work for me.  I'm running vnc with x11vnc, started through xinetd.  Any help is hugely appreciated :)

---

### Post by phersotty on 2006-11-06
> **Spatulas said:**
> Hello there.

I am attempting to use VNC while beryl is running,

Search for posts on nomachine and nxclient.  Its supposed to be faster than VNC.  I was trying it the other day, but I didn't have it configured right.  I think its do-able though.

---

### Post by Spatulas on 2006-11-06
I will need to access my box from a Windows box though; these don't allow for this do they?

---

### Post by garretwp on 2006-11-06
Nomachine / freenx will allow you to access your linux box from any machine as long as you have download the client for that plateform. the Nomachine client has a version for mac os x, windows, linux, and so on. I have freenx which is a public/free version of the Nomachine. It works wonders!

- Garrett

---

### Post by Spatulas on 2006-11-06
Thanks, I will try it out!

---

### Post by Spatulas on 2006-11-06
I got it working, however it starts a new X session; is there a way to use the existing X session etc?

---

### Post by garretwp on 2006-11-06
With freenx, I do not know of a way to use a current running x seesion. I do remember someone in the past saying that you can create a z session at home to load up the nxclient do what you have to do on the machine and then save your current state and if you need to load that current session remotely, you can do so. But there is no way you can use the current session that is running on the machine.

- Garrett

---

### Post by Spatulas on 2006-11-06
Dang, that is what I need :(

---

