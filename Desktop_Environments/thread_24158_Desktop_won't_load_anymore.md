---
title: "Desktop won't load anymore"
date: 2005-04-05
forum: Desktop Environments
---

### Post by Michael_Grosberg on 2005-04-05
I've had Ubuntu Hoary installed a couple of weeks ago, in a dual-boot  with Win2K.
It worked fine for some time but suddenly it won't load the desktop anymore!

After the login screen all I get is the a screen fillled with a brown color (the desktop background color when there is no wallpaper) and a working cursor. I can still switch to TTY by pressing Ctrl-Alt-1/2/3/4. 

Some more info - it started around the time I attempted to get my ATI card to work properly with TV-out and all by changing the driver. It didn't happen all the time at first, maybe in one out of three reboots. After I configured the driver properly, two days ago,  It stopped working altogether. I used the text mode to restore my backed up xorg.conf from before I changed the driver, but the problem remained, so maybe it has nothing to do with it after all - I'm totally confused by now!

What could be causing this? I assume there is some log file somewhere that will help me understand the problem. Where can I find it? I will post it here if I know where to look.

---

### Post by shakin on 2005-04-06
I would guess that an upgrade pooched your system. I had a similar experience when I had unofficial apt repositories in /etc/apt/sources.list

Keep only the official sources, not including universe and multiverse, then reinstall gnome. You can also install the kubuntu-desktop package to see if kde works. It's a decent backup just in case something happens to gnome.

---

### Post by sgarman on 2005-04-06
I'm experiencing the exact same thing - something hangs right when I log in. I do not see the gnome splash screen or hear the login sound. 

If I let the system sit in this state for about five minutes, it actually completes logging in. Then when I select System->Logout nothing happens, until a minute or so later when suddently the logout options screen appears where I can select logout/reboot/hibernate/etc. 

I am not running any non-ubuntu packages on this system. I'm open to suggestions on which logs might be relevant to post here.

---

### Post by sgarman on 2005-04-06
The solution to this problem is to raise the lo interface at boot time ("ifup lo" if you want to test this without rebooting). I had disabled the network service in order to keep my laptop from hanging at boot trying to raise the ethernet interface. 

See this thread for more details:

[http://ubuntuforums.org/showthread.php?t=23473&highlight=hangs](http://ubuntuforums.org/showthread.php?t=23473&highlight=hangs)

Regards,

Scott

---

### Post by Michael_Grosberg on 2005-04-07
[QUOTE=sgarman]The solution to this problem is to raise the lo interface at boot time ("ifup lo" if you want to test this without rebooting). I had disabled the network service in order to keep my laptop from hanging at boot trying to raise the ethernet interface. 

See this thread for more details:

[http://ubuntuforums.org/showthread.php?t=23473&highlight=hangs](http://ubuntuforums.org/showthread.php?t=23473&highlight=hangs)

Regards,

Scott[/QUOTE]

Scott, 
I'm happy to see I'm not the only one!
I'm a relative newbie to linux... how do I get the "ifup lo" command to run at boot time? do I add it to some file?

---

### Post by sgarman on 2005-04-07
You want to enable the network service to start at bootup. Try:

sudo update-rc.d -f networking defaults 35

---

### Post by Michael_Grosberg on 2005-04-09
[QUOTE=sgarman]You want to enable the network service to start at bootup. Try:

sudo update-rc.d -f networking defaults 35[/QUOTE]

Didn't work. I got a message saying it;s already enabled.

Now that Hoary final is out I'm going to do a clean install and hope it owrks properly.

---

