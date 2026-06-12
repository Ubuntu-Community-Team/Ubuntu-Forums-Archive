---
title: "Pros and Cons of 6.06 - My $0.02"
date: 2006-07-09
forum: Desktop Environments
---

### Post by linuxted on 2006-07-09
I've spent a bit of time on Dapper 6.06 and thought I'd share these tidbits:

Pros:  
1) USB2.0 seems to work great now.
2) mp3 players are working without much hassle
3) Start up time is very fast.
4) Installation is slicker

Cons:
1) Sound is completely broken
2) Java on 64bit doesn't work neither does 32bit (for chatrooms that use Java applets).

I could go on, but the rest is on the minor side.

:-({|= 
My $0.02

---

### Post by jISh on 2006-07-09
You can fix the sound, and fix the Java.
Get the sun java 1.5 packages from the repositories, and, well, how exactly is your sound broken? You can never hear anything?

---

### Post by linuxted on 2006-07-09
> **jISh said:**
> You can fix the sound, and fix the Java.
Get the sun java 1.5 packages from the repositories, and, well, how exactly is your sound broken? You can never hear anything?

I don't hear anything at all.  Power is on, input is attached and nothing appears to be muted.  CDs, mp3s, games, login/out... nothing has sound.

Java crashes on me with 64bit install on some of my favorite websites.  For example:
[http://www.hopeaz.com/Chat2.htm](http://www.hopeaz.com/Chat2.htm)

With 32bit install, Java sometimes crashes on the above website.

---

### Post by Anduu on 2006-07-10
Well if it is any consolation I crash consistently at that site (32 bit install)...possibly a firefox issue rather than Java?

I don't have another java enabled browser to test the theory :|

---

### Post by jonrkc on 2006-07-10
If you have the KDE desktop available (even if you don't use it normally), try and see if you get sound there--and look into the sound management part of the KDE control panel.  

A lot of sound problems are caused by conflicts between different sound management systems that don't get along with each other.  From what I've read (and experienced), sound is one of the greatest weaknesses of Linux, period.

I generally lose sound two or three times a day and have to juggle ALSA, ESD, and sometimes the KDE thing--is it called ARTS?--for several minutes, monitoring with aumix or alsamixer, till I get it back.  I spent an hour night before last trying to get sound for a movie.  I finally got it.  I wasn't much in the mood to watch the movie by then, though.

---

### Post by linuxted on 2006-07-10
> **Anduu said:**
> Well if it is any consolation I crash consistently at that site (32 bit install)...possibly a firefox issue rather than Java?

I don't have another java enabled browser to test the theory :|

I do appreciate the information (makes me feel less insane).  I've sent a bug report out weeks ago.  Is there another browser I could try in Linux?  I'm only aware of Mozilla/Firefox

linuxted

---

### Post by linuxted on 2006-07-10
> **jonrkc said:**
> If you have the KDE desktop available (even if you don't use it normally), try and see if you get sound there--and look into the sound management part of the KDE control panel.  

A lot of sound problems are caused by conflicts between different sound management systems that don't get along with each other.  From what I've read (and experienced), sound is one of the greatest weaknesses of Linux, period.

I generally lose sound two or three times a day and have to juggle ALSA, ESD, and sometimes the KDE thing--is it called ARTS?--for several minutes, monitoring with aumix or alsamixer, till I get it back.  I spent an hour night before last trying to get sound for a movie.  I finally got it.  I wasn't much in the mood to watch the movie by then, though.

I'm not sure what you mean by having a KDE desktop available.  I did install K3b which installed a bunch of KDE stuff.  Sorry for the newbee question

Linuxted
:-k

---

### Post by Dubbayoo on 2006-07-10
My sound works fine and I can log into java based chat room on vbulletin sites.

---

### Post by kd7swh on 2006-07-10
Confiure your sound card
and install the Java JRE from sun.com and all will be well.

---

### Post by Ptero-4 on 2006-07-10
> **linuxted said:**
> I'm not sure what you mean by having a KDE desktop available.  I did install K3b which installed a bunch of KDE stuff.  Sorry for the newbee question

Linuxted
:-k

What he meant is that you may need to install Kubuntu-desktop which will install the entire KDE.

Note: Doing this will consume an insanelly huge amount of HD space. Perform only if you have a big HD.

---

### Post by sefs on 2006-07-10
The last time my sound didnt was was becasue in the user profile the user was not authorzied to use audio devices, but once enabled there I had song.  Maybe its something like that.

---

### Post by jonrkc on 2006-07-11
If you don't want to install the entire KDE Desktop, you can just do this:
```

kdeinit & kicker &

```
and chances are (after a bit of a wait) you'll have a taskbar that you use to access KDE's tools.  On my installation I don't have to be root to do it, but you might have to do it as root, depending.

The basics of KDE seem to be in most installations.  It's true that the desktop takes a whole lot of hard-drive space.  Of course, you could always uninstall it.

---

### Post by linuxted on 2006-07-13
> **kd7swh said:**
> Confiure your sound card
and install the Java JRE from sun.com and all will be well.

I wish it were that easy.  Unfortunatley the Java JRE from Sun (64 and 32bit) doesn't work on the site I quoted above.

As far as configuring the soundcard, I'm not sure what I have to do.  I've gone to "System-Preferences-Sound" and the default sound card is correct.  Is there something else I need to do?  This sound card has worked flawlessly in other Ubuntu installs.

Thanks

---

### Post by lerrup on 2006-07-13
> **Ptero-4 said:**
> What he meant is that you may need to install Kubuntu-desktop which will install the entire KDE.

Note: Doing this will consume an insanelly huge amount of HD space. Perform only if you have a big HD.

Define insane. 

I have KDE and gnome installed on a 4gb partition with room to spare.  There is nothing big about it.

---

### Post by aysiu on 2006-07-13
```
 df -h
Filesystem            Size  **Used** Avail Use% Mounted on
/dev/hda7             8.8G  **3.4G**  5.0G  41% /
``` I have Ubuntu, Kubuntu, and Xubuntu. Is 3.4 GB a huge amount of hard drive space?

---

