---
title: "Do I need to do computer housekeeping in Linux?"
date: 2009-06-19
forum: General Help
---

### Post by Extreedoc on 2009-06-19
When I was using Windows I was used to having to do a little spring cleaning such as deleting Temp files and a very occasional defrag.
Is this something that needs to be done with Ubuntu 8.10 or is it a thing of the past for me now?

---

### Post by TeoBigusGeekus on 2009-06-19
> **Extreedoc said:**
> ...or is it a thing of the past for me now?
Yes it is.

---

### Post by nmaster on 2009-06-19
I'm not sure if its even possible to defrag ext3.  Apparently its not supposed to need it anyway.

---

### Post by bodhi.zazen on 2009-06-19
There is much less need on Linux.

Every OS needs cleaning , but be sure you understand what you are doing first.

Ubutnu now includes a "janitor" (see your system menu [ system -> administration -> janitor ]) and you may use other tools such as bleachbit.

See also :

[http://www.howtoforge.com/delete-unnecessary-files-from-your-desktop-with-bleachbit-on-ubuntu-9.04](http://www.howtoforge.com/delete-unnecessary-files-from-your-desktop-with-bleachbit-on-ubuntu-9.04)

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

[http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html](http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html)

---

### Post by Extreedoc on 2009-06-20
Excellent..., fingers tented. Thanks a lot folks especially Zazen. This Ubuntu experience just keeps getting better and better.
John.

---

### Post by HavocXphere on 2009-06-20
> **neal.m.master said:**
> I'm not sure if its even possible to defrag ext3.
Possible yes. Necessary no.

The performance gain is very small as it is not very susceptible to fragmentation.

---

### Post by kostkon on 2009-06-20
A good app you can use is [*BleachBit*]("http://bleachbit-project.appspot.com/").

---

### Post by Chevanova on 2009-06-20
Funny, i havent really thought about doing a defrag or any type of clean up seeing as my ubuntu is running so smoothly. Anyways thanks for the janitor hint, i might give it a whirl some day

---

### Post by credobyte on 2009-06-20
Cleaning Firefox cache should be enough :p

---

### Post by Yellow Pasque on 2009-06-20
> **bodhi.zazen said:**
> Ubuntu now includes a "janitor"
IMHO, the "computer janitor" is a dangerous n00b trap.

---

### Post by el.otro on 2009-06-20
I have used the "Janitor" couple of times, but it is not as secure as it should be....
   
It erases "outdated" packages (it tells you you might need them, though), and one time it screwed up my X.org, and later flash, and I was pretty new to ubuntu, and using the terminal was a scarry trip...(I survived though).
   
I wouldn't use it at all, I find ubuntu to be clean enough, and it cleans up your temp automatically when you shutdown (unless you set it to remember your session, obviously).  

I agree with Temüjin, it's a trap.
  
Housekeeping, I'd say, is limited to erasing programs you don't use, they are an unecessary use of space (however little) and security-wise a "risk", say for example, that you have Koffice, OpenOffice, and AbiWord, try the three of them and choose one.  Well, that's what I do.

---

### Post by Extreedoc on 2009-06-21
No need to worry about me catching my n00bs in a trap, I have Intrepid and it doesn't seem to have Janitor anyway but thanks for the warning.

---

### Post by 3rdalbum on 2009-06-21
I have found some use for Computer Janitor (it found some old packages I didn't need anymore), but I took its advice merely as a suggestion. New users probably shouldn't try it at this stage.

The system basically clears out a lot of ancient logs as it goes along, and temporary files are stored in a location that gets erased on boot.

Every month I'd do this:

```
sudo apt-get autoclean
```

Deletes old package archives that can no longer be downloaded. On Ubuntu it's rare that you have any of those.

If you're running low on disk space:

```
sudo apt-get clean
```

Deletes all cached package files - you don't need them, they just save you from having to download the package again if you need to reinstall it.

If you're running low on disk space or are about to dist-upgrade:

```
sudo apt-get autoremove
```

Removes (uninstalls) packages from your system that were automatically installed in response to a program you no longer have. For instance, if I install "sox", it will automatically install "libsox-fmt". If I remove sox, it will keep libsox-fmt. The autoremove function will remove libsox-fmt, assuming I have already removed sox.

Don't just blindly use apt-get autoremove. It tells you first what packages it will remove, and be sure to review this list if you don't want to potentially break something.

---

