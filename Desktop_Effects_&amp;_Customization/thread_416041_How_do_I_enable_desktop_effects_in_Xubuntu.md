---
title: "How do I enable desktop effects in Xubuntu?"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by elijahclarity on 2007-04-20
In Ubuntu 7.04, enabling desktop effects was just a matter of Desktop>Preferences>Enable Desktop Effects.

But Ubuntu7.04 ran a bit slow on my PC with 256MB RAM so I did a clean install of Xubuntu 7.04.

But I can't figure out a way to enable desktop effects in Xubuntu 7.04. Is there a way to enable desktop effects in Xubuntu as easily as I did in Ubuntu (Gnome)?

Thanks for your help.

---

### Post by kornhead127 on 2007-04-20
Maybe this thread will be of some assistance.
[http://ubuntuforums.org/showthread.php?t=232883](http://ubuntuforums.org/showthread.php?t=232883)

---

### Post by notwen on 2007-04-20
Check [this]("http://ubuntuforums.org/showthread.php?t=414223"), easy way to enable compiz's wobbly/cube effects.  The rest you'd hafta configure else where.

---

### Post by elijahclarity on 2007-04-21
"Compiz comes pre-installed on Fiesty, you just simply have to enable Desktop Effects under Applications--->Settings--->Desktop Settings"

Is this true? Is it THAT EASY on Xubuntu 7.04 too? If yes, I'm off to install Xubuntu Feisty:D

That is why I was wondering if I should have to install stuff like beryl etc. on Xubuntu when in Ubuntu (Gnome) it was all built-in so to say.

---

### Post by notwen on 2007-04-21
Compiz does indeed come pre-installed, so I guess it is that easy.  I don't use my xubuntu install that much, but post back if you have any issues.  Good luck. =]

---

### Post by shavenlunatic on 2007-07-11
was reading this thread hoping to find an answer.. didn't find a siumple one so I thought i'd try something simple

Synaptic, search for compiz.. mark "desktop-effects" for installation, whicih will add all its dependancies... once finished, hit Alt+F2 and run "desktop-effects"

jobs a done.. simple :)

---

### Post by Bart_D on 2007-08-21
Sorry for digging up an old thread but there's no point in me starting a new one for no reason, since the question is the same....

I followed TSElliot's guide to install the Nvidia Graphics driver for my graphics card here:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_1_-_OFFLINE_INSTALLATION](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_1_-_OFFLINE_INSTALLATION)
I used Method 1 ONLINE Installation.

All went well.  Next, I wanted to enable desktop effects.  I did a search for compiz and marked desktop-effects for installation.  IT added dependencies and installed.  I then hit Alt+F2 and entered "desktop-effects" and got a message:

[COLOR="Red"]**[SIZE="4"]The Composite extension is not avaliable[/SIZE]**[/COLOR]

Is there another way to get desktop effects enabled in Xubuntu 7.10?

---

### Post by Anticitizen2 on 2007-08-21
I an having the same problem as the poster above, except I am using Ubuntu 7.04.  I used Envy to install the latest nvidia driver on my geforce 8800 gts.  The driver appears to work just fine, but I am getting the "composite extension is not avaliable" error.  Any help in the matter would be great.

---

