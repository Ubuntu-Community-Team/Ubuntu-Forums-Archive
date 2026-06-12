---
title: "xorg.conf rewritten on restart"
date: 2007-02-05
forum: Desktop Environments
---

### Post by martinsaunders on 2007-02-05
Hi all,

I've had a good long search for this, but I can't seem to find anyone talking about this specific problem, but I apologise if this is a common topic and I've just missed the threads!

I've got a Acer TravelMate 3010 which has an Intel 945GM and a 1280x800 res (widescreen) LCD.

I've installed 915resolution from packages (sudo apt-get install 915resolution), and I've also run dpkg-reconfigure xserver-xorg to select the correct res. 

Once this is done, if I Ctrl-Alt-Backspace to restart X, 1280x800 is used and I'm happy, but if I restart the machine, it boots back into 1024x768. If I look in the /etc/X11 directory the working xorg.conf has been backed up, and a new xorg.conf is there without 1280x800 in it :mad:. If I edit that xorg.conf and manually add in 1280x800, CTRL-Alt-Backspace puts me back in 1280x800, but then a restart again replaces the xorg.conf and sticks me back in 1024x768!

I wondered if this might be happening because 915resolution isn't coming early enough in the boot sequence, so something is getting upset and giving me a new generic xorg.conf file. I installed 915resolution using the unbuntu package though, which I've assumed should start it at the right time.

So, does anyone have any ideas what is rewriting my xorg.conf file? :confused: 

Many thanks 

Martin

---

### Post by martinsaunders on 2007-02-05
#cough#

sneeky BTTT \\:D/

---

### Post by shareMenaPeace on 2007-02-05
Well maybe you forgott something?

You can try uninstalling and reinstalling with 

SYSTEM - > Administartion - > Synaptic

According to some user here in the forum it should work.

Or maybe this guide?
[http://absolutebeginner.wordpress.com/2006/08/20/absolute-beginner-guide-915resolution/](http://absolutebeginner.wordpress.com/2006/08/20/absolute-beginner-guide-915resolution/)

---

### Post by martinsaunders on 2007-02-06
Hi,

I tried reinstalling the package, and I also followed the link you suggested (thanks for posting that, very handy!). 

I tried turning off 'auto' in /etc/default/915resolution and setting the res and colour depth manually as the guide suggests, but sadly no difference. As an act of despiration I even tried sudo chattr -i /etc/X11/xorg.conf to stop the file being changed, but it was still being rewritten at boot.

Any final ideas before I ditch this idea and buy a new Mac? ](*,) 

Many thanks

Martin

---

### Post by jKeats3 on 2008-02-18
I'm having a similar issue as this fellow.  I get my video settings right, then reboot, and EVERY TIME I reboot, xorg.conf has been rewritten to the same crappy settings.  I'm relatively new to Ubuntu;  do I need to edit startup scripts or something to keep Ubuntu's hands OFF of my custom xorg.conf file?

---

### Post by mrmiserable on 2008-02-18
just a thought   do you have system-preference-screen resolution set to default box ticked if so this will override on start up 

just a settings thought

---

### Post by imoatama on 2008-02-21
If anyone experiencing this is running ATI's drivers, version Catalyst 8.x, then this is the probable cause. The newer drivers have a DB that records what settings it has put in xorg.conf and writes over any edits not in accordance with them. Most annoying.

Best bet is not to use aticonfig at all when installing ATI's drivers, but manually configure xorg.conf.

---

