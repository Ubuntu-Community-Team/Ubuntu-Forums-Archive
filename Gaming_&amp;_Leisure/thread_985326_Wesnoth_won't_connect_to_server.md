---
title: "Wesnoth won't connect to server"
date: 2008-11-17
forum: Gaming &amp; Leisure
---

### Post by blastradius on 2008-11-17
I've recently installed Wesnoth version 1.4 from the Ubuntu Hardy repos, game works fine, I can download add-ons no problem but when I try to connect to a game server it just hangs at the 'reading from server' window and the bar stays white.

Any ideas?

Thanks in advance

Eric

---

### Post by lukjad on 2008-11-17
Well, as a temp fix, you can download the games from the site itself. If you want, I can find the link for you.

As for your problem, are you behind a router or did you install a firewall?

---

### Post by blastradius on 2008-11-18
Just the default Hardy install.  The problem I've got is that It won't let me play online, I can get the add-ons but can't connect to a game server.

Thanks for the reply

---

### Post by ubuntu27 on 2008-11-18
Battle For Wesnoth gets updated quite often.
And every time there is a big update, they make the server to only work with the latest version.

I suggest you to update Battle for Wesnoth form version 1.4.0 to 1.4.6

[Battle for Wesnoth a]("http://www.wesnoth.org/")t [GetDeb]("http://www.getdeb.net/app/The+Battle+for+Wesnoth")

If you still have problems after updating Wesnoth, then you have a problem at your end (it is not the server).

---

### Post by blastradius on 2008-11-19
Thanks for the reply. Last question - Can I download it all and install in one hit or do I have to do each component seperately? isn't there just a 'Wesnoth' download?

---

### Post by lukjad on 2008-11-19
I am not sure if you are asking if you can install games all at once or just the package Wesnoth. I'm not too sure if you can get just one file to install it, but, if there were one, it would probably be called Wesnoth-all or something to that effect.

---

### Post by ubuntu27 on 2008-11-19
> **blastradius said:**
> Thanks for the reply. Last question - Can I download it all and install in one hit or do I have to do each component separately? isn't there just a 'Wesnoth' download?

If you are talking about the deb files from getdeb,
then you have to download "wesnoth", "wesnoth-data", "wesnoth-campaigns" to be able to play. It is highly recommended that you also download and install "wesnoth-music" (who wants to play mute?)

"wesnoth-editor" is optional. As the name implies, it si a program to edit or create a new map/scenario.

"wesnoth-server" You defentely DON"T need this.



Now to install, you have to put all the downloaded debs in the same directory since some of them are dependent upon one another.
You will have to install the "wesnoth" deb first, and then "wesnoth-data"
The rest can be on any order.

---

