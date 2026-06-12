---
title: "My desktop has changed dramatically."
date: 2012-02-07
forum: Desktop Environments
---

### Post by Blasted Remnants on 2012-02-07
Hi guys, I'm new to Ubuntu so I apologize ahead of time if I sound a bit foolish. Anyway, a few days ago I got fed up with Windows and decided to give Linux a go. After a bit of looking around I chose Xubuntu 11.10 and installed it.

   Everything except the wifi worked right off the bat with Xubuntu, so once I got my wireless figured out I moved on to Wine and tried to get some games working. I ran into some trouble with a particular game that needed extra setting up (World of Tanks and I give up for now), and after mucking about with Synaptic and a random looking (to me) mess of Terminal commands, I broke my sound and totally messed up my desktop. Since then I've managed to get the sound working again (well mostly, but I'm not getting into that now), but my desktop is still messed up.

   I installed and uninstalled a few different things like "Gnome" and "Unity" because I got the impression that I needed them for other things, but now I'm thinking that I should've NOT been fooling around with those types of things, or not just yet anyway. My desktop has changed in that it no longer has any icons, and even my right-click menu has changed when I click the desktop. On top of that, my loading screen changed too. The very first screen after my BIOS info flashes by, with the boot up options, now says "Debian" and has an ancient looking graphic of the Earth and some stars. And if all that wasn't enough, I've got a bunch of extra applications now that I've never heard of and have no interest in.

   I'm wondering if there's any easy way to restore my desktop and boot screens, and if possible automatically remove anything that those other desktops might have brought with them. Sorry for the vague info, I've done a lot of things to my system the last few days and I've pretty much lost track of it all. I'd be perfectly happy to provide better details if someone can tell me where to find anything, I'm fresh out of Windows and having a hard time making the transition. Thanks!:D

---

### Post by typhoon_tip on 2012-02-07
Judging from the level of mess and what you are reporting, I think a fresh re-installation (format and reinstall) is necessary.

Pay attention when they ask you to run command to install things: some components may look like "libraries", but they may be entire Desktop environments. A fair, newbie way of understanding is: when running an "apt-get install" command, it always tell you the total number of bytes you are about to throw at your PC. Ubuntu installs are very small usually. A "big" program is 5~6 MB. An entire Desktop (gnome-shell) may be over 100 MB. Wine framework is big too. When installing components, you should never exceed a few MB, and if it does, have a look at the dependencies required: you may be installing more than you are needing.

Coming from Windows, is normal to be misled by the sizes of installs. Usually packages are 1/10 the size you may expect in Windows.

---

### Post by Blasted Remnants on 2012-02-07
Thanks Typhoon, I'm just a few days in so starting over from scratch wouldn't be TOO big of a deal at this point. Would it be a bad idea to try and save anything from my current install? I added a few games that I'd rather not have to redownload, although of course I have no idea where to find them on my drive haha. How about Xubuntu itself, is it a fairly decent build for beginners? If I'm reinstalling anyway then I might as well take another look at my OS options while I'm at it. I mostly chose Xubuntu because it seemed like it'd be an easy one, but if you know a better one I'd probably try it out. Thanks!

---

### Post by typhoon_tip on 2012-02-07
Saving your wine installs is easier than you think, try this method:

1) Open a Explorer window and go to the home folder
2) Press CTRL+H or use the menu to "show hidden files"
3) Backup the entire .wine folder (may be big)

After reinstalling the system, simply do the following:

1) Install Wine
2) Restore your .wine folder "before" opening any wine application (it is created only after anything is opened)
3) Should work right away, perhaps you will miss the menu entries, but you can manually create them again

---

### Post by typhoon_tip on 2012-02-07
> **Blasted Remnants said:**
> How about Xubuntu itself, is it a fairly decent build for beginners? If I'm reinstalling anyway then I might as well take another look at my OS options while I'm at it. I mostly chose Xubuntu because it seemed like it'd be an easy one, but if you know a better one I'd probably try it out. Thanks!

Perfect choice. ;)

If you are looking for fancy graphic, and your hardware is good enough (at least 2G of RAM) you may want to try the official Ubuntu 11.10 with Unity/Gnome.

---

### Post by jayshomebrew on 2012-02-07
check out [playonlinux]("http://www.playonlinux.com") for setting up games.

I also suggest using [virtualbox]("https://www.virtualbox.org/") to play with virtual machines (VM). That way you can keep your main system safe and test with the VM. Once you get it working in the VM, you can then install only what you need in your main system.

---

### Post by pbpersson on 2012-02-07
Xubuntu uses the XFCE desktop system.  Gnome and Unity are also desktop systems.  KDE is another one.  If you installed Gnome and Unity on top of XFCE then I am not surprised you have a confused system.  You sound like a wild computer user.  ;)

Maybe you need to slow down, you sound like me.  :)

---

