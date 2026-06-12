---
title: "Desktop effects could not be enabled"
date: 2011-03-15
forum: Desktop Environments
---

### Post by Dr.Paneas on 2011-03-15
Hello guys, 

I have to open another DECNBE thread just because I didn't manage to find a solution by studying all the other related stories that took place here in Ubuntuforums.org.

Here is my output from Compiz-Check
```

paneas@ubuntu:~/Downloads/compiz-check$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

but...
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=186198&d=1300229148[/IMG]

---

### Post by Forlong on 2011-03-16
Interesting. What's the output of
```
compiz
``` in a terminal?

---

### Post by Dr.Paneas on 2011-03-16
> **Forlong said:**
> Interesting. What's the output of
```
compiz
``` in a terminal?

Here is the output you asked for:
```

paneas@ubuntubox:~$ compiz
Blacklisted PCI ID 8086:0112 detected

Launching fallback window manager

```After pressing Ctrl+C to terminate the command, all of my windows bars were gone and the keyboard was not working. I had to restart the machine and then things turned back normally.

---

### Post by andersonvom on 2011-04-03
I have a Dell XPS15 with GeForce 540M with Optimus / Intel video card and I can't seem to be able to run compiz either.

Everything seems to be able to run it, though:[INDENT]andersonvom@yoda:~$ [uname -a]("http://pastebin.com/YRdvxpcT")
andersonvom@yoda:~$ [glxinfo]("http://pastebin.com/rv3gTPuv")
andersonvom@yoda:~$ [./compiz-check]("http://pastebin.com/gTuCTkxU")
andersonvom@yoda:~$ [lspci  -v]("http://pastebin.com/Hchcd2qK")
[/INDENT]Does anybody know how can I enable compiz?

---

### Post by andersonvom on 2011-04-03
I just solved it, following the instructions on [this thread]("http://ubuntuforums.org/showthread.php?t=1465935").

Removing the ID of the video card from the blacklist will do the trick. But it has to be done modifying compiz binary file, because it's hardcoded there. After running compiz from the terminal, the ID will be listed as being blacklisted. Searching it inside compiz binary file and replacing it with something else will make it work. :D

```

sudo apt-get install ghex
sudo ghex2 /usr/bin/compiz

```

For future reference:
Dell XPS 15
2GB Nvidia GeForce 540M with Optimus
Intel GMA HD i915

---

