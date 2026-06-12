---
title: "Debloating Mini 9"
date: 2010-08-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by epb223 on 2010-08-23
My Mini 9 no longer has the hard drive space for the updates from Dell; as a result, I've got my eye on uninstalling some of the bloatware it came with (games, etc.), but I can't figure out how to get to any of it. I'm assuming that I can free up enough space this way to continue to get the updates, as long as I'm careful about cleaning up the packages with sudo apt-get clean. Am I wrong about this?

Thank you,
Edward

---

### Post by goofynewf on 2010-08-23
What version of Ubuntu are you using?  I am using 10.4 NBR for my Mini 9.

I had to remove a lot of programs, too, to free up space.  If you are using 10.4, there is the Ubuntu Software Center, which allows you to install and remove programs very easily.  I removed all the pre-installed games since I don't use them and it only helped a little.

On a side note, I had issues this past weekend with my mini.  I previously had less than 1 GB free.  I had to reinstall 10.4 and somehow, I now have 4 GB free.  Not sure how it happened and how I have that much remaining, but I won't complain.

---

### Post by mörgæs on 2010-08-23
A system never gets smaller than after a clean install. 

If you want to try to salvage some space on an existing system, apt-get clean, autoclean and autoremove are worth trying. There are many more options in apt-get, it is also a great tool if something goes wrong.

---

### Post by epb223 on 2010-08-25
I'm still on 8.04; I was going to go to 10.4, but there were so many complications with making a flash drive and so forth that I just gave up on the project more than a year ago, figuring that it was simpler to just stick with what was there for the limited purposes I use the netbook for. Then this problem came up. So without a handy utility such as you describe, any idea how I can uninstall those games, etc.?

---

### Post by mörgæs on 2010-08-25
> **epb223 said:**
> So without a handy utility such as you describe, any idea how I can uninstall those games, etc.?

You already have apt-get on the system. It is an essential part of Ubuntu.

Uninstall can be done through Synaptic, if you prefer.

---

### Post by epb223 on 2010-08-25
> **mörgæs said:**
> You already have apt-get on the system. It is an essential part of Ubuntu.

Uninstall can be done through Synaptic, if you prefer.

So the syntax on that would be, apt-get remove followed by the name of, e.g., the game? Because I can't locate the files corresponding to these things; all I can find are loads of files with names it's impossible for me to match up with the applications.

---

### Post by mörgæs on 2010-08-25
Correct. As I mentioned earlier, apt-get is a great program for system maintenance. There are many good manuals on the web, if you want to know more about it.

---

### Post by mörgæs on 2010-08-25
By the way, if you want a small system I would recommend building from the bottom up rather than installing a full system and then removing packages. There is more information here:

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by epb223 on 2010-08-28
Unfortunately, when I do sudo apt-get remove chess, for example, it says that it can't find the package "chess". I'm assuming this is because the package is named something else, but I can't find any packages on this system with recognizable titles.

---

### Post by mörgæs on 2010-08-29
If you search for 'chess' in Synaptic, you will see which packages are installed.

---

### Post by Cowchip7 on 2010-08-29
Synaptic is the best way to go. You can search for the games, dvd player, etc... whatever you don't want, and then completely remove them.

---

### Post by ugm6hr on 2010-08-30
If the problem is space, just use apt-get clean, as you had intended.

```
sudo apt-get clean
```

This just deletes all the files (apart from the lock file) from /var/cache/apt/archives

If you want to keep them, just copy them to a USB flash before running the command. It's easy enough to restor back later.

---

