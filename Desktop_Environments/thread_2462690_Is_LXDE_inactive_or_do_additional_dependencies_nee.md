---
title: "Is LXDE inactive or do additional dependencies need to be installed?"
date: 2021-05-25
forum: Desktop Environments
---

### Post by roler2 on 2021-05-25
Attempted to install LXDE via the Ubuntu 20.04 mini iso. Failed three times. Rebooted to a Black Screen with blinking cursor.

Is LXDE inactive or do additional dependencies need to be installed prior to reboot?

Thank you for any suggestions.

---

### Post by guiverc on 2021-05-25
LXDE should still work, but it's been upstream Debian packages since 18.10 as it's no longer maintained by Lubuntu (thus maybe different to 18.04 & prior releases as for installation).

I booted a recent QA-test install of 20.04 (*daily of what will become 20.04.3*), logged into text terminal (ctrl+alt+F4) and 

`apt-cache search lxde`

picked a package and

`sudo apt install lxde`

which included all *recommends*, and on switching back to the GUI (ctrl+alt+F1) can now login to LXDE on 20.04.   It (*LXDE*) looks good to me.

Note:  *I started with a desktop install of Lubuntu (as that was what was on the box already).  It's not a used system; the box is used for QA-test installs of more than just Lubuntu, but I'm heavily involved with Lubuntu so its commonly re-installed to it (until it was booted I didn't know if it contained  Ubuntu Desktop, Xubuntu, Kubuntu... or Lubuntu))*

---

### Post by roler2 on 2021-05-25
Thank you very much for your reply! I was attempting to install LXDE from the command line of the Ubuntu Netboot 20.04, rather than installing Lubuntu LXQT Desktop first and then installing LXDE. I am having difficulty configuring LXQT. The Lubuntu LXDE Desktop was perfect for me. So my goal was to install LXDE via the command line and then manually install the 18.04 lubuntu-artwork so as to mimic the Lubuntu 18.04 Desktop. Would it be possible to completely uninstall the Lubuntu LXQT Desktop after installing LXDE? Sudo apt install lxde utilizing the Ubunto 20.04 mini.iso got me a Black Screen with a blinking cursor upon reboot.

---

### Post by guiverc on 2021-05-26
Had the box I booted and the box had Ubuntu Desktop 20.04, Xubuntu 20.04, Kubuntu 20.04 instead of Lubuntu 20.04 (or the *impish* versions of the same) I'd have done my test using whatever was on that box.  That box was used only because it's here at my desk; and is used for QA-test installs (*and on occasion support*)

I don't believe Lubuntu is required (*in fact I'm convinced of that!*); however it maybe the prior Lubuntu install had some packages that **are** required.

LXDE cannot handle buttons (close/maximize/minimize etc) or the window dressing as a WM is expected to handle that and LXDE (like LXQt after it) is WM agnostic. 

