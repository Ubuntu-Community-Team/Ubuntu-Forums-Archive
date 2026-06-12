---
title: "Ubuntu 12.10 and Cinnamon - no desktop icons"
date: 2012-10-26
forum: Desktop Environments
---

### Post by jsradley on 2012-10-26
I've just upgraded to Ubuntu 12.10 and added Cinnamon 1.6.4-0ubuntu1~quantal1 but I cannot add any Icons to the Desktop or have the Computer Icon present if selected in setup.

Is there anyone else with this issue, and does anyone know how to solve.

thanks
John

---

### Post by larrys4227 on 2012-10-26
Probably not much help here (Not running Ubuntu or Mint/Cinn) but I believe there is a setting to disable icons or anything else from showing on the desktop.  Sounds like its enabled.

Navigate your way to /home/user/desktop and see if there is anything in that folder.  If there is, and you cant see it when viewing the actual desktop, then it is enabled.

If there is nothing there, move a picture or something into that folder and then view the desktop again.

Not sure where exactly to find this setting tho ... but its there.

HTH

---

### Post by skeve on 2012-10-26
> **jsradley said:**
> I've just upgraded to Ubuntu 12.10 and added Cinnamon 1.6.4-0ubuntu1~quantal1 but I cannot add any Icons to the Desktop or have the Computer Icon present if selected in setup.

Is there anyone else with this issue, and does anyone know how to solve.

thanks
John

same here, didn't manage to solve the problem :(

---

### Post by sickpuppet on 2012-10-27
This was happening for me on 12.04. I just start Nautilus and the icons reappear. 

I came across this post looking for problems with Cinnamon on 12.10, before I upgrade my production system.

---

### Post by mrkeef on 2012-10-28
Solved it!!!

Use dconf editor Go to org-gnome-desktop-background and tick "Show desktop icons"

---

### Post by jimubu on 2012-10-30
> **mrkeef said:**
> Solved it!!!

Use dconf editor Go to org-gnome-desktop-background and tick "Show desktop icons"

This fixed the issue. Thanks a lot.

---

### Post by jsradley on 2012-11-05
And for me too!
Thanks very much

---

### Post by SiflOlly on 2012-11-09
> **mrkeef said:**
> Solved it!!!

Use dconf editor Go to org-gnome-desktop-background and tick "Show desktop icons"

How do you use/run dconf editor?  I am having this problem also.

---

### Post by exploder on 2012-11-10
Desktop icons will not show up reliably if you have both Nemo and Nautilus installed. Remove Nautilus and the desktop icons should work fine. Nemo is a fork of Nautilus and the two conflict with each other.

---

### Post by Dr.Bimle on 2012-11-20
This is a file manager conflict as Nautilus handles the desktop in an Ubuntu Gnome session and Nemo handles it in Cinnamon. When you install Cinnamon you end up with two file managers that "want" to be default, and Cinnamon expects Nemo to be.

Best solution to avoid conflicts is to either create an Ubuntu remaster without Nautilus (complicated) or, well, use a Mint Cinnamon iso as base and install Ubuntu specific goodies on it if you wish. Simply uninstalling Nautilus is AFAIK not possible easily, Gnome will require it as a dependency until you convince it otherwise.

---

### Post by itsterry on 2013-01-31
> **mrkeef said:**
> Solved it!!!

Use dconf editor Go to org-gnome-desktop-background and tick "Show desktop icons"

Worked for me too: thank you!

---

### Post by cbanakis on 2013-02-20
> **mrkeef said:**
> Solved it!!!

Use dconf editor Go to org-gnome-desktop-background and tick "Show desktop icons"


Thanks, worked for me too.

---

### Post by jonnymopar on 2013-05-21
I used dconf editor and it still only worked half of the time.  Sometimes you'd get icons, sometimes not.  When I didn't get icons, I just type **sudo killall nautilus**, then opened a Nemo window.  Voila, icons.

However, since I don't have much on this particular computer yet, I decided to see what would happen if I just did **sudo apt-get purge nautilus**.  It only removed like 3 packages, and I've lost no functionality in Cinnamon that I can tell.  Plus... icons every time!

---

### Post by Quirrif on 2013-06-20
For all the ones asking how to fix this and being ignored:
Press ALT + F2 in your keyboard, a small screen will show up. There you type the following:
**dconf-editor** and then press ENTER.

dconf-editor will open. In the left pane, navigate to:
org /gnome / desktop / background

In the right pane, check **show-desktop-icons**.

Done, hope this helps.

---

### Post by suicideking on 2013-07-03
> **Quirrif said:**
> For all the ones asking how to fix this and being ignored:
Press ALT + F2 in your keyboard, a small screen will show up. There you type the following:
**dconf-editor** and then press ENTER.

dconf-editor will open. In the left pane, navigate to:
org /gnome / desktop / background

In the right pane, check **show-desktop-icons**.

Done, hope this helps.

First post, so yeah, noob question:

I'm using 12.04 ubuntu with cinnamon. When I do the above, alt + F2 and enter 'dconf-editor' it says 'command not found'

I was poking through the menus the other day and found a way to turn on the computer icon. I lost battery power and didn't log off and on again to save settings, so now can't find it. Is there somewhere else to turn it on?

---

### Post by mario21 on 2014-02-22
Also check noobslab for how to set nemo as default without removing nautilus [http://www.noobslab.com/2014/02/set-nemo-as-default-file-manager-in.html](http://www.noobslab.com/2014/02/set-nemo-as-default-file-manager-in.html)

---