### Post by Blasted Remnants on 2012-02-07
> **typhoon_tip said:**
> Saving your wine installs is easier than you think...

Thanks again Typhoon, but wouldn't there be a chance that something in my Wine is messed up and I'd be backing up a faulty insallation? I don't mind redownloading that stuff, I just wanted to skip getting Alien Arena and those sorts of games again.  :D

---

### Post by Blasted Remnants on 2012-02-07
> **jayshomebrew said:**
> check out [playonlinux]("http://www.playonlinux.com") for setting up games.

I also suggest using [virtualbox]("https://www.virtualbox.org/") to play with virtual machines (VM). That way you can keep your main system safe and test with the VM. Once you get it working in the VM, you can then install only what you need in your main system.

Hi Jay, thanks for the advice. Before I completely scrambled my system I had tried PlayOnLinux, but it kept telling me that 3D acceleration had to be enabled, although it was. Or, I think it was anyway, I installed the Nvidia driver for my card anyway. I had also tried to install Oracle Virtual Box, but couldn't get it to install. Something about it not letting me use the .deb for some reason, if I remember correctly. I plan to try it again after I reinstall my system tomorrow.

---

### Post by Blasted Remnants on 2012-02-07
> **pbpersson said:**
> Xubuntu uses the XFCE desktop system.  Gnome and Unity are also desktop systems.  KDE is another one.  If you installed Gnome and Unity on top of XFCE then I am not surprised you have a confused system.  You sound like a wild computer user.  ;)

Maybe you need to slow down, you sound like me.  :)

Haha yeah, I ran into a problem that mentioned Gnome and I went straight to Synaptic and downloaded everything Gnome related that I could find. Didn't bother rebooting, but I did find something saying that my problem was related to Unity somehow, so back to Synaptic for everything Unity related. Uhoh, something about ALSA and Pulse, back to Synaptic. Finally did a reboot and wouldn't you know it, my system was thouroughly thrashed haha. Ah well, at least now I know that "desktop environments" are not to be messed with for now. Thanks, I'll be a BIT more cautious after tomorrow's reinstall, lol.  :D

---

### Post by exodus_ on 2012-02-07
Hey blasted Remnants,

First i would like to clear up that Ubuntu itself was derived from Debian GNU/Linux.  Ubuntu and its derivatives still share a lot of the same principles and features too.  Obviously you must have installed something a little obscure if you are seeing a debian logo on Ubuntu though.

Also, it is perfectly OK to have multiple window managers or even desktop environments installed on one system!  In fact, several years ago I shared an apartment and my computer with a friend of mine.  Back then I prefered the simplicity of XFCE, but he felt more comfortable in KDE so I had both installed.  You can select what to operate in while logging in.  The only real downside I can see to having multiple desktop environments or window managers installed is the extra disk space used.  This is much less of an issue on somewhat-modern systems with lots of disk.

It seems like you did not keep a perfect log of every change you made to your system, so perhaps a clean install would not really HURT anything, even if it is not really needed.  Unfortunately unless we knew EXACTLY every step you have taken until now there is no real "easy" way to go about "fixing" it.  Have a look on the search options, just put a few keywords in about your problem and maybe you could find something, I wish you luck!

Also, I agree with the virtualbox statement!  Once you reinstall I would get virtualbox on there right away, and use a virtual machine for the experiments, and once you "know" what you are doing, THEN do it on your regular install.  

I would also like to point out that [http://help.ubuntu.com](http://help.ubuntu.com) is an excellent resource, and has lots of high-quality community documentation that has helped me on more than one occasion!

Welcome to the Linux world, it's really lots of fun when you realise all the interesting things you can do with your computer!

---

### Post by Blasted Remnants on 2012-02-08
Thanks Exodus, I definitely installed some obscure stuff buddy! Pretty much everything in Synaptic that even mentioned any of the words alsa, pulse, gnome, unity, or a few others got installed and reinstalled many times over the last few days, lol. I guess I was hoping for some Linux equivalent of the restore points that Windows uses. Not that I've ever had any success in the past with those either, but you never know, right? Anyway, I definitely plan on figuring out the VMs next time around. It was just impatience that led me to Wine, and my "troubleshooting" of Wine that led my system into "The Pit of Nonfunctionality". Thanks again, see ya around bud!

---

### Post by exodus_ on 2012-02-08
It is my pleasure Blasted!

Did you like Xubuntu?  XFCE is a lovely desktop environment, and served me well for a very long time.  XFCE may not be as polished as say, GNOME, but i have found the latter to become too "big" and "flashy" for my taste, and XFCE seems to be forward-thinking enough but still retaining aspects I like.

VirtualBox is an amazing program that I have NO idea how I lived without before it's creation!  It's very easy to use, and depnding on the host hardware can work at nearly "native" speeds!  Way back when I remember being quite amused to see my friend open up VMWare on his machine and have windows XP run insise a "window"!

Wine is a lovely project!  Having Wine installed alone will not break your system.  Some would even argue that Wine could be better for gaming than running on virtual hardware.

Also, I have had MUCH better success with regular backups to storage NOT on the computer I am backing up.  I always shut off those silly restore points because they just take up disk needlessly.  

Always happy to help :)