[https://packages.ubuntu.com/focal/lxde](https://packages.ubuntu.com/focal/lxde)

Lubuntu with LXQt and back when it used LXDE relied on `openbox` for that purpose, however Debian upstream with LXDE use `xfwm4`.  I don't see any *dependency* requirement for a WM which was likely added by Lubuntu up to 18.04/*bionic* but isn't there any longer as it's now a pure upstream (Debian) package.  That wouldn't have impacted my *test* as using a Lubuntu base meant `openbox` was already present.

I'm using `openbox` as example here; it maybe the package you're missing & possibly even the only one, but there may also be others.

FYI: Other WMs can be used too; eg. I use `fluxbox` & more in QA-testing different issues... but Lubuntu for now is still happy with openbox, but use whatever you prefer.

---

### Post by roler2 on 2021-05-26
Prior to rebooting should I attempt to install openbox and uninstall xfwm4?

---

### Post by guiverc on 2021-05-26
If you have `xfwm4` already installed... I just use that. 

 As I said, LXDE is WM *agnostic* in that it doesn't care (**intentionally**).   Many LXQt *devs* (that were LXDE *devs*) aren't fans of LXDE; one of whom packages for Debian upstream which is why it uses `xfwm4`.

I'm assuming you installed the *recommends*, which you'll note I specifically mentioned I did (and looking at the package *dep* rules I provided earlier, I'd for sure want some of them).

---

### Post by roler2 on 2021-05-26
[COLOR=#000000]If you have `xfwm4` already installed... I just use that. 

[/COLOR]I am not able to verify anything because I am not able to boot to a Desktop.  Utilizing 20.04 mini ISO sudo apt install lxde upon reboot I get a Black Screen with a blinking cursor in the upper left hand corner.

---

### Post by guiverc on 2021-05-26
Switch to a text terminal and look from there.

In my first post on this thread, everything I did was at text terminal (as GUI wasn't required, and you wouldn't have a GUI on your install so I was using my last** QA-test *focal* install because it was handy and allowed me to confirm LXDE was still usable).  I only switched to GUI when I was ready to *test* what I'd installed (and it worked I reported).

 I tend to use Ctrl+Alt+F4 to switch to terminal as I find F4 easy to feel without looking (the far left F1 can sometimes be an ESC on some laptop keyboards thus I go for F4, but use whatever you prefer).

** *it's no longer my last QA-test install; my last now was Xubuntu 20.04.3*

---

### Post by ActionParsnip on 2021-05-26
Did you install and setup gdm ?

---

### Post by roler2 on 2021-05-26
I attempted to install both lightdm and openbox. . .still booted to a black screen with a flashing cursor. Could not Ctrl+Alt+F4. Text Terminal would not activate. I am not good at troubleshooting. LXDE was easy for me to configure. I could try installing gdm however I am not sure it would be compatible with LXDE.

---

### Post by ActionParsnip on 2021-05-27
Why would it not be compatible? I use it myself on my Pis to load LXDE... But its just a DM... Why is LightDM "more compatible" than gdm with LXDE?

---

### Post by ajgreeny on 2021-05-27
You will, I think, need to enable and start whatever display manager you have installed as well with ```
systemctl enable lightdm
```, or similar command or the dm will not be used, hence the black screen.

---

### Post by roler2 on 2021-05-28
Thank you for all of the advice! After LXDE install utilizing the mini.iso and prior to rebooting, which should I attempt first: 'systemctl enable lightdm' or 'systemctl enable gdm'? If I get a Black Screen after rebooting I will have to start the entire process all over again.

---

### Post by ajgreeny on 2021-05-28
> **roler2 said:**
> Thank you for all of the advice! After LXDE install utilizing the mini.iso and prior to rebooting, which should I attempt first: 'systemctl enable lightdm' or 'systemctl enable gdm'? If I get a Black Screen after rebooting I will have to start the entire process all over again.

Whichever display manager (login screen) you wish to use.

As you will posibly now have more than one dm you will also need to choose that using command ***sudo dpkg-reconfigure gdm3*** which should give uyou the choice of which one to use.

I have not done any of this for many years so I hope my memory is not playing tricks on me.
Good luck!

---

### Post by roler2 on 2021-07-10
LXDE boots to Desktop utilizing the 18.04 mini.iso. I cannot get LXDE to boot to the Desktop utilizing the 20.04 mini.iso. It fully downloads, just doesn't boot to Desktop. Still booted to a black screen with a flashing cursor. Maybe it is not compatible with the configuration of the 20.04 mini.iso?

---

### Post by guiverc on 2021-07-10
> **roler2 said:**
> Maybe it is not compatible with the configuration of the 20.04 mini.iso?

The *mini.iso* is not an *official* ISO that is fully supported; it was a *side effect* of procedures of other *supported* tools and was made available as many users found it useful. Ubuntu 20.04 LTS was the *last* release where that procedure was used, thus the last release providing that specific *netboot/mini *ISO.

The ISO itself just  boots and installs packages from the web, there is nothing unique about it. 

I'd bet there is something (a package) you didn't install that creates the difference and your issue.  It may not be the package itself, but something done by the *post-install* script run on installation of a package.

In a prior comment i tested it with a Lubuntu base install.. I'd likely setup a VM (or *test box* like I used) and install it there like I did, then if it works there, compare the differences in *packages* installed between what worked, and what you have, and look for clues in that.

Yes LXDE will be different in *focal* to *bionic*, as the Lubuntu team adjusted packages from upstream in *bionic* but not in later releases; I'd already stated that.

 I doubt my prior test which started with Lubuntu would have been different had I used a different base (eg. Xubuntu, Kubuntu, Ubuntu etc) but I would have performed the test on whatever was there which happened to be Lubuntu. Maybe I'm wrong though; and the Lubuntu base caused a change that the Lubuntu team made in *bionic* that is no longer there.  To prove that I'd likely perform the test again on a different install (*last test was with Ubuntu on that box; but it was impish and not focal*), but either way I'd find somewhere it worked; and compare packages with your existing non-working system..  then cross of the packages that won't be involved and you'll be left with possibly only 1 or 2 possibles and I bet your answer.

---

### Post by roler2 on 2021-07-11
Thank you so much for all of the advice. I am closing this thread because I am not sure what I am doing wrong. . .if anything. I will just wait until Lubuntu 22.04 and try LXQT again. I was having a lot of difficulty configuring LXQT yet I will try again. I am just used to GTK and it is easy for me to utilize. I feel the 20.04 mini.iso may be configured differently than the 18.04, and that equally may be conflicting with a straight LXDE install from the command line. Might be best to try the Debian 10 or 11 minimal install, then add LXDE and then the Ubuntu Repositories, or install Ubuntu-core with the 20.04 mini so at least you get a Desktop and then install LXDE. However, for me, overall, it really isn't worth it. I will just wait until 22.04 and try LXQT once again. Thank you again for all of the advice.

Also I don't really understand ESM. Does that just involve specifically updating the kernel for 5 more years? I should have asked that in my other thread about ESM.

---

