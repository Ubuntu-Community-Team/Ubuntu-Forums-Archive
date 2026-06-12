---
title: "Annoying office prank - changing wallpapers"
date: 2011-10-13
forum: Desktop Environments
---

### Post by drsl on 2011-10-13
Hello Ubuntu community, give me a hand here :p

A few weeks ago a colleague of mine was helping me with some project he used to work on, and he saw me type my password in some app that doesn't hide it in the terminal (I think it was svn, not sure though). Now, this guy is a professional prankster, so you know where this is going #-o

The next day I log into my machine to discover that I have some weird (and slightly pornographic) wallpaper. And the wallpaper kept changing every 30 seconds or so to other similarly themed art pieces, and no matter what I did I couldn't make it stop. I tried removing them from the "Change Desktop Background" menu and they just kept popping up again after a few minutes. I also tried changing my desktop theme to no avail.

So I went into the terminal and started doing some searches for suspicious image files until I found the culprits. All the prank wallpaper images were in the /usr/share/icons/themes directory. I quickly deleted them and changed my wallpaper. That worked for a minute, until my wallpaper was changed to a black background, and kept doing so every time I changed it back to some picture. Immediately after that I changed both my user and my root password, obviously.

Now, to make matters worse, the next day I logged into my box again only to find that I have yet another wallpaper and another image file in the same directory I mentioned. I asked my prankster friend but he won't tell me what he did and how he did it, but he's the Linux expert here.

We all use Ubuntu 11.04 here, and I'm using the Unity interface. I'm not a beginner with Linux/Ubuntu, but I'm not an expert either.

Does anyone know what or how he did that, or at least point me in a direction so I can fix this?

Thanks for the help.

---

### Post by sirkeith on 2011-10-13
I always figger with friends like this you don't need enemies. Sorry I can offer no help, sympathy is all I can do.

---

### Post by smurphy_it on 2011-10-13
I'd start by checking to see if he made an account on your machine and also check to see if he done a NFS export.

```
cat /etc/passwd
cat /etc/export
```

---

### Post by drsl on 2011-10-13
> **smurphy_it said:**
> I'd start by checking to see if he made an account on your machine and also check to see if he done a NFS export.


Well, turns out he DID make an account, the bastard. I deleted it, but the problem still remains. I think he might be controlling my system remotely somehow, is that possible?

Or maybe he executed a malicious script, but I don't see any suspicious process running.

---

### Post by Dangertux on 2011-10-13
> **drsl said:**
> Well, turns out he DID make an account, the bastard. I deleted it, but the problem still remains. I think he might be controlling my system remotely somehow, is that possible?

Or maybe he executed a malicious script, but I don't see any suspicious process running.

If this is going on at your place of employment you need to contact whatever system administration or security personnel work in your company. Explain to them what happened and have them deal with it and your friend appropriately.

It stinks to "rat out a friend" but if he is doing these types of things because he thinks it is funny or  cute, it's really not. If he doesn't know what he's doing with this stuff, his next prank could cause serious security issues within your company.  He needs to understand that it's not a game and he's at work and needs to act professionally. 

Also : make sure you are protecting your password, even from your friends ;-)

---

### Post by ssam on 2011-10-13
check if he put something in cron

```

crontab -l

```

---

### Post by Copper Bezel on 2011-10-13
Yeah, that would make the most sense - a cron job to switch the wallpaper setting in gconf.

You also might want to check what it's actually set to now in gconf-editor under /desktop/background.

---

### Post by smurphy_it on 2011-10-14
Was there a /etc/export file.  That's typically where one would export a FS, so he can mount it on his end.

Check to see if your 'friend' setup any additional ports etc that he can connect in though.

```
netstat -ant |grep LISTEN
```

---

### Post by Entilza on 2011-10-14
> **Dangertux said:**
> If this is going on at your place of employment you need to contact whatever system administration or security personnel work in your company. Explain to them what happened and have them deal with it and your friend appropriately.

It stinks to "rat out a friend" but if he is doing these types of things because he thinks it is funny or  cute, it's really not. If he doesn't know what he's doing with this stuff, his next prank could cause serious security issues within your company.  He needs to understand that it's not a game and he's at work and needs to act professionally. 

Also : make sure you are protecting your password, even from your friends ;-)


WTF I hope I don't work with you!

---

