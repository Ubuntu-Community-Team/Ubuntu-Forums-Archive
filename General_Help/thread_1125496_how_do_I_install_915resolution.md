---
title: "how do I install 915resolution?"
date: 2009-04-14
forum: General Help
---

### Post by IxAxU on 2009-04-14
HI,
Instruction on this page >> [http://packages.ubuntu.com/dapper/i386/915resolution/download](http://packages.ubuntu.com/dapper/i386/915resolution/download)

> If you are running Ubuntu, it is strongly suggested to use a package manager like aptitude or synaptic to download and install packages, instead of doing so manually via this website.

You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:

deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) dapper main universe

Replacing cz.archive.ubuntu.com/ubuntu with the mirror in question. 
How can I do that? I tried dir /etc/apt/sources/ but that doesn't work.
I tried to install the .deb when I downloaded a mirror.. but it said that xserver-xorg-video-intel was conflicting with 915reolsution.

---

### Post by ajmctaggart on 2009-04-14
If you want to add a source you would need to use an editor...I like nano, but many use gedit
```

sudo gedit /etc/apt/sources.list
sudo nano /etc/apt/sources.list
```

After you get in there, I think it will be clear how to format that line for the particular repository you wanted to add...just remember that sometimes when upgrading your Ubuntu Distro, it may revert or simply deactivate (by using ##) so you may need to reactivate later...

After that, you can do a 
```
sudo apt-get update
sudo aptitude update

```
I like aptitude, most use apt-get nowadays I believe...

---

### Post by Seq on 2009-04-14
915resolution is not needed with the current -intel driver. Is there a specific reason you wanted to use it?

---

### Post by ajmctaggart on 2009-04-14
I didn't even realize it, but I think he/she meant to can the 915 and install the intel...

At any rate, I just wanted to explain how to add the repository, whatever happens after that...oh well :lolflag:

But seriously, Ixaxu what Ubuntu are you using?

---

### Post by machadoug on 2009-06-24
Dear Seq,

I don't know why IxAxU needed 915resolution, however I need it to enable higher screen resolution on my system.

I had 8.10 installed with 1280x[FONT=Verdana]800[/FONT] screen resolution, however when I updated to 9.04 I only get 1024x768. 
I also use another monitor at 1600x900 which is working at 1024x768.

My hardware:

[LIST]
[*]Notebook: Acer Aspire 5610
[*]Graphic Card:  [FONT=Verdana]Intel Graphics Media Acelerator 950[/FONT]
[LIST]
[*][FONT=Verdana]Native resolution: [/FONT] 1280x[FONT=Verdana]800[/FONT]
[/LIST]
 
[/LIST]
Your help is much appreciated.

Regards,

---

