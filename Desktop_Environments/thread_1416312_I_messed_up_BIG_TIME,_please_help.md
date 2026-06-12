---
title: "I messed up BIG TIME, please help"
date: 2010-02-25
forum: Desktop Environments
---

### Post by KannedFarU on 2010-02-25
Okay so I messed up BIG TIME and you guys can call me a noob or whatever. I don't care I just really need to get this server back up and running that I totally ruined. So I wanted to convert my server over from Ubuntu Desktop Edition to Server Edition so I thought it would be pretty slick if I did so just by running the following commands:

$ sudo gdm-stop
$ sudo apt-get remove gdm*
$ sudo apt-get remove gnome*
$ sudo apt-get autoremove

Pretty slick huh? Nope I lost just about everything that made Ubuntu useful. My network manager is nowhere to be seen, trying to mount something like a scd from the command line doesn't seem to work anymore, and man is no longer installed :cry:.

I was thinking about reinstalling Ubuntu and saving myself a butt load of time, but there's some data and an SVN repository that I need to recover from this machine before I do that. Since I'm having trouble mounting and cannot connect to the network, does anybody have any idea or suggestions for me to get out of this mess? If I could just mount a thumb-drive and get the repository off that would be good enough for me.

Any help is appreciated, thanks guys
~Kanned

---

### Post by prshah on 2010-02-25
> **KannedFarU said:**
> 
$ sudo apt-get remove gnome*

You can get hold of the "alternate" cd of the version of ubuntu you have installed. Insert the CD, then use the command apt-cdrom to index the CD and add it to your sources.list```
sudo apt-cdrom -f add
``` Follow the prompts to completion.

Then use the command```
sudo apt-get install ubuntu-desktop
``` to restore your desktop.

For the future, to convert to "server" edition, have it start at a different runlevel to avoid loading the GUI (or you may have to edit runlevel values; not sure about this.) Post back if you want to do this.

---

### Post by MooPi on 2010-02-25
Try this in conjunction with the previous post.  ```
sudo apt-get install xorg openbox obconf pcmanfm
```This will install a lightweight desktop environment called Openbox. Since you don't want the overhead of gnome this should keep it light. You'll need to start your x-session with ```
startx
```A right click of the mouse gives a minimal menu and access to terminal. Good luck.

---

### Post by KannedFarU on 2010-02-26
> **prshah said:**
> ```
sudo apt-cdrom -f add
``` 

Okay this did not work. It said something about skipping over non-existing file /blah/blah/blah jaunty/main/Packages and jaunty/restricted/Packages.

I cd'd into those directories and saw that the packages were gzipped, so maybe it doesn't like that? Is there a way I can copy these files into a directory and uncompress them then add them to my sources.list?

---

### Post by trimmer on 2010-02-26
If your source.list has not changed and you have access to the Internet you should still be able to access the UBUNTU repositories.

In that case you should be able to so a simple:

sudo apt-get install ubuntu-desktop

That should get you back up and running with all that you removed.

---

### Post by KannedFarU on 2010-02-27
No. Please read my original post. I DO NOT HAVE A NETWORK MANAGER. I CANNOT ACCESS MY HOME NETWORK OR THE INTERNET.

---

### Post by prshah on 2010-02-27
> **KannedFarU said:**
> /blah/blah/blah jaunty/main/Packages and jaunty/restricted/Packages.

the packages were gzipped, so maybe it doesn't like that?

Exact output please? You can use a digital camera to capture a screenshot, if convenient. Are you sure you were using the "Alternate" CD and not the live CD? (Though actually, a live CD should work as well.)

> **KannedFarU said:**
> I CANNOT ACCESS MY HOME NETWORK OR THE INTERNET.

Oow.. ears are bleeding. Actually, "trimmer" does have a point. You can use command line tools to connect to the 'net, even if you have uninstalled gnome and it's underpinnings. Post back if you want details on this.

---

### Post by KannedFarU on 2010-02-27
Okay thanks for you help guys. I had to improvise your suggestions a little bit but it seems to be working now. For clarification I will go over all the steps I did to get this working.

1.) Download "Alternate CD" of Ubuntu (I did not know existed :P) from here [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)
2.) Burn the .iso image to a disc (the proper iso way)
3.) Pop the disc into the broken machine, and boot up (running the commands didn't work for me so I allowed the disc to boot me into "Rescue a Broken Installation")
4.) Rescue mode had a network manager that connected to the internet and let me log into my broken partition. Once I got there I ran the following commands:
```
# sudo apt-get install ubuntu-desktop
```
5.) Reboot machine

Thanks again for your help, could not have done it without this community :P

---

### Post by asmoore82 on 2010-02-28
you can manually dispatch a DHCP client to get connected to the net
Then, reinstall the missing packages...

```
sudo dhclient3 eth0
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

