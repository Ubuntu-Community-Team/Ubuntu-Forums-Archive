---
title: "Revenrting Netboox remix to a normal desktop"
date: 2009-04-25
forum: Desktop Environments
---

### Post by BetterSense on 2009-04-25
I have hardy now, with a customized desktop. If I install UNR, keeping my current home directory, will I be able to keep my current desktop?

I wanted to try out Jaunty on my Aspire one, so I used the netbook remix USB image because it saved me the trouble of making an bootable stick out of a CD image. Plus, it has good power saving and stuff. I booted the disk to check it out but I liked my Gnome layout and fonts and panels and everything from my normal Hardy install. Is there a simple way to revert it from the strange netbook remix desktop to a normal gnome? 

Since all my configs should be in my home directory, once I do an actual install will my desktop look like it did under Hardy, or will netbook remix nuke them and install its own desktop config or something? I don't know if the live USB pulls configs from my current home directory but I doubt it.

---

### Post by pauna on 2009-04-25
There is a "Switch Desktop Mode" menu item in System -> Preferences. You can use it to choose the classic view instead of UNR view.

I used that yesterday when I did a complete reinstall of my EEE PC 901 using Jaunty UNR.

However, the switch is somewhat buggy. For example, it will not get rid of a background program called "maximus", which will keep on maximizing all opened windows. You can remove it from the session startup (System -> Preferences -> Startup applications), but for me it did not help. You can not even kill it, it just keeps on restarting.

The only way of managing maximus seems to be either remove the whole package (which also removes ubuntu-netbook-remix) or use gconf-editor, navigate to apps/maximus and check the box "no_maximize". I did that, but still get weird window behaviour.

---

### Post by BetterSense on 2009-04-25
Thank you for your input. 

Note that I won't be doing a blank install, but remounting my current home directory, which should contain all my current Gnome settings. If I do a *normal* ubuntu install, my desktop should stay just the way it is. I know this because I have done installs this way before, and the desktop settings are always retained from the old install.

Netbook remix might do this too, or it might do its own weirdness despite my current desktop configs. LiveUSB's don't look at your home directory for configs, after all. If I run a liveCD on any computer, the desktop always looks like whatever the live CD's default is.

I would expect Netbook Remix, once properly installed to the hard drive, to look at my mounted home directory and give me a desktop just like the one I have now, instead of the weird netbooky one. But I'm not about to assume that! I have extensive customizations for optimizing screen space, and fonts, including a list of maximus exceptions (I added maximus to my current install).


I could just use a normal Jaunty CD after all, but I understand that there is better power management, maybe better drivers, and less bloat on the Netbook Remix version, plus it already comes in USB form. I want UNR, I just want my desktop to stay the way it is.

---

### Post by Dr_Willis on 2009-04-25
I just had to delete maximus from the 'System -> Preferances -> Startup applications' listing and logged out/back in. and it dident 'restart' after that. I did not have to remove the maximus package.

This could be a annoying bug. or a nice feauture depending on if you love or hate maximus. :)

---

### Post by BetterSense on 2009-04-26
Bump, still scared to install UNR, not knowing if it will behave like a normal distro regarding stored desktop settings.

What do I need to do to resize my current home directory and create another bootable partition? It was not clear from the partitioner on the USB image what I needed to do in order to do this.

---

### Post by nightalon on 2009-04-26
I also have had this issue on multiple laptops...is there a bug posted?

It seems that the "Desktop Switcher" should shut down Maximus when reverting to a normal Ubuntu desktop, but oddly it does not.  WTF.

---

### Post by BetterSense on 2009-04-26
This thread isn't really about maximus or desktop switcher for that matter. It's about the behavior of UNR when it is installed on a system that has a home directory mounted on it, that has current settings in it. Bottom line, does it respect those settings, or does it do its own thing?

---

### Post by BetterSense on 2009-04-27
Well just in case anyone else is wondering, UNR is a complete nazi and will sabotage your system.

I played it safe by creating a new partition and installing UNR there. However the first time I booted it, it not only booted to the netbook desktop mode instead of my old desktop mode as dictated by my settings in /home, it also completely hosed my desktop settings for my other, old install. There is no reason this should happen and it angers me.

---

### Post by snowpine on 2009-04-27
> **BetterSense said:**
> 
I wanted to try out Jaunty on my Aspire one, so I used the netbook remix USB image because it saved me the trouble of making an bootable stick out of a CD image. 

You created a lot of problems for yourself down the line by "saving yourself the trouble" at the start. Use Ubuntu's "create a usb startup disk" feature (or the 3rd party unetbootin application) to copy a CD image to the USB stick. 

There is no reason to install Ubuntu NBR if you don't want the NBR interface. You should have used "regular" Ubuntu if you want the classic Gnome desktop.

---

### Post by BetterSense on 2009-04-27
Point taken, but it's my understanding that there are other differences. For example, it boots way faster than Hardy did. Possibly regular jaunty would too, but Canonical claims that 

> All of the initial Ubuntu Netbook remixes combine optimisations from the Moblin project for Intel® Atom&#8482; processors and it is specially designed for netbooks

They also state that takes up less hard drive space. 

Besides, there is no reason that it should screw up your desktop settings. If I installed regular Jaunty onto an existing home partition, it wouldn't have rearranged my desktop to look like the default Jaunty desktop. There's no reason for UNR to either. At the very least, if it insists on forcing its default desktop despite existing user settings, at least it should create a .unr directory or something and leave my existing settings alone so that other distributions installed on the computer wouldn't be borked. That's just plain not nice.

---

### Post by Dr_Willis on 2009-04-29
Im using the netbook remix on my AAO. told it to use the 'normal' desktop, and other then disabling maximus by hand. I cant really  recall any issues ive had with it. 

Perhaps time to get a list going of all known 'issues' caused by doing the switching.

---

