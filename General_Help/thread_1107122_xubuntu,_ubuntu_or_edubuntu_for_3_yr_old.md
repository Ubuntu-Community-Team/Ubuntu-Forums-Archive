---
title: "xubuntu, ubuntu or edubuntu for 3 yr old?"
date: 2009-03-26
forum: General Help
---

### Post by sfl on 2009-03-26
[FONT="Tahoma"]I'm considering xubuntu for installation on my a 3yr old child's computer. The computer in question is an old Dell (1st gen P4 I believe) with 512mb of RAM that was just replaced for the parents. 

I was asked to set it up for surfing the web and playing games (the simple flash kind). A few questions come to mind:

1) Assuming the presence of drivers for the video card and the like, would 512mb of RAM be enough to run Firefox w/ flash on ubuntu or xubuntu? 

2) Would it be exaggerated to expect to run WINE on such hardware? Reason being that some of the games the parents already purchased are made for windows. I would bin them personally but apparently it's important to them that the child can play these.  

3) Samba. I'm assuming all flavours of ubuntu run it but then again I may be assuming too much. Would xubuntu handle this? 

P.S Alternately, would a system running a Intel Celeron 430 Conroe-L (1.8 ghz) be enough for ubuntu or would I have to go lighter (xubuntu or lighter)

Any input would be greatly appreciated. [/FONT]

---

### Post by leonardo_neo on 2009-03-26
> 
1) Assuming the presence of drivers for the video card and the like, would 512mb of RAM be enough to run Firefox w/ flash on ubuntu or xubuntu?


I have installed Ubuntu in my other laptop, which has 512 Mb RAM. It works almost good. No problem with browsing, videos, flash.

Xubuntu, is lighter version because it uses Xfce desktop environment, and not gnome. So it is claimed to be a bit faster than Ubuntu. So you can give a try to Xubuntu and see how good it works?

> Would it be exaggerated to expect to run WINE on such hardware? Reason being that some of the games the parents already purchased are made for windows. I would bin them personally but apparently it's important to them that the child can play these.


Depends on what games you are willing to run, and how much memory they demand?

> 
3) Samba. I'm assuming all flavours of ubuntu run it but then again I may be assuming too much. Would xubuntu handle this?


Ubuntu shouldn't have any problem with that, but again Xubuntu will be a 'bit' faster. Intel Celeron 430 is good enough for Ubuntu.

Again, you didn't ask any questions about edubuntu. Edubuntu has some pre-installed educational softwares. So if you wish OS for education, then edubuntu, if for performance, then Xubuntu.

P.S. All the softwares of edubuntu can be installed in Xubuntu.

---

### Post by Neo_The_User on 2009-03-26
Edubuntu. Maybe Kubuntu due to the super easy GUI (i personally hate it)

FYI, Xubuntu is much faster. It's what I use. (Except I pulled the graphical env out)

---

### Post by peakshysteria on 2009-03-26
I would go for **Ubuntu 8.10** as well. We have an older Laptop with 8.04 running very well on a P4 with Ati 9000. Originally it was setup for our 4 year old daughter with 7.04. We also have a HP mininote 2135 with Ubuntu 8.10 for the missus. We also have a machine setup for our 7 year old daughter. This has a 3 year old Celeron processor. Currently it's running 8.04. Our main machine Has a AMD Athlon 64 proccessor and 3GB mem. This one is running 8.10. Soon 9.04 :) Gcompriz is a nice game compilation for a 3 year old. Our 4 year old soon got hooked on Supertux and Frozen bubble. And from there we found Gcompriz which is suitable for more ages.

---

### Post by Neo_The_User on 2009-03-26
The entire scheme for Ubuntu looks terrible though. I rather not have a distro that looks like skin nor do I think others want something that looks like flesh right out of the box.

---

### Post by leonardo_neo on 2009-03-26
> **Neo_The_User said:**
> The entire scheme for Ubuntu looks terrible though. I rather not have a distro that looks like skin nor do I think others want something that looks like flesh right out of the box.

Politely disagree, because that can be changed very easily. :)

---

### Post by sfl on 2009-03-26
Thanks for the prompt and thorough response Leonardo. Much appreciated!

> **leonardo_neo said:**
> 
Depends on what games you are willing to run, and how much memory they demand?

I was thinking more about the wine/win overhead here. These games are very simple games that seem to be written to run on practically any hardware... 

> **leonardo_neo said:**
> 
P.S. All the softwares of edubuntu can be installed in Xubuntu.
Good point. Maybe I'll just go straight to edubuntu and get a RAM upgrade.

Thanks again for the advice!

---

### Post by rbc on 2009-03-26
This has nothing to do with hardware, and you may have found these already, but if not, have a look at GCompris and Childsplay. I believe they are on the second Edubuntu CD. If not, they are available from the repos. They are both full of educational/fun activities for someone that age

---

### Post by mb_webguy on 2009-03-26
> **sfl said:**
> [FONT="Tahoma"]I'm considering xubuntu for installation on my a 3yr old child's computer. The computer in question is an old Dell (1st gen P4 I believe) with 512mb of RAM that was just replaced for the parents. 

I was asked to set it up for surfing the web and playing games (the simple flash kind). A few questions come to mind:

1) Assuming the presence of drivers for the video card and the like, would 512mb of RAM be enough to run Firefox w/ flash on ubuntu or xubuntu? 

2) Would it be exaggerated to expect to run WINE on such hardware? Reason being that some of the games the parents already purchased are made for windows. I would bin them personally but apparently it's important to them that the child can play these.  

3) Samba. I'm assuming all flavours of ubuntu run it but then again I may be assuming too much. Would xubuntu handle this? 

P.S Alternately, would a system running a Intel Celeron 430 Conroe-L (1.8 ghz) be enough for ubuntu or would I have to go lighter (xubuntu or lighter)

Any input would be greatly appreciated. [/FONT]

If I were setting up this computer, I think I'd drop the desktop environment entirely.  A 3-year-old's computer should, IMO, be set up to do those things the 3-year-old wants to do as easily as possible.  Since a toddler isn't going to have a long list of uses for his computer, you can forgo a menu in favor of launchers on the desktop.  And if you don't need a fancy menu and sophisticated panels, you don't need a full desktop environment.

I'd start with Ubuntu, and install Openbox and PyPanel, as well as some age-appropriate apps like Tux Paint, GCompris and/or Childsplay.  I'd also install the Adblock Plus and ProCon Latte extensions in Firefox, and a kid-friendly theme.  I'd setup ProCon Latte to whitelist parent-approved websites, then use it to lock everything down with a password.  I'd use the Gnome Configuration Editor to hide the computer and (if desired) network icons from the desktop.  Then I'd create a launcher on the desktop for each application (and possibly each website) I wanted the toddler to be able to access.  

Finally, I'd configure Openbox.  I'd set it to use a single desktop, and simplify the menu (which the toddler likely won't be using anyway).   I'd add PyPanel, Nautilus (using the "--no-default-window" option to supply the desktop and launchers), and the network manager applet (assuming you want to access a network) to the autostart script.  Then I'd enable automatic or timed login, and set Openbox as the default session for the toddler's account.

The result of all of this is a simplified desktop environment suited for a child.  There are no menus for the child to deal with, as everything is available through colorful desktop icons.  There aren't multiple desktop workspaces to confuse and frustrate the child.  Between desktop launchers that open Firefox to a specific website and the whitelist of approved websites, access to the internet is kid-safe.  And since you're not running a full desktop environment, it's better suited for the older hardware.

---

