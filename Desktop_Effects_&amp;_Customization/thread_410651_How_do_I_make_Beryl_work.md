---
title: "How do I make Beryl work"
date: 2007-04-16
forum: Desktop Effects &amp; Customization
---

### Post by LostArt on 2007-04-16
Ok I just installed Beryl but I can't seem to  get it to work, when ever I change the window management to beryl it changes back to meticunous, or whatever the m one is sorry:confused:  anyway, I have no idea what I'm doing wrong and I'm starting to get frustrated and super annoyed.



Sorry for adding another Beryl question

---

### Post by amohanty on 2007-04-16
That means you are probably crashing beryl. What version of ubuntu are you using?

AM

---

### Post by LostArt on 2007-04-16
I'm running Ubuntu 6.1 which is edgy I believe, and I'm pretty sure that I'm running the correct ATI drivers, I might just uninstall everything I've already installed and try it with the terminal.

---

### Post by amohanty on 2007-04-16
Have you tried using the svn version instead of the release version??
AM

---

### Post by Gorthus on 2007-04-16
I had this same problem and just solved it...

What you want to do is log out, and change your session to XGL. This will probably work. If does, come back and I'll tell you how to get it back the way it was, because when you switch to XGL it will get rid of your theme.

---

### Post by LostArt on 2007-04-16
Ok so I switched to XGL and it made all of the toolbars disapear, and everything super slow, and beryl still didn't work, unless of course that was supposed to happen, which I kinda doubt, and I'l try installing the svn version later today

---

### Post by qamelian on 2007-04-16
Which ATI card do you have? Some of the require XGL and the FGRLX ATI drivers. Other like the one in my laptop only work right with AIGLX and the open source ATI/Radeon drivers.

---

### Post by LostArt on 2007-04-16
On my notebook I have an ATI mobility Radeon 9100 IGP, I believe, the mobility might not belong but I'm pretty sure it does and please don't tell me it's unsupported or I'm gonna be PISSED OFF. and yes that was capitilized. also how can a run something like a dx diag?

---

### Post by qamelian on 2007-04-16
> **LostArt said:**
> On my notebook I have an ATI mobility Radeon 9100 IGP, I believe, the mobility might not belong but I'm pretty sure it does and please don't tell me it's unsupported or I'm gonna be PISSED OFF. and yes that was capitilized. also how can a run something like a dx diag?

Okay, first off you do not need XGL to get Beryl working with this card. This means you also don not need the binary FGLRX drivers from ATI. If you are trying to use a recent FGLRX driver with this card you are SOL. ATI doesn't even support this card in Windows anymore.

The good news is that Beryl runs just fine on this card with the open source ATI driver from X.org that should have already been installed when you first installed Ubuntu. Also the version of X that is installed in Edgy and later will already have AIGLX. 

Technically, all you should have needed to do was install the necessary Beryl components, start beryl-manager, and select Beryl as your window manager from the Beryl Manager applet in the notification area. The only other step that might have been necessary would have been to logout and back in again or reboot/restart X.

---

### Post by LostArt on 2007-04-17
okay, so should i reinstall ubuntu, err how should if ix the driver I changed, thnks for the help

---

### Post by Gorthus on 2007-04-17
Yes, I'd also like to know this. Pretty much 15 people told me that I couldn't run beryl unless I was in XGL, so I'd like to know too. I try putting the thing to Beryl but it jumps back to metacity and eats my desktop.

Please, explain your knowledge. ;)

---

### Post by qamelian on 2007-04-17
> **LostArt said:**
> okay, so should i reinstall ubuntu, err how should if ix the driver I changed, thnks for the help

You shouldn't have to reinstall Ubuntu, I don't think. Depending on how much you've puttered around trying to make it work with XGL. Getting back to the original open source driver should be as simple as editing the driver line for your display in /etc/X11/xorg.conf to change fglrx back to either ati or radeon, and restarting the X server. Using the open source driver with both this card and the 9000 IGP, All I did to get beryl working was to install it, start beryl-manager and select beryl as my window manager. That's it. On feisty it's even easier. If you don't mind using Compiz instead of Beryl, all you need to do is tick a box in the Desktop Effects applet under System > Preferences!

---

### Post by qamelian on 2007-04-17
> **Gorthus said:**
> Yes, I'd also like to know this. Pretty much 15 people told me that I couldn't run beryl unless I was in XGL, so I'd like to know too. I try putting the thing to Beryl but it jumps back to metacity and eats my desktop.

Please, explain your knowledge. ;)

You just need to check the home pages for both XGL and AIGLX projects to find out which cards each support. I don't have the links right at hand as I'm just on my coffee break at work! My primary laptop has a 9000 IGP and my secondary hasa 9100 IGP. I was never able to get FGLRX working correctly on either, so that meant that XGL was out of the question. I discovered purely by accident who well Beryl performed on these cards with the open source drivers. My desktop on the other hand has an NVidia Geforce 5600FX graphics card and I absolutely have to install the Nvidia binary drivers and XGL to use Beryl or Compiz on it. This drive me bonkers because I prefer AIGLX to XGL.

---

### Post by LostArt on 2007-04-17
Well all things work out for the best I suppose, I ended up having to reinstall ubuntu anyways. So I'll just use the terminal and install the newest version of beryl later today, So this might sound dumb but what version of Beryl should I install?

---

### Post by qamelian on 2007-04-17
> **LostArt said:**
> Well all things work out for the best I suppose, I ended up having to reinstall ubuntu anyways. So I'll just use the terminal and install the newest version of beryl later today, So this might sound dumb but what version of Beryl should I install?

Currently, I just use the version in the Feisty repos, but since you're using edgy try the instructions here: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

Also, I'd suggest that you start off with just the basic beryl / emerald stuff first and make sure it works for you before you start adding in any of the extras or experimental stuff. Best part is that with AIGLX, you won't have to mess around with installing any additional ATI drivers.

---

### Post by LostArt on 2007-04-17
Ok so I've installed Beryl, (the right way this time) but when I ever I launch the beryl manager, the whole screen goes white and if click, my computer logs me out. Any ideas? 
EDIT
Now I've messed with it a bit and found that beryl crashes (goes to the white screen, and goes back to the login area) after I change from mentacity to beryl, or click on the red diamond.

---

### Post by qamelian on 2007-04-17
I've never had this problem, but I've seen reports on the forums of others running into it. You may need to search the Beryl forums for an answer. I'll search as well to see if I can find any of the posts I've seen that may contain a solution.

---

### Post by LostArt on 2007-04-17
All right, I've been looking a bit, but I have'nt seen many solutions, just people mentioning it. Looks like there's a quest ahead of me.

---

### Post by LostArt on 2007-04-18
Okay so I've heard that the wsod or white screen of death issue has been fixed in beryl 0.2.0 but the problem is, the only way I know of getting this file is through a tar.gz file, and I have no idea how to work those, so If someone could give me some help with how to use it I would be very thankful.

---

### Post by txhellkat138 on 2007-04-18
Try this howto 
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

the 0.2.0 version is in the repo&#347; listed on that page and you should just be abnle to apt-get all of what you need

---

### Post by LostArt on 2007-04-18
It still doesn't work, would it make things better if I upgraded to fiesty? If I do upgrade to fiesty how do I do it? And lastly am I spelling fiesty right?????

---

### Post by NPuter on 2007-04-22
"feisty":)

---

