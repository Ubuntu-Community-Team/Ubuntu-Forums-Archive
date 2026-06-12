---
title: "How to get to X11/xorg.conf from bash"
date: 2007-04-03
forum: Desktop Environments
---

### Post by DapperMe17 on 2007-04-03
Hi

Kubuntu 6.10


I mistakingly changed the nvidia driver name incorrectly while editing my X11/xorg.conf file.

Now, when I restart the machine, I'm presentd with the bash/tyy screen.


I attempted to edit the X11/xorg.conf file from Bash with "kdesu kate /etc/X11/xorg.conf" but unfortunately I get the response...."kate unable to open xserver" or something very similar, due to the driver name crash.


How can I get to the X11.xorg.conf from Bash?


Thanks

---

### Post by FuturePilot on 2007-04-03
Try this```
sudo nano -w /etc/X11/xorg.conf
```
After you make your changes <Ctrl> X and then Y to save then hit Enter.

---

### Post by DapperMe17 on 2007-04-04
Thanks for your reply!

How certain are you with this command? I only ask because the issue is on a remote PC, at another location from where I'm at.


Thanks

---

### Post by FuturePilot on 2007-04-04
I use this command a lot. Sometimes I even use it in the terminal if I don't feel like launching a text editor.  nano is your friend if you need to modify a config file and can't get X started.

---

### Post by DapperMe17 on 2007-04-04
Even from Bash/tyy prompt?

---

### Post by FuturePilot on 2007-04-04
Yeah I'm pretty sure, I've never used it from a remote location though, But I do use this all the time when I mess up X.

---

### Post by DapperMe17 on 2007-04-04
Thanks, will give it a try!

---

### Post by DapperMe17 on 2007-04-05
"sudo nano" worked like a charm!

Thanks

---

### Post by TheTinman on 2007-04-05
> **DapperMe17 said:**
> I attempted to edit the X11/xorg.conf file from Bash with "kdesu kate /etc/X11/xorg.conf" but unfortunately I get the response...."kate unable to open xserver" or something very similar, due to the driver name crash.

DapperMe17,

The reason nano worked remotely and Kate didn't is because Kate needs X while nano doesn't.  In other words, Kate is a GUI-based app while nano is a command line one.

---

### Post by DapperMe17 on 2007-04-05
Thanks for the distinction! 

So technically, I could use "nano" via terminal, rather than dealing with the text editor.

---

### Post by ceelo on 2007-04-05
I will have to try these commands next time I screw something up. :razz: Last time my X server wouldn't start, I had to load up a Knoppix LiveCD and mount my Linux drive through there to fix it.

---

