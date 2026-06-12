---
title: "New computer to play w/ Linux!!!  Help with install ideas"
date: 2009-02-12
forum: General Help
---

### Post by tuproxy on 2009-02-12
Ok, I'm really glad to be back and I'm ready to sink my teeth into Linux. 

I just put together a new system with an Asus Mobo, quad core intel, 8gb ram, Dual 74gb raptors, 5 500gb drive array...

Well, I want to run a server and I know that this is an over-kill for a simple file-server but I thought I would install the desktop as well.  

I'd like to get suggestions as to what install.  Is it possible to run all the server apps on the desktop install?  Can I just add the packages later?

I'm also planning to install another OS that has a kitty-cat name; just to learn an alternate OS.  

Please give me some suggestions as to what I can do with the desktop vs server version.  

Also what about 8.04 vs 8.10?

---

### Post by Tim Sharitt on 2009-02-12
You can add anything to the desktop install which is available for the server install (as well as install desktop apps on the server). 

What you install really depends on what you need it to do. Running unneeded applications will only drain resources from other processes.

---

### Post by phirestalker on 2009-02-12
the server version will support the desktop as well, all you have to do is install the server version and then once you have internet connection you can type apt-get install ubuntu-desktop, and that will take care of installing the stuff that would get installed with a desktop install.

8.04 is the LTS or Long Term Support version, which has the benefits two-fold of being, one step back from the bleeding edge (ie more stable, great if running a server) and also it is "supported" longer which I'm not so sure about since it is community supported anyway *shrug*

Tim's right about the resource drain. Some people would argue that the default desktop install is a little "bloated", but how you want to do it depends on your knowledge/patience. you could install X then install gnome and go from there, or you could install ubuntu-desktop and then remove things that don't need to be on a server (compiz for example).

---

### Post by punx45 on 2009-02-12
that system sounds to be pretty capable whichever route you take to the server.  if you have a second computer handy i suggest going with the server install and building from there.   it encourages more learning.   and if you find yourself tearing your hair out you can very easily install the GUI.

as for the kitty-kat OS, check the following link for resources.   last i read the compatible hardware is pretty slim, and if i recall correctly, the BIOS is pretty important, but some of the working boards were ASUS, so you might be on the right track.

[http://wiki.osx86project.org/wiki/index.php/Main_Page](http://wiki.osx86project.org/wiki/index.php/Main_Page)

---

### Post by tuproxy on 2009-02-12
> **punx45 said:**
> that system sounds to be pretty capable whichever route you take to the server.  if you have a second computer handy i suggest going with the server install and building from there.   it encourages more learning.   and if you find yourself tearing your hair out you can very easily install the GUI.

as for the kitty-kat OS, check the following link for resources.   last i read the compatible hardware is pretty slim, and if i recall correctly, the BIOS is pretty important, but some of the working boards were ASUS, so you might be on the right track.

[http://wiki.osx86project.org/wiki/index.php/Main_Page](http://wiki.osx86project.org/wiki/index.php/Main_Page)

Thanks for your reply.  The only reason I was considering the desktop version is b/c I wanted to try some apps out that are available for it.  

I also have a similar PC that is running Vista Business 64, a laptop running Vista home, and I have 2 P4's with tons of HD's. 

DOes anyone have any experience with a bootloader for multiple installs? I'd like to load a few OS choices.

---

### Post by Tim Sharitt on 2009-02-13
Rhe grub bootloader seems to work with nearly everything. At the least you can chainload other bootloaders.

---

### Post by punx45 on 2009-02-13
yeah and check the site i linked for sure, but im under the impression that osx86 doesnt play very nice with multi boots

---

### Post by williane on 2009-02-13
WMware and do all three =D

---

### Post by tuproxy on 2009-02-13
> **punx45 said:**
> yeah and check the site i linked for sure, but im under the impression that osx86 doesnt play very nice with multi boots



I looked and it looks like my Vista machine is the idea machine to run OS# on.  Thank you very much for that link.  

I really have no intention of running OS# much but I would like to know if it is worth it to buy one.  I don't buy before i try.

---

### Post by tuproxy on 2009-02-13
> **williane said:**
> WMware and do all three =D

Actually I think that is going to be the route I take. I'll install 8.04 LTS Desktop and then install server and OS# on the VM's.  I have gotten away from VM's in the last year b/c I heard about a number of security issues.

---

### Post by punx45 on 2009-02-14
> **tuproxy said:**
> I looked and it looks like my Vista machine is the idea machine to run OS# on.  Thank you very much for that link.  

I really have no intention of running OS# much but I would like to know if it is worth it to buy one.  I don't buy before i try.

if you live near an apple store, they are very accommodating for trying (as long as you dont use myspace or facebook, haha)  i have heard that someone wrote a book on a mac in one of the stores.   good luck either way.   i like the OS.  its what i use as a main desktop.

---

