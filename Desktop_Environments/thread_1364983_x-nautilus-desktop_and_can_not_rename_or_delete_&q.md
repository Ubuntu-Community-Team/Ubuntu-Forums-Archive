---
title: "x-nautilus-desktop:/// and can not rename or delete &quot;Audio Disc.volume"
date: 2009-12-26
forum: Desktop Environments
---

### Post by coetzewc on 2009-12-26
**x-nautilus-desktop:/// and can not rename or delete  "Audio Disc.volume**             
                                                                Hi guys can you please help,

I have noticed nautilus crashing since yesterday when i insert CD media.
All icons disappear.

However if I reboot without media in my drive or re-login all icons are back.

There is one Icon called "Audio Disc.volume" that has been created and i have no idea how to remove this from my desktop.

Error Sorry, could not rename "Audio Disc.volume" to "Audio Disc.volume ": The specified location is not supported
It apparently sit at location x-nautilus-desktop:/// and has no rights or associations or permissions hove do i fix this error?

I hope i'm clear about the issue
1St Issue nautilus crashing
2nd issue this seemingly lost icon that shouldn't be there, i'm sure these two issues are related?

Thanks:confused:

---

### Post by MooPi on 2009-12-26
Hello, check and see if this same file is located in > /usr/share/applications. Let me know please.

---

### Post by coetzewc on 2009-12-26
this is my files in /usr/share/applications#

Hope this helps?

---

### Post by MooPi on 2009-12-26
I don't see anything that stands out but a .desktop file is named different from what is displayed. Something call AudioVolume, could be alsavolume.desktop. I was hoping one of the icons would stand out and look like the one positioned on your desktop. Anything ?
Could you right click on the offending Icon and see what name is under properties?

---

### Post by coetzewc on 2009-12-26
Please find attached ad problem description

---

### Post by MooPi on 2009-12-26
Here is a shot in the dark. In terminal type ```
sudo rm Audio Disc.volume
```If it won't let you do that type ```
sudo rm Audio
``` hit tab for auto complete then enter.

---

### Post by coetzewc on 2009-12-27
christo@christo-desktop:~$ cd Desktop
christo@christo-desktop:~/Desktop$ sudo rm Audio Disc.volume
[sudo] password for christo: 
rm: cannot remove `Audio': No such file or directory
rm: cannot remove `Disc.volume': No such file or directory
christo@christo-desktop:~/Desktop$ sudo rm Audio
rm: cannot remove `Audio': No such file or directory
christo@christo-desktop:~/Desktop$

I can't see anything in the command prompt that shows thet the file is there but it still shows up in the GUI on my desktop.

What will happen is I rename my Desktop to OLD and create a New Desktop, Will I stuff enything else up.

Im using Gnome 2.26.1 with Compiz and some Screenlets.

And there is some Wine stuff.

---

### Post by coetzewc on 2009-12-27
I have tried several things now, it seems it has someting to do with the way nautilus fires up your default program used to read Audio CD's, has anyone had similar problems with Icons disappearing when you load an Audio CD.

I till can not delete the "Audio Disc.volume" icon created some time earlier and cant find a way to give the filr at least rights to start working on it is' just visible in the gui...

Freeking me out....!! AArrgggg!! :confused::confused::confused:

---

### Post by karmic pig on 2009-12-30
hello,
you can delete it by opening a nautilus window. The icon will be on left part of screen
Delete it an refresh your desktop

Regards

---

### Post by coetzewc on 2010-01-10
Today after security updates checked and it was gone???

---

### Post by coetzewc on 2010-01-10
Oh and thanks guys for trying with me to solve...

Ubuntu people rock

---

### Post by ruifmartins on 2011-12-28
> **karmic pig said:**
> hello,
you can delete it by opening a nautilus window. The icon will be on left part of screen
Delete it an refresh your desktop

Regards

I'm sorry, no it does not appear! :confused:

---

