---
title: "Missing dependencies? What have I removed by accident?"
date: 2014-09-17
forum: Desktop Environments
---

### Post by Mike_Walsh on 2014-09-17
Afternoon, all.

Got an interesting little problem here (self-inflicted, of course!); need a bit of advice from somebody more experienced in these matters.

I decided, yesterday, to remove all my extra distros (Lubuntu, Kubuntu, Xubuntu, and Mint 17), and return to dual booting only with Ubuntu 14.04 and Zorin's OS Core 9. It was using a good chunk of my monthly data allowance up, simply keeping all six distros updated..! So...

I thought I'd install the Xfce desktop alongside Unity, as I've always liked Xubuntu's appearance. Following the instructions from this page, I proceeded to install Xfce:-

[https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative)

This shows what a noob I still am.....and also that I don't always read things as carefully as I should..! I actually ended up [COLOR=#ff0000]REPLACING[/COLOR] Unity with the Xubuntu Xfce desktop; not what I intended at all. So, following advice given on THIS page, I had a go at re-installing Unity:-

[http://askubuntu.com/questions/462914/how-to-reinstall-unity-desktop-on-ubuntu-14-04](http://askubuntu.com/questions/462914/how-to-reinstall-unity-desktop-on-ubuntu-14-04)

Using the advice halfway down the page, I re-installed Unity (holding my breath!)

```
 [FONT=Ubuntu Mono]sudo apt-get update
[/FONT] sudo apt-get install ubuntu-desktop
```

and [COLOR=#ff0000]BINGO! [/COLOR]everything's working as before....with ONE small exception.

I had an update notification come through while I was working in Unity this morning (the icon on the launcher came up, pulsing as it should), so I clicked on it, expecting the Updates window to appear; but nothing happened. I discovered that by right-clicking the icon, and then clicking on 'Install all updates', that the little progress bar on the icon itself filled in, and from my CPU load indicator (Psensor), I could tell it had definitely finished.....but I also got no window telling me the software was up-to-date. I'm only guessing that it is, at this stage.

I'm also guessing that I've inadvertently removed some dependencies when I was installing the Xfce desktop, as there was also a large list of items to enter through the terminal to remove any conflicts with Unity, vis-a-vis:-

```
[COLOR=#0000FF][FONT=Arial]sudo apt-get remove nautilus gnome-power-manager gnome-screensaver gnome-termina* gnome-pane*
 gnome-applet* gnome-bluetooth gnome-desktop* gnome-sessio* gnome-user* gnome-shell-common compiz 
compiz* unity unity* hud zeitgeist zeitgeist* python-zeitgeist libzeitgeist* activity-log-manager-common gnome-
control-center gnome-screenshot overlay-scrollba* && sudo apt-get install xubuntu-community-wallpapers && sudo 
apt-get autoremove[/FONT][/COLOR]
```

Since I'm not yet experienced enough to recognise most of these things off the top of my head, can anybody tell me which of these needs to be re-installed to make the Software Update window work again, as it should? What have I accidentally removed that shouldn't have been? :confused:

Any advice would be very much appreciated; hopefully, I shall learn another piece of the Linux puzzle out of this!

Regards,

Mike.

---

### Post by TheFu on 2014-09-17
You can install as many GUIs as you want on to the same system. Just use a different account for each so the settings don't get screwed.

I haven't used the GUI to handle packages or updates in years. For me, it doesn't provide enough feedback, like the shell output does.

So ... run:
**sudo aptitude update  && sudo aptitude dist-upgrade**
and post any warnings or errors. DO NOT POST THE ENTIRE OUTPUT, just the relevant stuff.

---

### Post by Mike_Walsh on 2014-09-17
Hallo there; thanks for taking an interest in this.

I ran your suggestion, and this was the result:-


```
paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ sudo aptitude update && sudo aptitude dist-upgrade
[sudo] password for paul: 
sudo: aptitude: command not found
paul@paul-EK335AA-ABU-SR1619UK-GB540:~$
```

Something else I've removed without meaning to?:rolleyes:

Regards,

Mike.

---

### Post by vasa1 on 2014-09-17
AFAIK, aptitude isn't installed by default on any Ubuntu flavor. If you want to use it, you'll need to install it first.

---

### Post by Mike_Walsh on 2014-09-17
Hi, Vasa.

What exactly IS 'aptitude', and what does it do?

Regards,

Mike.

---

### Post by TheFu on 2014-09-17
Got on my systems somehow - though I don't recall installing it, perhaps I type in my sleep? ;)

**sudo apt-get install aptitude**
[B]
man aptitude[/B]  will explain what it is, does and while it is useful.

Aptitude is smarter than any of the other APT tools about dependencies. THAT is why I used it. It is similar to apt-get, so you can use that, but it is a good habit to get into s/apt-get/aptitude/ for almost everything.  It also will clean up old packages automatically - which can be nice, especially on /boot partitions.  Aptitude is not perfect and most of the time apt-get provides the same results.

I have to ask - when you saw that error - did you copy/paste it into google and search before posting here?

---

### Post by matt_symes on 2014-09-17
Hi

As well as TheFu's suggestion, I would also consider running apt-get with fix-missing. My first attempt would be a dry run to see what is missing and to see what it would reinstall.

```
sudo apt-get install --fix-missing --dry-run
```

If your happy with what it would reinstall the run then command without the dry run switch.

```
sudo apt-get install --fix-missing
```

This does, of course, assume that missing packages are the cause of your problems and that apt can identify them.

To see what aptd does not like you may want to run 

```
sudo apt-get update && sudo apt-get upgrade
```

This should identify any issues with apt.

Kind regards

---

### Post by Mike_Walsh on 2014-09-17
Thanks for the suggestions, guys. I'll have a look at what's what, and if I can figure out what's gone on, I'll get back to you.

@TheFu; I'll be honest, no.....I didn't Google it first. I've always managed to find reams of good advice on here, from people who have considerably more experience with Linux than me, and who invariably manage to help me solve things..! ;)

Cheers.

Regards,

Mike.

---

### Post by slickymaster on 2014-09-17
Aptitude is a menu-driven, text-based front-end to the Advanced Packaging Tool (APT) system. Many of the common package management functions, such as installation, removal, and upgrade, are performed in Aptitude with single-key commands, which are typically lowercase letters.

It's best suited for use in a non-graphical terminal environment to ensure proper functioning of the command keys.

---

### Post by Mike_Walsh on 2014-09-17
Hi again, guys.

Right. I installed aptitude:-

```
sudo apt-get install aptitude
```

After running:-

```
**sudo aptitude update && sudo aptitude dist-upgrade**
```

The results were as follows:-

```
The following packages will be upgraded: 
  python3-distupgrade ubuntu-release-upgrader-core 
  ubuntu-release-upgrader-gtk 
3 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 136 kB of archives. After unpacking 0 B will be used.
Do you want to continue? [Y/n/?]

```

I entered Yes, and allowed the system to do its thing. After that process had terminated, I clicked on the Software Updater icon, and [COLOR=#ff0000]BINGO! [/COLOR][COLOR=#000000]The window appeared (as it should), and I was able to follow the process through to conclusion, when it told me the 'software on this system is up to date.'

So; thanks for the info, and the help, guys. Obviously, I uninstalled something essential when I was performing the 'clean-up' after the Xfce install (before I realised I'd gotten rid of Unity); I'm guessing it was probably the gtk stuff. Problem apparently sorted; many thanks!

@TheFu; I'll have to remember that one. That's a pretty useful command for finding out what's missing. Thanks.

@slickymaster; Thanks for a nice, clear explanation! Appreciated.

I'll mark this as solved. Thanks, everybody; another 'piece of the Linux puzzle' I've learnt today.


Regards,

Mike.


[/COLOR]

---

### Post by TheFu on 2014-09-17
Glad it was solved.  **Aptitude completely rocks.**  Too bad it isn't pushed more often, since it can solve many more dependency issues that apt-get, synaptic or software center does.  It was strongly recommended by the Debian team for a few years, but they've given up and let folks use apt-get.

For lurkers, here's more info on aptitude: [https://wiki.debian.org/Aptitude](https://wiki.debian.org/Aptitude)
In general, it is safe to swap aptitude where apt-get might be used. I've seen it solved dependency issues that made apt-get barf and die.

BTW - a data backup is good, but having a system that can be restored is better. ;)

---

### Post by Mike_Walsh on 2014-09-17
THAT'S for sure..!

Aptitude's a nifty bit of kit; I shan't be forgetting it in future. 

Cheers, Fu!


Regards, 

Mike .

BTW; I only changed the signature last night! I'm having an avatar crisis at the moment... :p

---

### Post by TheFu on 2014-09-17
> **Mike_Walsh said:**
> BTW; I only changed the signature last night! I'm having an avatar crisis at the moment... :p

In another thread, I've been helping someone who backed up their data, but none of the ownership, groups, permissions, or ACLs.  They aren't really happy even with the data restored.

Proper backups would have made the restore trivial.

---

### Post by Mike_Walsh on 2014-09-17
Well; what I do amounts to a 'double-check' in a way. I keep regular backups of all important and personal data (documents, photos, videos, internet links, etc....including browser bookmark backups) to my external HDD. PLUS, I do regular system backups via the Control Panel 'Backups'.....so all the permissions, ownerships, etc, are covered as well. Only makes sense, I feel..... 

Anyway, I'm happy now I've got that little 'hiccup' sorted out. I now have the benefits of TWO different DEs, with only the one set of updates required for the whole lot. There might be a FEW Xubuntu-specific ones in there, but not many; because when it comes down to it, the two OSs are VERY similar 'under the hood'.

Once again, many thanks for your help.....much appreciated. Linux might be a steep learning curve for some, but in my case, I've spent 30-odd years playing around with all sorts of OSs, so.....I'm used to the 'different', as opposed to necessarily 'better', and I've found the transition, on the whole, to be remarkably smooth. I **LIKE**&#8203; it! (And it's so much more versatile than a certain Redmond-based outfit's offerings...)

BTW, I hear they're only JUST now talking about providing multiple workspaces in Windows 9, when it comes out; to my way of thinking, it's one of the best features of Linux in general. No more of that constant minimising/maximising to the taskbar!

Regards,

Mike.

---

