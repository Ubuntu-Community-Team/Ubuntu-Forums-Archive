---
title: "Couple Questions"
date: 2008-12-22
forum: General Help
---

### Post by lurid on 2008-12-22
I recently started playing around with linux distros, right about the time I bought my laptop (Toshiba Satellite M305-4848) and I have a couple issues:

1) It feels kind of buggy and typing feels laggy at times.  Also there is a weird graphical glitch like static blurring when I maximize a window sometimes.  Any ideas on things I could do to improve performance / figure out why i'm having problems?

2) How do I give myself access to rename / delete files like within a music collection?  I understand the sudo su command from terminal, but that doesn't really help me here.  What am I missing?

---

### Post by SlidingHorn on 2008-12-22
well, it would be more helpful to know what version of *buntu you're running and all the extras, but I always had those issues with my slower machines if I used compiz.  

when it comes to the music, (**don't do this until someone smarter than me comes along and approves it**) try "sudo chown" on the files

---

### Post by Nathan Sweeney on 2008-12-22
> **lurid said:**
> I recently started playing around with linux distros, right about the time I bought my laptop (Toshiba Satellite M305-4848) and I have a couple issues:

1) It feels kind of buggy and typing feels laggy at times.  Also there is a weird graphical glitch like static blurring when I maximize a window sometimes.  Any ideas on things I could do to improve performance / figure out why i'm having problems?

2) How do I give myself access to rename / delete files like within a music collection?  I understand the sudo su command from terminal, but that doesn't really help me here.  What am I missing?

What type of graphics card does your laptop have?  IE, is it Intel, Nvidia, or ATI?  If you go to System -> Administration -> Hardware Drivers, are there any proprietary drivers that you can enable?

For the music and rename/delete, where are the files from?  What directory are they in?  This may be a permissions issue if you copied them from a different partition.

---

### Post by lurid on 2008-12-22
> **Nathan Sweeney said:**
> What type of graphics card does your laptop have?  IE, is it Intel, Nvidia, or ATI?  If you go to System -> Administration -> Hardware Drivers, are there any proprietary drivers that you can enable?

For the music and rename/delete, where are the files from?  What directory are they in?  This may be a permissions issue if you copied them from a different partition.

"There are no proprietary drivers in use on this system" is the only message I see when I try that.  It uses an Intel integrated GMA 4500MHD.

They're from backup DVDs I made, they're in home/user/music.

I'm running Ubuntu 8.10 (Intrepid) kernel 2.6.27-9-generic gnome 2.24.1

---

### Post by ad_267 on 2008-12-22
To make sure you have correct privileges on the music files do:
```
sudo chown -R $USER:$USER $HOME/music
sudo chmod u+w -R $HOME/music
```

You could try disabling visual effects under System - Preferences - Appearance - Visual Effects if the graphical glitches are too annoying.

---

### Post by Bölvaður on 2008-12-22
[QUOTE=lurid;6415561
They're from backup DVDs I made, they're in home/user/music.[/QUOTE]

When you copy from a cd or dvd the files remain read only. (This can also happen when copying from different file systems that do not have file permissions).
So you need to use chown for changing the owner of the files with the -R for recursively change every file beneath that place in the tree.
The same has to be done with chmod for the permissions. chmod 644 seems to be the default (chmod u=rw,go=r isnt it?)

---

### Post by hyper_ch on 2008-12-22
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

