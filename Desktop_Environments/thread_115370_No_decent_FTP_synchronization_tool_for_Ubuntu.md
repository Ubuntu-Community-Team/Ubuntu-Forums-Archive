---
title: "No decent FTP synchronization tool for Ubuntu"
date: 2006-01-10
forum: Desktop Environments
---

### Post by rasmusbp on 2006-01-10
I'm slowly migrating from XP til Ubuntu. The most annoying thing right now is that there doesn't seem to be any decent, newbie-friendly (GUI!) equivalent to the windows program [SyncBack]("http://www.2brightsparks.com/syncback/syncback-hub.html"). This program automatically synchronizes stuff from my hard drive to an normal FTP server (ie an exact copy). Can this really be true? I've searched hard, but haven't been able to find something that comes close. Normally, I've always been able to find a good (often even better) linux version of my old xp apps! 

I haven't been able to make SyncBack work properly through Wine, so that's why I'm asking this...

Thanks!
Rasmus

---

### Post by shakin on 2006-01-10
1. [ftpsync](http://sourceforge.net/projects/ftpsync/)
2. mirror (repositories)
3. ftpmirror (repositories)
4. fmirror (repositories)
5. sitecopy (repositories)

I'm sure there are more since much of the Open Source world depends on FTP mirrors for file downloading.

---

### Post by rasmusbp on 2006-01-10
Thanks for the list! I've had a look, but none of these program seems to offer a GUI?! Sorry, but I'm really hoping to get the luxury of setting this thing up without having to use a terminal...

Cheers

---

### Post by TiZeta on 2006-01-10
Hi!
i've seen there is a sync function in Kbear, it's an ftp graphic client for Kde, but i think you can use it with Gnome too.
You can find it packed for Unbuntu, have a look in Synaptic or Kpackage (or try with apt-get).

Bye :smile:

---

### Post by cwaldbieser on 2006-01-10
rsync uses ssh or an rsync server rather than FTP.  It is comman line based, but there are GUI front ends:
[http://www.cis.upenn.edu/~bcpierce/unison/]("http://www.cis.upenn.edu/~bcpierce/unison/")

---

### Post by rasmusbp on 2006-01-16
Thanks everyone. 

TiZeta, I tried Kbear, but it didnt really work properly under Gnome. Most of it did work, though, but the program crashed when I tried to sync a local dir with a ftp dir. 

The FTP server that I am using only runs FTP, not SSH, so I can only use programs with FTP functionality.

So, it seems that I am stuck with an XP app for now...

Bye

---

### Post by rasmusbp on 2006-01-16
Thanks everyone. 

TiZeta, I tried Kbear, but it didnt really work properly under Gnome. Most of it did work, though, but the program crashed when I tried to sync a local dir with a ftp dir. 

The FTP server that I am using only runs FTP, not SSH, so I can only use programs with FTP functionality.

So, it seems that I am stuck with an XP app for now...

Bye

---

