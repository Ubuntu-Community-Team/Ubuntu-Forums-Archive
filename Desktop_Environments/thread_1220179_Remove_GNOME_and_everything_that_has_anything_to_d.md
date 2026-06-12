---
title: "Remove GNOME and everything that has anything to do with it"
date: 2009-07-22
forum: Desktop Environments
---

### Post by JFASI on 2009-07-22
Ok, as the title might imply, I want a server. However, the server kernels for Ubuntu are incompatible with CUDA, as they aren't able to build an interface for it, etc. The desktop kernels do not have this problem, so I figured I'd go ahead and install Ubuntu desktop, and then promptly ditch GNOME. 

However, it seems I have no idea how to do that. I've gone ahead and purged the package ubuntu-desktop, but gdm and friends still starts. I've tried deleting everything in aptitude, but I quickly realized that dependencies are not fun to work with. Is there any (relatively) easy way of removing GNOME? 

What about stopping it from starting ever?

---

### Post by mojoman on 2009-07-22
Try this, it will remove Gnome for starters. You'll probably want to do that from to console mode and then remove everything that has to do with x-server as well. Should get you pretty close to a server setup. Maybe removing alsa-stuff as well. Be sure to let aptitude or apt-get handle all you dependencies.

[http://www.psychocats.net/ubuntu/purekde]("http://www.psychocats.net/ubuntu/purekde")

---

### Post by Sub101 on 2009-07-22
You can remove gdm.

```
sudo apt-get remove gdm
```

Which would result in you booting to terminal.

---

### Post by .kkursor on 2009-07-22
Try installing text-only installation from Ubuntu Desktop Alternate CD (F4 on boot). Maybe this is a solution.

---

### Post by JFASI on 2009-07-22
Great, that worked perfectly, aside from minor version numbering issues. Now how would I go about ditching X?

---

### Post by .kkursor on 2009-07-22
What does the word "ditching" mean? The dictionary says that is emergency landing on water :(

---

### Post by mojoman on 2009-07-22
> **JFASI said:**
> Great, that worked perfectly, aside from minor version numbering issues. Now how would I go about ditching X?

```
apt-get remove --purge xserver-xorg-core x11-common xserver-xorg
```

will probably do the trick and should remove any other x-server package as well. You'll want to simulate it first just to see what it removes. _Notice the -s below which will do a dry-run of the command._

```
apt-get remove -s --purge xserver-xorg-core x11-common xserver-xorg
```

Obviously, you'll have to do this in CLI mode or else God knows what happens.

/mojoman

---

### Post by JFASI on 2009-07-22
Well, I meant remove it. I suppose it wouldn't do any harm to leave it in place, since I'm not using it and I have more than enough hard drive space...

---

### Post by .kkursor on 2009-07-22
It's better to remove it to free some RAM, I think.

---

