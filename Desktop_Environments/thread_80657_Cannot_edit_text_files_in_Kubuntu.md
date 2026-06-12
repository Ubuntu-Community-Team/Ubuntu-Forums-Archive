---
title: "Cannot edit text files in Kubuntu"
date: 2005-10-22
forum: Desktop Environments
---

### Post by blastus on 2005-10-22
Hello, I've having a major problem in Kubuntu! I cannot edit text files!

sudo kwrite /etc/apt/sources.list
```
Error: "/var/tmp/kdecache-neo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/tmp/kde-neo" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"
```
sudo kate /etc/apt/sources.list
```
kate: ERROR: Communication problem with kate, it probably crashed.
```
kdesu kwrite /etc/apt/sources.list
Sometimes the command hangs, other times it prompts for a password, but then fails.

kdesu kate /etc/apt/sources.list
Sometimes the command hangs, other times it prompts for a password, but then fails.

I should point out that these problems also occur when trying to edit text files in my own home directory. 

kwrite ~/blah
```
Will not save configuration.

Configuration file "/home/neo/.kde/share/config/kwriterc" not writable.

Please contact your system administrator.
```
kate ~/blah
```
kate: ERROR: Communication problem with kate, it probably crashed.
```
Here another error I sometimes get:
```
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
kbuildsycoca running...
ASSERT: "m_currentContainer==container" in /build/buildd/kdebase-3.4.3)
```
Trying to open a text file in Konqueror makes no difference. What is the DEFINITIVE command for editing text files in Kubuntu? Both kate and kwrite are just broken. In GNOME it is just "sudo gedit" and that's it and it works all the time no errors ever.

---

### Post by aysiu on 2005-10-22
sudo kate should not work.
sudo kwrite should.
Plus, you should always be able to kwrite something in your /home directory.
Maybe your permissions got messed up. Right-click on the offending folder (~/.kde/whatever) and go to properties. What does it say under permissions? Who owns the folder and what do others have access to?

---

### Post by blastus on 2005-10-22
[QUOTE=aysiu]sudo kate should not work.
sudo kwrite should.
Plus, you should always be able to kwrite something in your /home directory.
Maybe your permissions got messed up. Right-click on the offending folder (~/.kde/whatever) and go to properties. What does it say under permissions? Who owns the folder and what do others have access to?[/QUOTE]

That's interesting. "/home/neo/.kde/share/config/kwriterc" is owned by root and is a member of root. I don't remember, but I may have opened kwrite as root (either with sudo or kdesu), and changed the font size while in kwrite. I guess I need to chown kwriterc now.

Why shouldn't kate work with this? And what about kdesu? Thanks for your help!

---

### Post by aysiu on 2005-10-22
[QUOTE=blastus]That's interesting. "/home/neo/.kde/share/config/kwriterc" is owned by root and is a member of root. I don't remember, but I may have opened kwrite as root (either with sudo or kdesu), and changed the font size while in kwrite. I guess I need to chown kwriterc now.[/quote] Sounds like a plan.

> 
Why shouldn't kate work with this? And what about kdesu? Thanks for your help! I don't know all the details, but it's something about kate wanting to write to some temp directory it doesn't have access to. Assuming everything's working correctly, you should be able to do sudo kwrite from the terminal or kdesu kwrite from the Run dialogue. Honestly, though, I prefer sudo nano. Maybe that's just me.

---

### Post by blastus on 2005-10-22
OK now kwrite ~/blah works, but

sudo kwrite /etc/apt/sources.list

```
Error: "/var/tmp/kdecache-neo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/tmp/kde-neo" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"
```

The first time I hit the save button in kwrite I get this additional message in the console

```
Error: "/tmp/ksocket-neo" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"
```
:???:

---

### Post by aysiu on 2005-10-22
Does it still save, even though you get those error messages in the console?

---

### Post by blastus on 2005-10-22
[QUOTE=aysiu]Does it still save, even though you get those error messages in the console?[/QUOTE]

