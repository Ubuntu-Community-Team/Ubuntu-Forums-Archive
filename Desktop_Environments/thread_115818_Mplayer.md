---
title: "Mplayer"
date: 2006-01-11
forum: Desktop Environments
---

### Post by shawnzyoo on 2006-01-11
i reinstalled mplayer and all the codecs
when i play a file it runs fine
but then when i enlarge the window (from very small)
the video gets really choppy
any suggestions/ideas to whats going on?
thank you

---

### Post by Ampersand on 2006-01-11
One possibility would be going to Properties, then under the Video tab try selecting a different driver from the list.

---

### Post by kaamos on 2006-01-11
.. the video output "xv" being probably a good choice.

---

### Post by bikeman on 2006-01-11
Another possibility is to enable DMA, if your HDD supports it and it is not already enabled.  I found that this solved my DVD playback choppiness, don't know if it would help when playing files.
Daniel

---

### Post by shawnzyoo on 2006-01-12
thanks for the help
i changed the driver last night 
and watched a movie, it slowly got out of sync
but then i tried another driver and it worked perfectly
thanks for the help

now i just need to try and get mlayer working with firefox. OI!
it shows mplayer embedded plugin
and downloads to 99% and does nothing
any suggestions?
once again thanks for the help

---

### Post by bikeman on 2006-01-12
I found [Automatix]("http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix") to be very helpful.  It installed all of the things I needed to get multimedia (and other stuff) set up and working properly.  Be sure that you have your sudo permissions set up properly (I didn't, the expert installation does not add the user to the sudoers list), and be sure to read the warning about illegal stuff in the US.

---

### Post by renzokuken on 2006-01-13
had exactly the same problem myself but solved it thanks to some help in these forums

i added the following two lines to my xorg.conf as follows

# sudo gedit /etc/X11/xorg.conf

then in the "Device" section add these two lines

Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"

would be a good idea to back up your xorg.conf first though so if it doesnt solve it u can revert to the old one

---

### Post by shawnzyoo on 2006-01-13
i had two input device sections
and i inputting it into both of them
the embedded mplayer goes to 99% then stops for a second
and then just shows STOPPED
i am at a loss for the most part..
thanks for the suggestion though

---

### Post by OldGaf on 2006-09-07
> **shawnzyoo said:**
> i had two input device sections
and i inputting it into both of them
the embedded mplayer goes to 99% then stops for a second
and then just shows STOPPED
i am at a loss for the most part..
thanks for the suggestion though

I had Mplayer working fine in Dapper and Breezy. Last night I installed Dapper again to get a nice clean Kubuntu install. I used Automatix to install Mplayer. Now I get audio but no video in FireFox. It works fine for local files, but not for imbedded ones...... ?

---

