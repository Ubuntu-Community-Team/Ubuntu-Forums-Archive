---
title: "external USB drive problem. (no audio)"
date: 2009-03-22
forum: General Help
---

### Post by oldsoundguy on 2009-03-22
Not sure of the thread area where this actually BELONGS, but here it goes:
Running 8.04 and have Alsa working just fine normally. 
(3.06 hyperthreaded with Creative LIVE 5.1 card) Even got it working digital out into 5.1 digital amp (no master volume control that WORKS, but it has been that way all along .. never worked.)

The problem is I have an external USB drive I have on a Windows box (NTFS) that has music files on it .. since, for some strange reason, I can't find any Windows computers on my network, only my Linux computers, (that is a totally different issue that I tried to solve and got "help from hell" on it!  USELESS!) I can't PLAY the music from the networked Windows boxes (file sharing enabled).  So tonite I attempted to play from the drive by attaching it via USB.  Fine .. the files are there and I can see the entire drive contents .. only thing is when I launch Amarok, NO SOUND .. it shows the file being played! (Amarok will play from the internal hard drives or from the opticals without a problem!)

Any clues?

---

### Post by oldsoundguy on 2009-03-22
bump

---

### Post by lawentzel on 2009-04-08
My only suggestion is it could be a through put issue.  Perhaps you are running a USB 1 port.  Just a guess.  I have an external hard drive and do not have that issue.

---

### Post by oldsoundguy on 2009-04-08
turned out I had to uninstall all networking on all machines and start at point A.  Got THAT to work!

---

### Post by sieve on 2009-08-18
Sounds like you fixed it, but for anyone else reading it, I recommend reading [this thread]("http://ubuntuforums.org/showthread.php?t=1130384&highlight=amarok+won't+play+songs").  I had the same problem of no sound and performing these installs fixed it.

---

