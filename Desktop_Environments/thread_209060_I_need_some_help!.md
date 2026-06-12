---
title: "I need some help!"
date: 2006-07-04
forum: Desktop Environments
---

### Post by Magiczero on 2006-07-04
hi

I have a Hitachi SuperScan Surpreme 21 monitor and I am getting a new computer and I know that when I first installed Ubuntu on this computer I had to edit some xorg.config file but I dont remember how I had to do it. Don't I need to be logged in as an admin? How do I log in as an admin? The resalution needs to be 1024 x 768! Can anyone help me here? Please?  
Thanks alot
*I really need some help here**

---

### Post by jvictor on 2006-07-04
sudo gedit /etc/X11/xorg.conf


sudo acts as the shortcut to run a pgm as admin

scroll to somethign like this (if u r using a CRT)

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
      [B] HorizSync       30-70
       VertRefresh     50-120[/B]
EndSection


replace the bold section with ur monitors value, b careful incorrect values can mess up the monitor


 SubSection "Display"
                Depth           24
                Modes           "1152x864" "1024x768" "800x600" "640x480"
 EndSubSection

and add ur preferred resolution

---

### Post by Magiczero on 2006-07-04
I looked on my computer that I have my 21 inch monitor hooked up to and I don't see a bold place for what you said to look for.  What is supposed to say?  Maybe mine is just not bold.
Thankssudo gedit /etc/X11/xorg.conf


sudo acts as the shortcut to run a pgm as admin

scroll to somethign like this (if u r using a CRT)

Section "Monitor"
Identifier "SyncMaster"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-120
EndSection


replace the bold section with ur monitors value, b careful incorrect values can mess up the monitor


SubSection "Display"
Depth 24
Modes "1152x864" "1024x768" "800x600" "640x480"
EndSubSection

and add ur preferred resolution
__________________
[http://jubyvictor.blogspot.com/](http://jubyvictor.blogspot.com/)
jvictor is online now Report Bad Post   	Reply With Quote Quick reply to this message Multi-Quote with this Post
jvictor
View Public Profile
Send a private message to jvictor
Find More Posts by jvictor
Add jvictor to Your Buddy List
New Reply

---

### Post by jvictor on 2006-07-05
Well What I meant to say is that look for that text that is in bold in ur /etc/X11/xorg.conf file and IF its not there add those lines with the horizontal and vertical refresh values that are supported by your monitor 

Then go to the section that looks like 

SubSection "Display"
Depth 24
Modes "1152x864" "1024x768" "800x600" "640x480"
EndSubSection


and there u can add ur preferred resolution in the format show above

Sorry for being vague

---

