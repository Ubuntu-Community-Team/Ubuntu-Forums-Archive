---
title: "XFCE - Replace Thunar"
date: 2008-03-09
forum: Desktop Environments
---

### Post by mabryant on 2008-03-09
I have been looking around for the last week or so for a guide on how to replace Thunar. I have found many guides for doing this in Gnome and replacing Nautilis, but not for XFCE.  What I want to do is for Konqueror to launch when I click on a mounted volume on the desktop or click on a link in my "Places" panel applet.
I just can't find the right file to change.

Any ideas?

Mark

---

### Post by Gen2ly on 2008-03-09
its doable I suppose, but I don't think many have tried this.  XFCE is meant to be a light desktop, adding konqueror would signifigantly change that.  There's another file manager called Pcman thats light if XFCE's does fit the bill.

---

### Post by kerry_s on 2008-03-10
do you plan on using thunar at all?

i was thinking maybe link the thunar command to konqueror, something like->
sudo mv /usr/bin/thunar /usr/bin/thunar1
sudo ln -s /usr/bin/konqueror /usr/bin/thunar

[COLOR="Red"]WARNING![/COLOR] i have never done this and don't even know what might go wrong. but it is reversible and in theory any command that calls thunar would then launch konqueror in it's place.

you been warned, wait for more input from others, someone might have a better idea.

---

### Post by mabryant on 2008-03-10
I thought about changing the link, but I want to have the ability to use Thunar if I want to. I actually like Thunar, but it is missing a feature that, for me, is a show stopper: the ability to browse SMB networks. I VPN into work a lot and have to use files on the network and it a real pain to have to mount all the servers and shares when I want to use them.  With Konqueror I can just type in SMB://server and get to my files.

---

### Post by kerry_s on 2008-03-10
you would still be able to use thunar, just have to use the command thunar1 or what ever you rename it to.

---

### Post by mabryant on 2008-03-10
I changed the link and it appears to be working great.  Thanks.

---

### Post by ctyc on 2008-03-10
but why

---

### Post by dotancohen on 2008-03-11
Know that Konqueror depends upon KDE, so you will need to install a lot of packages to get konqueror. And most of the libs will be loaded into memory when you run Konqi, so your lightweight desktop just became as heavy as KDE. Actually, heavier, as you are now running both KDE and XFCE.

---

### Post by erginemr on 2008-03-11
> **dotancohen said:**
> Know that Konqueror depends upon KDE, so you will need to install a lot of packages to get konqueror. And most of the libs will be loaded into memory when you run Konqi, so your lightweight desktop just became as heavy as KDE. Actually, heavier, as you are now running both KDE and XFCE.

But in the mean time, we should not forget his objective which is to find a hassle-free way to view the samba network. I have no experience in samba but if any other light-weight browser (be it pcmanfm, krusader or maybe rox) can fulfill this demand, suggestions are welcome.

---

### Post by x1a4 on 2008-03-11
> **kerry_s said:**
> do you plan on using thunar at all?

i was thinking maybe link the thunar command to konqueror, something like->
sudo mv /usr/bin/thunar /usr/bin/thunar1
sudo ln -s /usr/bin/konqueror /usr/bin/thunar

No need to rename the link.  /usr/bin/thunar points to /usr/bin/Thunar, simply changing what the link points to, and calling Thunar directly is good enough. 

> [COLOR="Red"]WARNING![/COLOR] i have never done this and don't even know what might go wrong. but it is reversible and in theory any command that calls thunar would then launch konqueror in it's place.

There will be issues with Konqueror as it's too tightly integrated with KDE.  Nautilus on the other hand will work much better.

---

### Post by mabryant on 2008-03-11
> **x1a4 said:**
> 
There will be issues with Konqueror as it's too tightly integrated with KDE.  Nautilus on the other hand will work much better.


