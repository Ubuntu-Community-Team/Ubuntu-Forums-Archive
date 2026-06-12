---
title: "Monitor Resolution"
date: 2009-06-24
forum: Desktop Environments
---

### Post by AJack10600 on 2009-06-24
When I first started Ubuntu 9.04 I had a resolution of 1600x1200, then I changed it down to 1024×768. Now the funny thing is that once I had changed it down, I could not see the other settings in the Monitor settings anymore. Only smaller pixel settings. 
 
How can I go back to the  1600x1200 setting ?

---

### Post by Alex8080 on 2009-06-24
Try using keyboard navigation and anticipate the Apply-Button. That would be my method :KS

If you can still use your ubuntu, you could also execute
```

gksudo gedit /etc/X11/xorg.conf

```in the terminal and change the resolution back to what you need.

If your ubuntu is unuseable you could:

[LIST]
[*]try out different start-methods of your installation at GRUB.
[*]start from live-cd.
[/LIST]
to modify the file mentioned above.

---

### Post by AJack10600 on 2009-06-24
I guess I expressed it wrongly... 
 
I do not mean the settings on the monitor, I mean the monitor settings in Ubuntu, monitor application. I simply do not see the old and bigger resolutions anymore...

---

### Post by Alex8080 on 2009-06-24
So the problem seems to be that the possible monitor-resolutions are not recognized correctly, right?

I am not an expert on this, but if you already had the setting before (which means that it works), then I would backup my xorg.conf and try to set it manually in the file, with the risk, that it might not work after restarting the system ... (see options in my first post for resetting ubuntu)

:popcorn:

Maybe somebody else here can lead you to a cleaner solution :D

---

### Post by AJack10600 on 2009-06-24
yea thx...
 
I fear that it's got to go through the command lines..

---

### Post by blackxored on 2009-06-24
Try changing the Frequency (Mhz) from the graphical app. If not stick to bash.

---