Yes. Are these error messages normal for Kubuntu?

---

### Post by escobar on 2005-10-24
From my experience, yes those errors are normal. Also, I ditched kate and got leafpad. Lightweight. Does it's job. Period.

---

### Post by blastus on 2005-10-24
I just had to chown kwriterc again. I think I going to stick to "sudo nano" and not deal with this kwrite and kate mess.

There just seems to be tons of bugs, annoyances, and instability in both KDE and GNOME. I really wanted to use GNOME but Nautilus is so extremely unstable it is useless to me because it crashes all the time. And Konqueror, while it is pretty stable, has plenty of bugs and annoyances like keyboard focus problems (sometimes it looses keyboard focus and the ONLY way I can get it back to do an ALT-TAB and cycle back to it), selection problems (often times the anchor of a selection is not highlighted but it is still part of the selection), and so on and so forth. Sometimes applications just don't open in KDE, I'll see a bouncing icon for about a minute, then it will disappear as though I had not done anything. Then two seconds later I'll try to open the application again and it will open. There's just too much to list (Kaffeine, Administrator Mode etc...) here but hopefully KDE and GNOME will start to seriously focus on the bugs and stability problems of their environments and applications.

---

### Post by aysiu on 2005-10-24
Have you considered using XFCE? It's a lightweight desktop environment that I've found to be completely without bugs. No freezing up. No weird starts and stops or crashes. No error messages. The beauty of XFCE is that you can keep it lightweight but still use Gnome and KDE applications. For example, in XFCE, I use Konqueror (for FTP) and Gnome-Volume-Manager (for managing the automounting of devices) on a regular basis. Give it a shot!

---

### Post by claydoh on 2005-10-25
I found that running "kdesu kate" will work for kate. I also don't seem to have the permission errors on kwriterc or keditrc using sudo since installing Breezy (fresh install). "sudo kwrite" still shows the ""/var/tmp/kdecache-clay" is owned by uid 1000 instead of uid 0." error but it does not change the rc files permission. But I use kedit which, which doesn't show these errors anyway.

---

### Post by blastus on 2005-10-26
> Have you considered using XFCE? It's a lightweight desktop environment that I've found to be completely without bugs. No freezing up. No weird starts and stops or crashes. No error messages. The beauty of XFCE is that you can keep it lightweight but still use Gnome and KDE applications. For example, in XFCE, I use Konqueror (for FTP) and Gnome-Volume-Manager (for managing the automounting of devices) on a regular basis. Give it a shot!

I will look into it. I would try this on a secondary Ubuntu installation as I don't want to mess up my main installation. I'm also on dialup too so it depends on how big XFCE is, like if it's over 100Mb or something.

> I found that running "kdesu kate" will work for kate. I also don't seem to have the permission errors on kwriterc or keditrc using sudo since installing Breezy (fresh install). "sudo kwrite" still shows the ""/var/tmp/kdecache-clay" is owned by uid 1000 instead of uid 0." error but it does not change the rc files permission. But I use kedit which, which doesn't show these errors anyway.

"kdesu kate" gives me about 6 million "kbuildsycoca: WARNING:" warnings along with ASSERTS and all kinds of other funky stuff. Either that or it hangs or says that there was a communication problem. I also just installed kedit and experienced the same errors/warnings that kwrite gives. Good old "sudo nano" works flawlessly though.

---

### Post by aysiu on 2005-10-26
[QUOTE=blastus]I will look into it. I would try this on a secondary Ubuntu installation as I don't want to mess up my main installation. I'm also on dialup too so it depends on how big XFCE is, like if it's over 100Mb or something.[/quote] [It seems to be about 4k.](http://packages.ubuntu.com/breezy/x11/xfce4) Don't install xubuntu-desktop. Just install XFCE4 and whatever peripherals you want manually through Synaptic. You'll need the Universe repositories for this, by the way.

---

