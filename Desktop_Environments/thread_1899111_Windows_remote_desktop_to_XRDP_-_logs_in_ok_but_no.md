---
title: "Windows remote desktop to XRDP - logs in ok but no functionality"
date: 2011-12-22
forum: Desktop Environments
---

### Post by duncang92 on 2011-12-22
I apologise for being a complete Ubuntu N00B ..... I know enough about Linux and Ubuntu to be dangerous and that's about it.

I'm running Ubuntu 11.10 and can connect to my PC remotely from my netbook yet the screen that I see after I've logged in has none of the top bar or sidebar and only a basic window with File Edit etc..

This doesn't allow me to do anything such as checking for runaway process that is stopping my XBMC application from responding on the main PC.

The netbook is running Windows 7 and I'm using remote desktop to connect to the Linux PC with the Linux PC using XRDP. Currently set to sesman-Xvnc. I've tried all the other options and they don't help at all.

Any help or pointers would be greatly appreciated.

Thanks, Duncan

---

### Post by gradwell on 2011-12-29
I have the same problem.

I did a clean install of Ubuntu 11.10 and 

  sudo apt-get install xrdp

which worked.

Connect/logon is OK but I get a blank screen.

---

### Post by markherring on 2011-12-30
Same issue here as well. Allows me to log in but all I see id the background. No menus, no icon's no launcher, nothing. Any one got any ideas?

---

### Post by caliph007 on 2012-01-01
> **markherring said:**
> Same issue here as well. Allows me to log in but all I see id the background. No menus, no icon's no launcher, nothing. Any one got any ideas?

Same problem here. Clean install of 11.10 32bit.
When I resize the RDP window to a smaller size I see a menu bar with some non-helping functionality. But no lauchner, etc.

---

### Post by gradwell on 2012-01-05
Instructions for installing a newer version of XRDP are at [http://scarygliders.net/2011/11/17/x11rdp-ubuntu-11-10-gnome-3-xrdp-customization-new-hotness/](http://scarygliders.net/2011/11/17/x11rdp-ubuntu-11-10-gnome-3-xrdp-customization-new-hotness/) 

I and several others have tested these and they result in a working XRDP with Ubuntu 11.10.:p

---

### Post by duncang92 on 2012-02-10
After some playing I know that it's something to do with the video capabilities/settings of the system that I'm logging into .....

With only the standard video driver applied to the Ubuntu system then everything shows up good.

As soon as I load the ATI Catalyst driver then I can see the Desktop background but not the sidebar or other items such as System Settings etc..

If I play with the different video options from remote desktop then I can end up with a grey/blank screen that some of the other posters have mentioned ....

---

### Post by inobe on 2012-02-10
hey guys a quick search revealed.....

[http://it.rawconcept.com/2011/10/24/xrdp-ubuntu-11-10-update/](http://it.rawconcept.com/2011/10/24/xrdp-ubuntu-11-10-update/)

from bug 846407

[https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/846407](https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/846407)

may be the ubuntu side, not sure, just trying to help.

---

### Post by duncang92 on 2012-02-12
I fixed it.

The issue is that the remote display (the Windows one) that I am connecting from cannot manage to display the Unity Desktop settings. It took an inordinate amount of time googling, reading and trying things to find it.

I created a .xsession in my home directory /home/duncan in my case.

sudo gedit .xsession

.... and then edited it to have:

gnome-session --session=ubuntu-2d

I then changed the permissions to make it executable

sudo chmod 755 .xsession


I can now remotely login and everything is good.

---

### Post by Xfool on 2012-03-30
> **duncang92 said:**
> I fixed it.

The issue is that the remote display (the Windows one) that I am connecting from cannot manage to display the Unity Desktop settings. It took an inordinate amount of time googling, reading and trying things to find it.

I created a .xsession in my home directory /home/duncan in my case.

sudo gedit .xsession

.... and then edited it to have:

gnome-session --session=ubuntu-2d

I then changed the permissions to make it executable

sudo chmod 755 .xsession


I can now remotely login and everything is good.

duncang92 solution worked for me! 
I have seen this proposed elsewhere but the key was chmod 755 .xsession to make the session actually use the ubuntu-2d desktop.

After setting the desktop back to full color all of the taskbar icons showed up and look to be fully functional.

Thanks.

---

### Post by Xfool on 2012-03-30
After getting the desktop up I quickly ran into the problem of typing "d" in any command window takes you directly to the desktop. This makes it impossible to do anything like cd directory.

AtesComp has the solution
[http://ubuntuforums.org/showpost.php?p=10514519&postcount=8](http://ubuntuforums.org/showpost.php?p=10514519&postcount=8)

Re: D key (alone) shows desktop over Xrdp
Also being plagued by the inane and obtuse use of the "d" key via remote login, I troweled upon the black earth a little deeper.

Using "gconftool-2", I traveled down the structured tree to light upon the branch "/apps/metacity/global_keybindings" and found the "show_desktop" item. Lo, the value appears as "<Super>d". With apparent resolve, the poorly designed program is left bewildered as to the use of "<Super>" and randomly decide for itself to apparently ignore "<Super>" and select the "d" key. Unbeknownst to the astute end-user, the lowly "d" key has suddenly become his bane forevermore.

I protest! An error I say! I banish thee to the deepest pit of hell!
Changing this does not one any good fortune, sudo or not!

To correct heinous error, edit the swine of a file "/var/lib/gconf/debian.defaults/%gconf-tree.xml" and set the "show_desktop"s stringvalue to "Disabled" or whatever your humble preference. A trick upon this treat is to actually make entry of the word "Disabled" as it contains a "d". The astute reader shall quickly note the use of the "delete" key on "&lt;Super&gt", enter "isable", and use the existing "d". No longer shall each user need concern themselves with prior given solutions henceforth.

My given solution requires a logout/login.

Live well hence forth for all user logins thereafter. I fare thee anon.

---

### Post by SkipperTW on 2012-11-23
The below worked great - using an ATI card on 12.04 

created a .xsession in my home directory /home/duncan in my case.

sudo gedit .xsession

.... and then edited it to have:

gnome-session --session=ubuntu-2d

I then changed the permissions to make it executable

sudo chmod 755 .xsession



Thank you for the assistance - this is day one for me on Ubuntu -

---

### Post by gradwell on 2012-11-24
XRDP installs and works OK first time on Ubuntu 12.04.

---

### Post by rijo2 on 2013-08-07
Thanks! I am able to login with full functionality thanks to your info.

> **duncang92 said:**
> I fixed it.

The issue is that the remote display (the Windows one) that I am connecting from cannot manage to display the Unity Desktop settings. It took an inordinate amount of time googling, reading and trying things to find it.

I created a .xsession in my home directory /home/duncan in my case.

sudo gedit .xsession

.... and then edited it to have:

gnome-session --session=ubuntu-2d

I then changed the permissions to make it executable

sudo chmod 755 .xsession


I can now remotely login and everything is good.

---