### Post by ArtF10 on 2007-08-21
Hehe, I installed Ubuntu 7.04 and the message shows up.  I read somewhere in this forum(can't remember the link) that certain videocards do not support this feature in Ubuntu.

Very frustrating....especially because SamLinux runs with ALL 3D effects WITHOUT ANY PROBLEMS AT ALL!!!!  I want to stick with Ubuntu, so I am going to install Xubuntu(hey if you can't get the bling bling, you're better off with better responsiveness....PLUS, mine's an old machine) and forget about this option altogether.  This was the very reason why I purchased a NEW card and now I find out that it won't suffice.  I am gutted.

---

### Post by ArtF10 on 2007-08-22
Well folks, it may be a bit more complicated than we're making it out to be.  If you've got Ubuntu, here's what I found:

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by ArtF10 on 2007-08-22
oh by the way gents, try the above at your own risk and if you do decide to take the plunge, do post the result as it would help others facing the same problem.

---

### Post by Anticitizen2 on 2007-08-22
Thanks for the info ArtF10, I will probably give that a shot.  Im still a newb when it comes to ubuntu, so in the event that something goes wrong, what would be the best way to reverse the damage?

---

### Post by ArtF10 on 2007-08-22
I don't know...I too am new to Linux.  HOWEVER, I tried doing this from the Ubuntu Live CD.  I first updated my graphics drivers using TSeliot's guide and then followed the steps in the link I posted.  IT went through and after a massive amount ofupdating, it said something like Compiz is already installed or something to that effect...can't remember exactly what.  It said ti reboot but since I am running it from the CD I decided not to.  Anyways I went to desktop effects and the same message came up.  I changed Composite fromDisable to Enable in xorg.conf and THE SAME MESSAGE CAME UP.  Frustrating.

---

### Post by gtrtx on 2007-08-22
I've got it working with xfce, however I'm not using Xubuntu, I've just installed the xubuntu-desktop on top of  ubuntu studio because I prefer xfce over gnome. 

However, It's not using xfce's window decorations but rather gnomes. Also, I had to run it first under my gnome desktop....otherwise I got no decorations. I'm not using emerald.

I'm using Trevino repos as I've had problems with all other repos. At this time I'm using the 0.5.1 version until they get all the ccsm stuff worked out in the current version. 

Anywho, I've had it running this way for quite some time without issue. 

Just thought I'd throw this out there.

---

### Post by ArtF10 on 2007-08-22
Ok, so I rebooted with the Live-CD, installed the graphics cards drivers again and this time DID not go to the link I gave above about Compiz Fuzion.  I just went to xorg.cong and changed Composite from Disable to Enable and then selected desktop effects from System.  I got it ro run from the Ubuntu Fiesty Fawn Live-CD BUT, after about 10 seconds all then madness broke lose.  Thje workspaces on a cube was selected but the cube did not show up after about 10 seconds.  So switched between workspaces, saw the cube and all and was happy.  Then the cube dissapeared.  The workspaces were reduced from 4 to 1 so I manually changed them back to 4 but still no cube.  The Terminal will no longer open....it's frozen.  The control bar at the top of each window..you know the one with the minimize, maximize and close buttons...has dissapeared so I cannot drag windows to test if they are wobbly.  I selected wobbly windows but it won't work.

I don't know if this is just because it is the Live-CD or what....this is really confusing.

---

### Post by ArtF10 on 2007-08-23
[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

If someone gets it to work in XUbuntu please post here saying that you did.  Also, if you had to make modifications to get if working in XUbuntu, please post those as well.

---

### Post by kmcq on 2007-08-23
> **gtrtx said:**
> I've got it working with xfce, however I'm not using Xubuntu, I've just installed the xubuntu-desktop on top of  ubuntu studio because I prefer xfce over gnome. 

However, It's not using xfce's window decorations but rather gnomes. Also, I had to run it first under my gnome desktop....otherwise I got no decorations. I'm not using emerald.

I'm using Trevino repos as I've had problems with all other repos. At this time I'm using the 0.5.1 version until they get all the ccsm stuff worked out in the current version. 

Anywho, I've had it running this way for quite some time without issue. 

Just thought I'd throw this out there.

mind explaining how you did it?

---

### Post by ArtF10 on 2007-08-23
He's "installed" it under Gnome and is now (after downloading Xubuntu-desktop) using it under Xfce.  That's an interesting suggestion.

Do you still have Gnome on your system or did you get rid of it after getting these effects to work in Xfce?

---

### Post by Bart_D on 2007-08-25
After a lot of searching on the net, I doubt that this is possible in XUbuntu.

Sigh!

---

### Post by ArtF10 on 2007-08-26
Actually, if you check out the first post on this page;

[http://ubuntuforums.org/showthread.php?t=515076&page=43](http://ubuntuforums.org/showthread.php?t=515076&page=43)

It shows XUbuntu with Emerald....I'm assuming that the person who posted this screenshot must have found a way to get Compiz Fusion to also work with XUbuntu.

---

