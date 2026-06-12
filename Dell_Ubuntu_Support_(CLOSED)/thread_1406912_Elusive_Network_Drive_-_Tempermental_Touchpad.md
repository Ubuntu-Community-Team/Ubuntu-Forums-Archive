---
title: "Elusive Network Drive - Tempermental Touchpad"
date: 2010-02-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by K-Sub on 2010-02-14
I have already posted part of this under Networking, but I thought that I would try here as well.  

I recently bought a Dell Mini 10v running Ubuntu 8.04.  This is my first  plunge into the world of Linux.  On my home network I have a network  hard drive.  Sometimes when I log on to the Mini it can see the network  drive, as well as the other computers on the network, sometimes it  doesn't see anything on the network.  When it does see the network  drive, sometimes it can access the subfolders, sometime it can't.  I  have done a lot of searching on the forums and have not been able to  find anything about intermittent connections.  Here is another wrinkle  that may or may not be relevant, I also have a networked HP Laserjet  printer.  Regardless of whether or not the Mini can see the network  drive and the other computers, it seems to always be able to see and use  the printer.  

Also, I find the touchpad on this machine very difficult to control, the cursor seems to jump and wander on its own.  I have played with the settings and have not been able to find a combination that fixes this.

Any suggestions/ideas/tips on either of these problems?  Thanx.

---

### Post by K-Sub on 2010-02-15
OK, I managed to fix my network problem.  In the file browser (Nautilus?) I went  to Go - Location and then typed in smb://192.168.1.XXX, i.e. the IP  address for the drive.  Once I got there, I set up a bookmark and I was  done.  Now, whenever I want to go to this drive, all I need to do is  click on the bookmark.  This worked so well that I also used it to log  on to the disk drives on my Windows PC.  Worked there too.  I'm not sure  why I was having trouble logging on to these drives before, but this  works like a champ.

Now, if anyone has any wisdom about the oversensitive touchpad, please let me know.

---

### Post by bobcollard on 2010-02-16
> **K-Sub said:**
> 

Now, if anyone has any wisdom about the oversensitive touchpad, please let me know.
  Install the applet gsynaptics either from  Synaptic Package Manager or through Terminal using "sudo apt-get install gsynaptics" (without quotes)  You can put it in your startup and set it each time you reboot or disable the touch pad altogether, like, if you use a mouse on the side.

EDIT: You must disable touch pad in  the Mouse section of your System settings.  Both won't work together.

---

### Post by Boondoklife on 2010-02-16
The network issue is one that I always have and really the best solution for me was to install a mDNS server on my NAS this ensures that the service is always listed under network.

---

### Post by K-Sub on 2010-02-16
> **bobcollard said:**
> Install the applet gsynaptics either from  Synaptic Package Manager or through Terminal using "sudo apt-get install gsynaptics" (without quotes)  You can put it in your startup and set it each time you reboot or disable the touch pad altogether, like, if you use a mouse on the side.

EDIT: You must disable touch pad in  the Mouse section of your System settings.  Both won't work together.

OK, well I installed the applet gsynaptics, but when I go to run it, I get the message 'GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

Any idea where the appropriate file would reside so I can take care of this?  Thanks.

---

### Post by bobcollard on 2010-02-16
> **K-Sub said:**
> OK, well I installed the applet gsynaptics, but when I go to run it, I get the message 'GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

Any idea where the appropriate file would reside so I can take care of this?  Thanks.
Sorry, didn't know they had this problem in ubuntu gnome.  remove gsynaptics and install gpointing-device-settings. It is a newer one and a bit more complicated.  That's why I recommended gsynaptics.  I don't know where that file goes.

---

### Post by Boondoklife on 2010-02-16
> **K-Sub said:**
> OK, well I installed the applet gsynaptics, but when I go to run it, I get the message 'GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

Any idea where the appropriate file would reside so I can take care of this?  Thanks.
Try /etc/X11/xorg.conf

---

### Post by K-Sub on 2010-02-17
> **Boondoklife said:**
> Try /etc/X11/xorg.conf

Would that be in the root directory?  I can't find etc.

---

### Post by K-Sub on 2010-02-17
> **K-Sub said:**
> Would that be in the root directory?  I can't find etc.

Never mind, I found it, thanks.

---

### Post by K-Sub on 2010-02-17
Well, ok, I found the file, opened it with Text Editor, and added 'SHMConfig' 'true', but I get an error message that I don't have permission to change the file.  Now what?  Is there some other way to do this?  As you can see, I'm an Ubuntu newbie (about a week.)

---

### Post by Boondoklife on 2010-02-17
> **K-Sub said:**
> Well, ok, I found the file, opened it with Text Editor, and added 'SHMConfig' 'true', but I get an error message that I don't have permission to change the file.  Now what?  Is there some other way to do this?  As you can see, I'm an Ubuntu newbie (about a week.)

press ALT+F2
type gksudo gedit /etc/X11/xorg.conf
click run

This will open the file with admin rights and allow you to save it. Please make sure you know what you are doing and make a backup if you are not sure.

---

### Post by K-Sub on 2010-02-17
> **Boondoklife said:**
> press ALT+F2
type gksudo gedit /etc/X11/xorg.conf
click run

This will open the file with admin rights and allow you to save it. Please make sure you know what you are doing and make a backup if you are not sure.

Well, I did have a backup, but I wasn't 100% sure that I knew what I was , doing...anyway it worked like a champ, thanks.

---

