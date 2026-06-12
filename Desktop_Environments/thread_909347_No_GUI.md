---
title: "No GUI"
date: 2008-09-03
forum: Desktop Environments
---

### Post by blackriven on 2008-09-03
So I booted Ubuntu today and suddenly all the bars on the top and bottom are blank, nor is clicking in the places where buttons are supposed to be elicits any response. At first the bottom bar didn't appear at all. I tried the recovery options, and it appeared, but still no real GUI. Right clicking, save for this one restart, doesn't bring up any menus. I put in the cd, but it's the 7.10 version and I have Hardy, so I didn't try to boot using it yet, nor would I know what to fix anyway. Anyway, since the cd's been in the drive when I boot I get a message that nm-applet (/usr/bin/nm-applet) wants access to the default keyring, and prompts me for a password. I enter it, and there my ability to use Ubuntu ends. 
What did I do before that happened? Nothing in particular. I played with the audio options, trying to get firefox to share audio with other applications, but that's it. I tried to install video drivers to solve the blue lines I get in videos, but it was fairly long ago and I don't think that's the source of the problem. 

I dual boot it with Vista, and run it on an HP Pavilion dv6500. 
Help :(

---

### Post by blackriven on 2008-09-03
Did I post it in the wrong section or something? This is a serious problem, I can't use Ubuntu at all this way.

---

### Post by kdevil on 2008-09-03
This sounds a bit like a problem I had with an older version, so I might know how to fix it.  Does logging in as a different user work?

---

### Post by blackriven on 2008-09-03
I only have one user. I did try various combinations of alt+ctrl+F_, F1-F6 open new logins don't they? That's the closest I got to logging in as another user at any rate. I also tried alt+ctrl+backspace, and relogged as myself, but that doesn't help. And what's worse, is that the problem's severity changes. Sometimes I have both bars, but they are blanc, other times I get no bars at all.

---

### Post by kdevil on 2008-09-03
Log in through ctrl-alt-F1, and do 'sudo adduser temp'.  Once that's done, go back to the graphical login screen and log in as temp, and see if you have the same problem as with your normal account.

---

### Post by oldrocker99 on 2008-09-04
I tried that myself (reinstallation of Ubuntu Studio) and got the same: no bottom toolbar. Widows I minimize just disappear off to the right. This has never happened to me before after more reinstalls than I'd like to admit.

Any more ideas?

:guitar:

---

### Post by blackriven on 2008-09-04
> **kdevil said:**
> Log in through ctrl-alt-F1, and do 'sudo adduser temp'.  Once that's done, go back to the graphical login screen and log in as temp, and see if you have the same problem as with your normal account.

Yes it worked. Now how do I get my original account back? 
And what is it's problem to begin with?

---

### Post by kdevil on 2008-09-04
Ah, good.  If it's anything like the problem I had, something in GNOME got screwed up somehow.

Back in text-only mode, login as your usual account, then do:
mv .gconfd .gconfd_mightbebroken

After that, try logging in as usual and see if it's fixed.

---

### Post by blackriven on 2008-09-04
> **kdevil said:**
> Ah, good.  If it's anything like the problem I had, something in GNOME got screwed up somehow.

Back in text-only mode, login as your usual account, then do:
mv .gconfd .gconfd_mightbebroken

After that, try logging in as usual and see if it's fixed.

Didn't work. The only difference is that the background is restored to the default.

---

### Post by kdevil on 2008-09-04
Hmm, when I hit this problem, it was in an older version of GNOME.  I fixed it by deleting .gconfd, renaming the .gnome-desktop dir, then logging in and moving everything from the old (renamed) .gnome-desktop to the new .gnome-desktop.

Since .gnome-desktop no longer exists, try renaming the .gnome2 dir.

---

### Post by pdk on 2008-09-04
I'm not sure from your dexcription that I have the same problem. When I login from any user I get a blank screen (usual background color) and a mouse that moves. 
I can alt + ctl + F1 and login with no graphics. My .xsession-errors in my home dir says
process currently running setuid or setgid , not supported, refusing to initialize GTK+
Bug No 156632 was reported with this problem sometime in 2007 but the fix ( to remove the gdmflexiserver call in /etc/gdm/PreSession/Default) does not fix this. My home system has the same file and works.
The problem arose after downloading the latest updates using package manager this was the first time after install that the system was on the internet.
Where do we go from here ?
Peter

---

### Post by pdk on 2008-09-04
I've just been checking how to manually start xwindows.
I found
 sudo /etc/init.d/gdm stop
sudo /etc/init.d/kdm stop
sudo apt-get remove kdm
sudo apt-get remove gdm

maybe one could try uninstalling the 2 above and then re-installing ?
I'm working on my good home system at the moment.
Peter

---

