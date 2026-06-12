---
title: "GDM meltdown. Screen entirely blank after logging in."
date: 2009-05-13
forum: Desktop Environments
---

### Post by hkphooey on 2009-05-13
After a completely normal day yesterday I shut down my laptop running Ubuntu 9.04. This morning when I started it up, after logging in, I could only see my desktop background. No panels, no menus, no right-click, no window manager, and no key combinations (eg Alt-F2) were working. Nothing to do but shut down. 

I tried a LOT of things to get this working again. I'll include the list below in case it helps anyone else troubleshoot such an occurence. Eventually, after 4 hours I tracked it down to the fact that metacity, gnome-panel and nautilus weren't being loaded on startup. I made some .desktop files and put them into ~/.config/autostart . This seems to have temporarily solved the problem, but I know this is not the correct way to start things. How do I get the system back to normal? What is the correct way to call these three apps on Gnome startup?

As far as I can figure, the only thing I did yesterday which could have affected this was going into the Edit Menus application and removing some menu items which were not required - basically software which I'd uninstalled a long time ago and things I didn't ever use. How could this affect things so disastrously? 

OK, so now the long boring list of things I tried before hitting on the correct solution. 

1. Restart. Remove second monitor attached to VGA out. 

2. Ssh in from other box and restart display manager with 
	sudo /etc/init.d/gdm restart
Ctrl Alt Backspace is disabled in Ubuntu 9.04. Well lets get ctrl alt backspace working anyway.
	sudo apt-get install dontzap
	sudo dontzap -d

3. Login with Gnome failsafe mode. 

4. Login with failsafe terminal. OK we got in, but wireless isn't working.

5. From Failsafe terminal, rename 
	~/.gnome2
	~/.gconf
	~/.gconfd
	~/.config

Logout and try login as gnome, gnome failsafe. Nothing happening. 

6. Try a different window manager.
	sudo apt-get install fluxbox
Then at the login prompt, select Session > Fluxbox.
That works. 

7. Something to do with gnome install? 
	sudo apt-get install --reinstall ubuntu-desktop
Nope. How about when I restore all the orginal .conf directories. Nope. 

8. How about 
	sudo apt-get purge ubuntu-desktop
	sudo apt-get install ubuntu-desktop
Nope.

9. Whats in gconftool 
      gconftool-2 --get /desktop/gnome/session/required_components_list 
Give me  ["windowmanager","panel","filemanager"], which is apparently right. 

10. Login as Failsafe terminal. Running metacity and gnome-panel works ... but you can't get a command line in the normal session. 
Searching around on how to autostart these gave me my idea about putting .desktop files in the autostart directory. 

11. Not tried: apt-get install kubuntu-desktop (180 megs of hell)

So basically ... how could I so completely hose my system doing something like editing menus? And how do I get it back to normal?

---

### Post by micio on 2009-05-13
you was looking for a solution and you tried a lot of things, but have you looked into ~/.xsession-errors ?

meybe there is something helpful into that file.. 
Let us know

---

### Post by lzap on 2009-05-13
Maybe the same problem: [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/371808](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/371808)

---

### Post by hkphooey on 2009-05-14
Hi. Thanks for taking time to reply. Its often a bit lonely in these forums ... :-)

micio: Yes I did find .xsessionerrors and looked in it, but there was nothing interesting in there. Sorry I can't remember exactly what it was, and of course the file has now been overwritten. 

lzap: Thanks for the pointer. It doesn't really look like the bug exactly. Once it was broken it was completely broken and I couldn't log in at all. I even created a new user and tried to log in under the new account, but it had the same effect. 

As far as I can tell, something I did deleting UNUSED menu items, caused this, which seems pretty serious. I've been using computers for 25 years. Linux for 5 and Ubuntu exclusively for 2. It took me half a day to figure out what was going wrong, so imagine what a novice user would think if they did the same thing ...

---

### Post by hkphooey on 2009-05-18
I still haven't figured out how to get nautilus, gnome-panel, and metacity to start when I log into Gnome Display manager. Really this shouldn't be so complicated. 

Also I've been having more problems which I believe are also related to me removing menu items.

When I click on a zip archive, I'm prompted to install new software to help me open it. It gives me the choice of Ark, which I've never used. 

file-roller is installed, and has never been uninstalled. I can run file-roller from the command line and its perfectly happy. I can then process archives with it. However Gnome desktop seems to have forgotten all about it. 

The .desktop files for it are present in 
/usr/share/app-install/desktop/
and
/usr/share/applications/

I've tried re-installing it. No deal. 

I can't remove it as it will take the whole gnome-desktop package with it. ie everything. 

So how do I convince gnome and/or the menu system that this app is installed, and available? And I think in solving this, I'll also solve the problem of how to get metacity, nautilus and gnome-panel to activate on login.

---

### Post by hkphooey on 2009-05-21
OK well after wasting a week on this, plus finding a new, irritating problem with the archive manager file-roller*. I gave up. 

I reinstalled from the CD last night, and pretty much everything is working fine after about 4 hours of effort. Guess I should have done that a week ago and saved myself the hours of anguish. 

However, I still don't see _why_ this might have happened. All the incidents seem to be related to removing items from the menu, and there's no way that should cause this sort of havoc. 

Gah ... until the next time .... 

* file-roller was installed. However, every time I clicked on an archive, Ubuntu thought for a while and offered to install Ark. If I uninstalled file-roller, it would also offer to install that. However when I re-installed it, it just ignored it and offered to install Ark again. I checked the location of many many .desktop files, and they were all there. Completely mystifying.

---

