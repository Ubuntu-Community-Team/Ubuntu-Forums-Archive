---
title: "BIOS won't boot off CD--how to install Linux?"
date: 2009-05-24
forum: General Help
---

### Post by fiddler616 on 2009-05-24
Hello,
I have a clunker of a computer (64MB RAM, 433 mHz??, ~5GB hard drive) that is doing nothing special with Windows 98. I'd love to put Linux on it (I'm on the fence between CrunchBang, Arch and Ubuntu Server), but the BIOS only supports booting off the hard drive or a floppy disk.

I've found several forum pages (not here) about using a floppy disk to boot off a CD, but the tutorials have been very unclear. I also thought about putting the hard drive in a different computer, installing, and then swapping it back, but it has a few more pins than the other desktop's hard drive connector (I'm sorry I can't be more specific, I'm hopeless with hardware). I've also though about crazy things like installing Linux on a different hard drive and using Clonezilla to write that image on the appropriate computer over the network, but that seems very questionable.

So, is there anything I can do? Thanks.

---

### Post by Old_Grey_Wolf on 2009-05-24
Try one of these suggestions:
[https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD](https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD)

---

### Post by snowpine on 2009-05-24
Your specs are too low for Ubuntu or Crunchbang, not sure about Arch.

If you have a working OS, you can use Unetbootin, maybe DSL (damn small linux)?. There are also a few tiny linux distros that will boot from floppy.

---

### Post by albinootje on 2009-05-24
> **fiddler616 said:**
>  I have a clunker of a computer (64MB RAM, 433 mHz??, ~5GB hard drive) that is doing nothing special with Windows 98. I'd love to put Linux on it 

To me the best choice for installation sounds like getting the hard disk out, and then put it in another old machine which has a similar old interface for that hard disk, and then do the installation. Ask friends or relatives to help you with that.

And perhaps you can tell us what you'd like to do with that machine, because the specifications of that machine are unfortunately very low for a recent desktop Linux installation. (It would be fine for a simple file- or webserver).

Worth trying would Puppy Linux or some other like here : [http://tiny.seul.org/en/](http://tiny.seul.org/en/)

---

### Post by jimmy the saint on 2009-05-24
If you are VERY comfortable with linux and are willing to invest some time (trial and error no doubt) go with Arch and a minimal winow manager like Openbox.  That is the setup I have on my laptop and its great.  It was definitley a learning experience though. The nice thing about Arch is that you only have what you installed.  The bad thing is it is a real pain sometimes to figure out what you need if you are used to Ubuntu just having it!  

Alternately DSL (damn small linux) or puppy linux might work.

---

### Post by fiddler616 on 2009-05-24
Victory! I'm in the middle of an Ubuntu Server install, after following Old_Gray_Wolf's link (I made a boot floppy).

I've decided that I'll use it as a CLI playground (former moderator K.Mandla swears by using the terminal on his [blog]("http://kmandla.wordpress.com/"), and it's not quite the same on a terminal emulator).

Thanks, all of you!

---

