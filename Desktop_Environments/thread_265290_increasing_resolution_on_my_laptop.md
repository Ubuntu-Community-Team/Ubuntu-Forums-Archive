---
title: "increasing resolution on my laptop"
date: 2006-09-25
forum: Desktop Environments
---

### Post by Drew32 on 2006-09-25
I tried to increase my resolution but i cannot increase it past 1024 X 768 and 60hz refresh rate even though when i had XP on there i had mine set to 1280 X something or other...  how would i set ubuntu to the same resolution and a higher refresh rate?  i tried installing nvidia drivers which is what my laptop has but it didnt do any good. :(

---

### Post by wpshooter on 2006-09-25
I think you have to edit the xorg.conf file under the etc/X11 directory.  But I don't know exactly what you change.

Maybe one of the video experts can help you, if you put your question in the video subforum.

---

### Post by sabelsen on 2006-09-25
Yes, you need to edit your xorg.conf file (/etc/X11/xorg.conf). But first, take a backup of your /etc/X11/xorg.conf (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup). Scroll down until you see something like this: 

Section "Screen"
	Identifier	"someIdentifier"
	Device		"someVideoDeviceCardIdentifier"
	Monitor		"SomeMonitorName"
	DefaultDepth	24
        SubSection "Display"
	      Depth	16
	      Modes	"1920x1200" "1680x1680" "1600x1200" "1280x1024"   
"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

You probably have more than one "SubSection "Display"", but follow my directions and I believe this will work fine for you. Notice the DefaultDepth parameter. If your monitor handles that many bits of colors, which I assume, set that one to 24. Now, for all your "SubSection "Display""'s, add your preferred resolution (one that does not exceed the maximum resolution) at the beginning of the Modes line. I, for example, added "1920x1200", which is my preferred resolution, at the front of every Modes line. All the other resolutions were already there when I edited xorg.conf. If a SubSection with Depth 24 is not listed, then you have to create it yourself by just copying one of the other sections (or mine) and modify it accordingly. When you're done, save and close the file. Now, you need to throw yourself out of your X environment. So, in your X environment, press Ctrl+Alt+Backspace, which let's you back into Gnome or whatever after a couple of seconds. If you monitor blinks a couple of times and kicks you back to the shell, well, your modification didn't work. You can check the reason for the failure through the response you get from X or by tail'ing /var/log/messages. If you want to enter X again, and your configuration didn't work, you can simply overwrite your xorg.conf with your backup file. If it worked, congrats!

Hope this helps.

---

### Post by sabelsen on 2006-09-25
Drew32, your preferred resolution is 1280x1024 if I understand your post correctly. With laptop monitors you don't really need to adjust the refresh rate, 60 is just fine. If you still want to "play" around with rates you should google "xorg.conf HorizSync VertRefresh" or something, and find the values for your own monitor.0

---

### Post by ramjet_1953 on 2006-09-26
Before you do any of the above, what chipset do you have?
If you have the intel 915 graphics chipset, just download "915resolution", using Synaptic.
Then read the docs that come with it and you should be sweet.

Regards,
Roger :D

---

