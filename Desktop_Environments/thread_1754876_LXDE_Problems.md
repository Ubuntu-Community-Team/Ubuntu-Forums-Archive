---
title: "LXDE Problems"
date: 2011-05-10
forum: Desktop Environments
---

### Post by gdonwallace on 2011-05-10
So I installed Ubuntu and tried to use Unity for a week or so, and just couldn't do it.  Decided to try LXDE and see if it will work for me; and so far it is.  However; I have a very odd problem.

I came in this morning and started working around 8, at 1 this afternoon, I noticed my machine was running really...really...slow.  I clicked on the panel at the bottom to bring up my terminal so I could run TOP and see what was happening.  When I clicked, nothing happened.  I tried clicking on everything on the panel, including the shutdown button...nothing.  

I alt+tab'd to get to the terminal and TOP was showing the process lxpanel running at 100% or more CPU (Dual core CPU).  

The only way to get the panel back was a reboot.  Has anyone else had this problem, and what have they done to fix it.  

Other than the cpu monitor running in the lower left, I have a weather applet, network connection indicator.  Everything is pretty vanilla as this is my work machine.

lxde.org is down (? odd ?) just get a white screen when I hit the site.

---

### Post by ajgreeny on 2011-05-10
I've been using Lubuntu 10.10 for a month or two on my old Acer Travelmate laptop, celeron 2.3GHz cpu, 512 MB ram, and it really flies on that.  I have never seen any similar problem on my machine, though the LXDE desktop is not very vanilla style, like yours, as I have customised it a fair bit adding some startup applications (xfce4-power-manager), and removing others such as gnome-power-manager, which simply does not work in LXDE.

Did you add the lxde package to your 11.04 install, or lubuntu-desktop, or is yours also a reinstall of Lubuntu 11.04?  Perhaps there is some problem of incompatibilities between the two systems when you put lxde on top of unity/11.04.

Keep trying; I think lxde is going to get a lot of users, with unity being so very different and disliked by such a large number of users.  Lxde and xfce will be the winners, I think.

PS:  I also get a white empty screen at lxde.org.  Very odd!

---

### Post by gdonwallace on 2011-05-11
I installed the packages for lxde from Synaptic.  So Unity is still there.

I didn't get any warnings during the install of packages being removed, although I think a couple where updated; but that was for LXDE, if that where the issue then it could effect some other programs I have.  

Not really sure, may have to run a check on my system to make sure no dependencies broke with the install.

---

### Post by gdonwallace on 2011-05-11
Checked missing depends and it does not seem to be an issue.  Just can't figure what would be causing this.  I am running XFCE on my laptop, so I may install that (or Xubuntu Desktop) and see how well that works out.  

Oh well, will keep snooping around and see what I can find.

---

### Post by gdonwallace on 2011-05-11
So i uninstalled LXDE and installed Lubuntu-core and its requirements.  Lets hope this fixes the problem I am having with lxpanel.  Will run for a while and see what happens.

---

### Post by gdonwallace on 2011-05-13
Looks like the problem persists.  Had to kill the process and relaunch, and is now running.

I would really like someone who also has this problem to let me know if there is something going on and how this can be fixed.  I don't understand why lxpanel is suddenly using so much CPU.

---

### Post by flemur13013 on 2011-05-13
I was running lxpanel in fluxbox and it caused problems (crashed or hung, I forget) and replaced it with fbpanel (IIRC the forerunner to lxpanel).

---

### Post by gdonwallace on 2011-05-16
I got in this morning and lxpanel had frozen over the weekend.

Decided to remove lxde and install xfce, see how that works.  So far the only thing I am seeing is an issue with redrawing some of the icons on the upper panel when I launch an xterm session and resize it.  Other than that it seems to be working OK.  Will see how things go as the day moves forward.

---

### Post by replica2010 on 2011-05-16
I noticed the same thing after installing Lubuntu.  It's a shame, as I really like the clean look of lxpanel, versus xfce-panel. However, I'm finding myself going back to xfce (and xubuntu-desktop), because Lubuntu (openbox-lxde) just can't handle dual monitors. (Without a LOT of screwing around; with xfce, it just 'works').

So, very sad; Lubuntu looked so promising, but without stability (and, you know, one of the desktop apps driving the cpu at 100% kind of kills the whole 'lightweight' bit) ... it's sort of pointless to switch.

(Are there really no people that want to use modern hardware with a wm, and not have all the fluffy eyecandy of Unity and ilk, but just something that looks passably nice and can, you know, manage windows? On two monitors? /rant-whine)

---

