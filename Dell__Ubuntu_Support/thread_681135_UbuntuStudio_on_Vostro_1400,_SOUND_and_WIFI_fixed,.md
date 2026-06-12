---
title: "UbuntuStudio on Vostro 1400, SOUND and WIFI fixed, How-To"
date: 2008-01-28
forum: Dell  Ubuntu Support
---

### Post by andyvich on 2008-01-28
Hey everyone!  So after having to scour around the forums for the information, I thought it would be nice to have the info and fixes in one post for someone like me who might be google-ing things trying to get set up.  Here is how I got the sound and wireless card working on my Vostro 1400 (two of the most common problems).  BTW I am using Ubuntu Studio 7.10, found here: [http://ubuntustudio.org/.]("http://ubuntustudio.org/")
These fixes should also work with regular Ubuntu.  This information was from other posts in the forums here and on other sites, and I take no personal credit for it, I am merely putting it all in one place for you.

        ***Sound Fix Code Entries in Console:***[LIST]
[*]sudo apt-get install     gstreamer0.10-plugins-ugly-multiverse[/LIST]Only install ugly multiverse plugin for gstreamer.  This gets mp3 playback and encoding.[LIST]
[*]sudo apt-get install     linux-backports-modules-generic[/LIST]I rebooted, and could now choose between
 Ubuntu 7.10, kernel 2.6.22-14-386 and Ubuntu 7.10, kernel 2.6.22-14-generic in the GRUB menu.  By choosing the latter (Generic) , the sound worked perfectly[COLOR=#000000]. [/COLOR][COLOR=#000080]_[You can comment out the other two entries above it with "]("http://ubuntuforums.org/showthread.php?t=627945")_[/COLOR][COLOR=Black][#" so it boots to generic automatically. ]("http://ubuntuforums.org/showthread.php?t=627945")[/COLOR] Type "sudo gedit /boot/grub/menu.lst " into the terminal to edit the Grub file, and be careful what you change![LIST]
[*]sudo gedit     /etc/modprobe.d/alsa-base[/LIST]Then paste this at the end of the file : options snd-hda-intel model=5stack
 (Other people have said using “3stack” instead of “5stack” works too.  Mine is set to 5stack)[LIST]
[*]Restart, and make sure to go into sound settings and enable everything and turn the volumes up.[/LIST]***WIFI Fix:***[LIST=1]
[*]Go to System>admin>restricted  drivers and enable them, and check off the driver for wifi (mine was     listed there)
[*]It might say you need to get a package first, if so get it from Synaptic first.
[*]Keep trying to enable that restricted driver, it might prompt for the driver location, choose     the download from the web option, and it will get it from the site just fine through an ethernet connection.
[*]Make sure to go into     System>Administration>Network and enable and configure the     WIFI card
[*]It should work, keep tinkering with settings if it doesn't[/LIST]Hope this helps someone!

---

### Post by fgiorgetti on 2008-02-18
Andy,

Thanks for submitting this tip. I was also googleing and trying to find out more information on the Audio driver, but what you posted worked for me as well.

I am using Ubuntu 7.10 and the intel audio driver is working fine here.

Thanks once again,

Fernando H Giorgetti

---

