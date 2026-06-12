---
title: "Beryl and Kubuntu"
date: 2006-11-11
forum: Desktop Environments
---

### Post by ColinG on 2006-11-11
Vey quick question, to run beryl on Kubuntu do I have to have the Gnome Desktop installed? If so do I start beryl by typing beryl-manager in a kde terminal?

many thanks :)

---

### Post by igknighted on 2006-11-11
As far as I know beryl has no reliance on gnome

---

### Post by ColinG on 2006-11-11
Thanks!

This being the case, can someone point me in the direction of a nice HOWTO

Many thanks

---

### Post by tamagotono on 2006-11-11
Here is a quick generic HOWTO that I cobbled together, for my linux users group, from information on [www.beryl-project.org](www.beryl-project.org) . I highly recommend this site's Forum as it is the repository of all knowledge and wisdom regarding Beryl.  

Hope it helps.
**NOTE:  THESE INSTRUCTIONS ASSUME YOU ARE RUNNING UBUNTU 6.10 WHICH HAS AIGLX BUILT IN. IF NOT, THAN CHECK OUT THE WEBSITE LISTED BELOW...**
-------------------------------------------------------------------
GENERIC BERYL INSTALL INSTRUCTIONS
Step 1-Update your system.
	First enable all the extra repos (universe, multiverse)
	Update you system
		sudo apt-get update
		sudo apt-get dist-upgrade
Step 2-Install all needed packages.
	Add one of these repos to you sources.list
		deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy
		deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy
		deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy
Step 3-Backup xorg.conf file 
	sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
Step 4-Modify xorg.conf and install beryl.
	For NVIDIA Video Card follow this step:
		Edit /etc/X11/xorg.conf and add the following two lines to the screen section.
		Option "AddARGBGLXVisuals" "True"
		Option "DisableGLXRootClipping" "True"
			---------------------------------------------------
	For INTEL chipsets follow this step:
		Edit /etc/X11/xorg.conf and add the following line to the screen section.
			Option "XAANoOffscreenPixmaps"
			---------------------------------------------------
	For ATI Video Cards follow these steps (I haven't tried this myself):
		- Uninstall fglrx (because fglrx has his own libraries like libGL.so)
		- reinstall mesa packages (I just selected reinstall for all mesa , mesa-gl, mesa-glu ... in 			  synaptic).
		- Change xorg.conf to use the 'radeon' driver

Now install beryl.
	sudo apt-get install beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings
		 beryl-manager beryl beryl-dev emerald-themes
Restart xorg and everything should be ready to go!
You can start beryl by opening run (alt-F2) and typing beryl-manager or adding beryl-manger as a session start-up program

---

### Post by ColinG on 2006-11-11
Many thanks for this. I guess my very first job is to install the 9*** series Nvidia driver.

Thanks again for the help.
Colin :)

---

### Post by mexlinux on 2006-11-11
What about XGL, not needed any more?

---

### Post by WalmartSniperLX on 2006-11-11
Hmm I installed XGL/Beryl on my Kubuntu 6.06 system and it seems to have been set up fine. However it doesnt like ati/x1k lol :D and delivers really, really slow performance, and the visuals can get a bit buggy. :rolleyes:

Btw I used this : [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL)

---

### Post by ColinG on 2006-11-12
Thanks to all, and a really big THANKS at that.

Beryl now up and running on Kubuntu :p

Just two questions - 
I've ended up with a 386 kernel when I'm running a Pentium D. It seems to run ok but why a 386?
Why does the Adept Update Notifier appear on the taskbar after I have started Beryl Manager? I do not start the Manager until after it has closed (that is until after the notification icon in the notification area of the KDE task bar has shut/disappeared).

---

### Post by davebgimp on 2006-12-02
Same thing here for me with the Adept Notifier. I'm guessing Kwin by default hides it and Beryl just doesn't know that. I'll post back if I can find an answer on hiding it other than disabling it from starting.

In the meanwhile, you can manually run this command to kill it, restart it, where it seems to run as it should:
**sudo killall adept_notifier && adept_notifier &**

> **ColinG said:**
> Thanks to all, and a really big THANKS at that.

Beryl now up and running on Kubuntu :p

Just two questions - 
I've ended up with a 386 kernel when I'm running a Pentium D. It seems to run ok but why a 386?
Why does the Adept Update Notifier appear on the taskbar after I have started Beryl Manager? I do not start the Manager until after it has closed (that is until after the notification icon in the notification area of the KDE task bar has shut/disappeared).

---

### Post by davebgimp on 2006-12-02
Okay, I created a link to beryl-manager in .kde/Autostart and restarted X and the Adept Notifier seems to be hidden correctly. ps -A tells me it is in fact running, but it is no longer hanging out on my desktop. Hope that works for you too.

---

