---
title: "Odd Lockups After Apt-Get Upgrade"
date: 2005-03-09
forum: Desktop Environments
---

### Post by darthsabbath on 2005-03-09
Hi, guys, 

I hope I have the right forum, and I apologize in advance for mis-posting if not.  However, as the issue is not a specific apt-get question, that's why I did not post it in those... 

Anywoo...

I just started running Ubuntu, and so far, I'm digging it.  However, on my laptop installation, I'm having some difficulties.  When I install Ubuntu, and update the software everything goes smooth.

From there, I login, and connect to the internet (via NIC, as I'm also having a wireless issue), and follow these steps from ubuntuguide.org:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

From there, I run apt-get update and apt-get upgrade, to upgrade to the latest packages.  After that, things seem to go to hell... for example, the Themes applet will not open, or the the dropdown menus will not open.  Or sometimes certain apps, such as Firefox or Rhythmbox will lockup.  All symptoms are intermittant, and not related to any application.

Now, I know the easy answer is... "Don't do that anymore."  And I'm not.

My question is:  am I doing anything wrong?  This is going to be my third installation of Ubuntu (unless there's someway I can return to a pre-upgrade state).

I really like Ubuntu, and want to stick with it.  This is my first Debian distro, and despite my problems, my desktop (which I have thankfully not done apt-get upgrade), is running fine.

Any advice on this issue (such as why this may be a problem) or how I can resolve it without a reinstall, would be greatly appreciated.

Thanks,
Phil

---

### Post by LongTooth on 2005-03-09
I can't say why your system is locking up the way it is. And an upgrade should not be a problem. At least it shouldn't. Update and upgrade shoud be part of everyday system care. Where you get into deep water is when you do a dist-grade and the new version is not ready. Like I did! Maybe this isn't an option for you, but you really should dist-upgrade to Hoary. I jumped the gun sometime ago not realizing Hoary was far from being ready. Really messed up my system. Hoary is getting close to it's release date and things are looking up. I've upgraded to Hoary and it's as stable as Warty. Did so without losing any data. It was indeed very painless. 

I would caution you. Comment out any added extra Warty repositories. I have yet to find out which one to add for Hoary. But when I first upgraded I included the add repositories for Warty. While they posed no problems, I did get authentication errors when updating or upgrading. Here is my sources list. As you can see, I've commented out the Warty repositories. I'm certain there are others one can include but for the moment, I'm taking the more cautious path. 

## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe  
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted  

 #deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
 #deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
 #deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe

---

### Post by darthsabbath on 2005-03-16
Just an update... sorry it's taking me so long to get back ot this... been working on some other issues.

Did a clean reinstall... still getting these issues, WITHOUT doing updates.  Looking back on the issue, it appears to be Gnome related, rather than just lockups.  For example, if I try to open Gedit (from either the command line or clicking on a launcher), I get the following in my .xsession-errors file

----------------

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp $/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/megatron:/tmp/.ICE-unix/4305
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(network-admin:4559): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specifie$

(gnome-terminal:4539): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specifie$
(gnome-terminal
** (gedit:4778): CRITICAL **: file gedit-prefs-manager.c: line 227 (gedit_prefs$

---------------

Restarting GNOME does not help.  When I open Gedit (again, as an example... this happens across several apps, and always intermittently), the mouse will switch to the "working" icon.  It will stay like this for up to a minute or so, then disappear, the window never opening. 

Other apps (the Firefox that came with the distro, for instance), will lockup randomly and have to be killed.  However, let's say I download Firefox 1.0.1 form mozilla.org, and install it, it works fine.  

Gonna try a dist-upgrade to Hoary, and see if it works any better.  If it doesn't, I'm going to do a clean installation of Hoary.

Again, the odd thing is, my desktop, with the exact same installation, works fine.  So I'm wondering if it's something with my specific setup... 

Oh well... any help appreciated... I'll keep y'all upgraded.  Thanks for all the help so far! :D

Phil

---

