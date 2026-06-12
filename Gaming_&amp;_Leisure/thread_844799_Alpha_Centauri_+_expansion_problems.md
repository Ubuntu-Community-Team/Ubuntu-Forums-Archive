---
title: "Alpha Centauri + expansion problems"
date: 2008-06-29
forum: Gaming &amp; Leisure
---

### Post by das letzte einhorn on 2008-06-29
Through some very extensive search over the internet, I have been able to grab native Linux ISOs of Alpha Centauri and it's expansion. They are nearly impossible to find now.

However, when I tried to run the setup, I had these issues pop up

xavier@Xavier:~/virtual-drives/1$ sh setup.sh
Loki Update Tool not found, running installation program
This installation doesn't support glibc-2.0 on Linux / x86_64

Please contact Loki Technical Support at [email]support@lokigames.com[/email]
Continuing with install ...
Loki Uninstall Tool not found, running installation program
This installation doesn't support glibc-2.0 on Linux / x86_64

Please contact Loki Technical Support at [email]support@lokigames.com[/email]
Continuing with install ...
This installation doesn't support glibc-2.0 on Linux / x86_64

Please contact Loki Technical Support at [email]support@lokigames.com[/email]

It seems that because my Ubuntu distribution is 64 bit, the game is nncompatible with it. Is there a workaround however?

---

### Post by Cappy on 2008-06-29
Look here: [http://ubuntuforums.org/showthread.php?t=667771](http://ubuntuforums.org/showthread.php?t=667771)

Someone already said on the thread that for Alpha Centauri you just need to use ```
linux32 ./setup.sh
```

---

### Post by das letzte einhorn on 2008-06-30
One part is resolved. However now I get writing permission issues

xavier@Xavier:~/virtual-drives/1/loki_update$ linux32 ./setup.sh
----====== Loki Update Tool installation program ======----

You are running a x86 machine with glibc-2.0
Hit Control-C anytime to cancel this installation program.

Would you like to read the /home/xavier/virtual-drives/1/loki_update/README file ? [Y/n] n
Please enter the installation path [/usr/local/Loki_Update] 
No write permission to /usr/local
Please enter the installation path [/usr/local/Loki_Update] 

When I try to open it with sudo, I get this

xavier@Xavier:~/virtual-drives/1/loki_update$ sudo linux32 sh setup.sh
sh: Can't open setup.sh

Any solutions on how to bypass this? I do not want to install it in my home folder.

---

### Post by Cappy on 2008-06-30
Use
```
sudo linux32 ./setup.sh
```

---

### Post by das letzte einhorn on 2008-06-30
Here is what I get

xavier@Xavier:~/virtual-drives/1$ sudo linux32 ./setup.sh
[sudo] password for xavier: 
linux32: ./setup.sh: Permission denied

Should I copy the content of the ISO image to the hard drive, and then do a chmod on the setup file?

---

### Post by Cappy on 2008-06-30
> **das letzte einhorn said:**
> Here is what I get

xavier@Xavier:~/virtual-drives/1$ sudo linux32 ./setup.sh
[sudo] password for xavier: 
linux32: ./setup.sh: Permission denied

Should I copy the content of the ISO image to the hard drive, and then do a chmod on the setup file?

You can probably copy only the installer over and have it work
```
cp ~/virtual-drives/1/setup.sh ~/Desktop/setup.sh
chmod +x ~/Desktop/setup.sh
sudo linux32 ~/Desktop/setup.sh

```

If not, then yes, you can copy the whole CD over to a folder.

Don't be afraid to experiment.

---