I tried Nautilus, but every time I opened it, Gnome took over my settings from XFCE.  I understand the concerns over using Konqueror in XFCE defeating the purpose of the lightweight environment, but the easy use of Samba shares trumps it in my case.  I don't have a very ancient box, but it still is 4-5 years old (AthalonXP 2100, 1GB memory) and XFCE using Konqueror is still much more responsive than KDE or Gnome was.

If anyone has any other easy to use Samba file managers, I would be very interested in trying them. Having changed the link, my places panel applet now fire Konqueror, but the desktop icons for mounted volumes still use Thunar. I don't know if I'm going to be able to change that since those icons seem more integrated with Thunar/XFCE than the places applet.

Mark

---

### Post by erginemr on 2008-03-11
I don't know if it helps, but the following links suggest a way to add quasi-native samba support to Thunar:
[http://grumpymole.blogspot.com/2006/12/xubuntu-browsing-samba-shares-with.html](http://grumpymole.blogspot.com/2006/12/xubuntu-browsing-samba-shares-with.html)
[http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131)

---

### Post by x1a4 on 2008-03-11
> **mabryant said:**
> I tried Nautilus, but every time I opened it, Gnome took over my settings from XFCE.

Run nautilus with the **--no-desktop** option.  Create the following script: **/usr/local/bin/myfm** with the following contents:
```

#!/bin/sh
/usr/bin/nautilus --no-desktop

```

and recreate the /usr/bin/thunar symlink pointing it to /usr/local/bin/myfm . 
```

sudo rm /usr/bin/thunar
sudo ln -s /usr/local/bin/myfm /usr/bin/thunar

```

This will make Nautilus your default file manager and run without replacing the XFCE desktop and window manager. 

You'll still be able to use Thunar by running /usr/bin/Thunar .

---

### Post by ldrn on 2008-05-22
> **x1a4 said:**
> No need to rename the link.  /usr/bin/thunar points to /usr/bin/Thunar, simply changing what the link points to, and calling Thunar directly is good enough. 
Thanks! I wanted to replace Thunar with Dolphin, and this same trick worked great.

For all the naysayers about performance, don't worry. Not only am I running XFCE and KDE4 apps mixed, I'm also starting up a few KDE3 ones, so I get to run three UI libraries at once on my poor low-powered via processor. ;)

---

### Post by kortsen on 2008-06-13
> **kerry_s said:**
> do you plan on using thunar at all?

i was thinking maybe link the thunar command to konqueror, something like->
sudo mv /usr/bin/thunar /usr/bin/thunar1
sudo ln -s /usr/bin/konqueror /usr/bin/thunar

[COLOR="Red"]WARNING![/COLOR] i have never done this and don't even know what might go wrong. but it is reversible and in theory any command that calls thunar would then launch konqueror in it's place.

[SIZE="5"]THANK YOU[/SIZE]

I found this thread while trying to find a way to make XFE my default file manager in Xubuntu HH. 

For those of you using xfe, here is an easy way to make xfe the default file manager.

1) run xfe as root.

2) navigate to /usr/bin

3) delete the symlink "thunar" (Not the executable Thunar)

4) right-click on the executable xfe and select "Symlink to ..."


[IMG]http://lars.kortsen.googlepages.com/thunar1.png[/IMG]


5) A dialog box will pop up for the name of the symlink.  /usr/bin/ will already be filled in.  Complete it by adding "thunar".


[IMG]http://lars.kortsen.googlepages.com/thunar2.png[/IMG]

6) click [Accept]


__________________

---

### Post by kortsen on 2008-07-15
The Xfce desktop seems to be linked to the Thunar executable.  I tried changing "Thunar", the executable file, and links on the desktop didn't work (for those of you who have subdirectories in your Desktop directory). And "Trash" didn't work; it seems xfe can't or won't talk to the trash applet.

I restored the Thunar _executable_ and created a thunar _symlink_ as detailed above.  The end result is that the places applet launches xfe and the trash applet launches Thunar.  I can open desktop subdirectories with the Places applet's [Desktop] link. I can live with that.

---

