---
title: "Howto: Quick drag-n-drop burn DVD .iso file"
date: 2009-06-06
forum: General Help
---

### Post by dwasifar on 2009-06-06
Useta be you could right-click on a DVD .iso image and choose Write To Disc, and it would use a fairly straightforward utility to do it - Nautilus Burn, I think.  Now that choice uses Brasero, which I don't particularly like, not least which because its elapsed and remaining time estimates are so bad.  So I took the opportunity to make things easier on myself by creating a drag and drop launcher link on my desktop to burn DVD images.  I just drag the image onto the launcher and it burns it and ejects it.

Here's how:

1) Open text editor and paste in this:
```
#!/bin/sh
growisofs -Z /dev/dvd="$1"
eject /dev/dvd
```
2) Save to your home directory as burndvd.sh (or whatever you want to name it)
3) Set it executable (right-click and choose Properties>Permissions, or use chmod).
4) Create a desktop launcher that points to it (right-click on desktop and choose Create Launcher, using type Application in Terminal).

That's it.  To burn a DVD .iso file all you have to do is drag it over the launcher and let it go.  You'll get a terminal window with text showing the burn progress and the disc will eject when done.

---

### Post by jenkinbr on 2009-06-06
sudo apt-get install nautilus-cd-burner, but this will remove brasero.

---

### Post by dwasifar on 2009-06-06
> **jenkinbr said:**
> sudo apt-get install nautilus-cd-burner, but this will remove brasero.

Hey Jenny, long time no see!

I know you can do that, but this workaround is actually quicker than either Brasero or Nautilus Burner.  Instead of right-click, choose from menu, click OK, it's now a one-click operation: drag and release.

---

### Post by jenkinbr on 2009-06-06
Whoa - haven't seen you since the Community Games forum (in my ignorance, I didn't even bother looking at your handle)

One small issue with your script is it may not work on everyone's computer.  My computer links blank dvd's to /dev/cdrom0 or /dev/cdrom1 (depending on which drive I used)  For some reason, the /dev/dvd alias doesn't get used on my system....

---

### Post by AlarmingSword on 2009-06-06
> **dwasifar said:**
> 

That's it.  To burn a DVD .iso file all you have to do is drag it over the launcher and let it go.  You'll get a terminal window with text showing the burn progress and the disc will eject when done.

Thanks, dwasifar - I'll definitely be utilizing this :)

---

### Post by dwasifar on 2009-06-06
> **jenkinbr said:**
> One small issue with your script is it may not work on everyone's computer.  My computer links blank dvd's to /dev/cdrom0 or /dev/cdrom1 (depending on which drive I used)  For some reason, the /dev/dvd alias doesn't get used on my system....

That's true.  Users should use the proper alias for their system, be it /dev/dvd, /dev/cdrom, or whatever is appropriate for their drive.

---