---

### Post by Blasted Remnants on 2012-02-08
> **exodus_ said:**
> Did you like Xubuntu?

I love it actually, my only complaint so far has been trying to find something akin to the Control Panel and Device Manager. I'm thinking that this is more of a Linux difference, and not specific to Xubuntu. Not a big deal, I just need to get used to finding things within my new OS. And that of course is half the fun, right? :p

> **exodus_ said:**
> VirtualBox is an amazing program...

I completely agree, I used it in Windows to test many different things in the past, but I was unable to get it working the other day. I did get some good tips on installing it for next time though.

> **exodus_ said:**
> Having Wine installed alone will not break your system.

No, I'm sure Wine is perfectly fine in most situations. But I was adding patches and compiling source code and doing all sorts of crazy things to mine, lol. I botched the instructions on a half dozen sites for how to compile a custom wine build to run a particularly fussy game. Oops! I think I'll stay away from that stuff for now, lol.

> **exodus_ said:**
> I have had MUCH better success with regular backups to storage NOT on the computer I am backing up.

Absolutely agreed, same here. I've got two 160 gig internal drives, one of which is empty for now, and I've got an external drive with a terabyte. Sorry for the lengthy reply, just wanted to let you know that I'm reading these and paying attention lol. Thanks again, I appreciate the help!  :p

---

### Post by exodus_ on 2012-02-08
ROFL!  I have not compiled very many things from source since my slackware days!

apt-get has made me VERY lazy!

---

### Post by Blasted Remnants on 2012-02-08
Yeah, I needed to integrate a fanmade patch, and the instructions I found had been translated from Russian. I probably should've known how THAT was going to turn out without needing to actually experience it, lol. Ah well, lesson learned :)

On a side note, I LOVE all these little "apt-get this", "sudo that" commands and whatnot. Kinda reminds me of DOS, but with more "umph".

---

### Post by exodus_ on 2012-02-08
> **Blasted Remnants said:**
> 

On a side note, I LOVE all these little "apt-get this", "sudo that" commands and whatnot. Kinda reminds me of DOS, but with more "umph".

DOS was only ever meant for use on so called "single-user" computers.  UNIX came first on big huge multiuser systems that would have lots of clients connected to it at once!

The terminal is often the fastest and easiest way to do some things, so it will probably always exist :)

---

### Post by LinuXofArabiA on 2012-02-08
Hello. Before doing a fresh install all over again (I dont agree with that synopsis, anyone can say do a fresh install) I would suggest resetting your Unity desktop settings. use the following code in terminal:

unity --reset.

Hope that will fix things. Note that you will have wait for a 2-3 minutes. If nothing happens then ctrl+c should terminate.

Good luck!

---

### Post by Blasted Remnants on 2012-02-08
It's cool, I love being able to just type in a command rather than having to open up my shortcuts folder, start my app, and close my folder out. And the apt-get thing, wow! Pure genius that is.

---

### Post by Blasted Remnants on 2012-02-08
> **LinuXofArabiA said:**
> Hello. Before doing a fresh install all over again (I dont agree with that synopsis, anyone can say do a fresh install) I would suggest resetting your Unity desktop settings. use the following code in terminal:

unity --reset.

Hope that will fix things. Note that you will have wait for a 2-3 minutes. If nothing happens then ctrl+c should terminate.

Good luck!

Hi L of A, sorry if my message wasn't clear enough (I know, I've got a big mess) but Unity was something that I acidentally installed, and it and Gnome are now giving me problems with my regular desktop, the XFCE or whatever the Xubuntu default is called. Sorry about the confusion, and thanks anyway! :D

[EDIT] Actually, would there be a similar command for XFCE?

---

### Post by exodus_ on 2012-02-08
This person does not want to use unity!  They have said they loved Xubuntu and wish to return to a "stock" Xubuntu install or repair said install.  The advice given of reinstall is valid, but it is up to the user to decide what to do.

The original experience the poster had never had, nor ever would have Unity, it would be XFCE.

---

### Post by Blasted Remnants on 2012-02-08
Hi again everyone, thanks for all the help! Just wanted to mention that I've got Xubuntu reinstalled, with Wine and Virtual Box as well. So far everything is good, except that my PlayOnLinux seems to be stuck on downloading updates. It's been at it for 45 minutes so I'm thinking that it's failed somehow. I couldn't get it to work before either, but my Wine and Q4Wine both seem alright. Thanks again guys, I appreciate the help!  :D

---

### Post by exodus_ on 2012-02-08
Glad to hear all has worked out well for you :)

---

### Post by deonis on 2012-02-08
+ 1 for virtual box

---

