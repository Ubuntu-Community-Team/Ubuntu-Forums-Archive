---
title: "Beryl"
date: 2007-04-03
forum: Desktop Effects &amp; Customization
---

### Post by CorranSW on 2007-04-03
Arghhh i've been trying to install beryl for months and nothing seems to work.... i just keep getting these random errors no one else seems to be encountering.... Does anyone here who is experianced in ubuntu, have xfire, or skype or anything????? If i can get camtasia for linux ill take a video and upload it to youtube just so i can show u guys whats going wrong... maybe i'm justing not getting something here???? I think my main problem is that the nvidia drivers just dont seem to want to activate themselves??? i've tryed programs like envy to try and do it for me but they dont work... when i try to follow the official guide on the nvidia website i get something like this,
i enter
gangster@gangster-desktop:~$ sh NVIDIA-Linux-x86_64-1.0-9755-pkg2.run
sh: Can't open NVIDIA-Linux-x86_64-1.0-9755-pkg2.run
and i get that crap....  after downloading the file.. any other tutorials seem to yield the same results...
Just for the record my system specs are....
Nvidia 7900GTX
AMD 4800+
2 gigs of ram
Asus -A8n SLI deluxe
Creative soundblaster xfi card...
I really want to get Beryl working i have been trying for at least a month... i have tryed every guide that has ever been posted on the internet...
If somone would please enlighten me i would be sooooo greatfull.....

---

### Post by CorranSW on 2007-04-03
Also i was going to ask how to log in a super admin on the terminal.. forgot the command for that

---

### Post by CorranSW on 2007-04-03
Is there any program that can do all the dirty work for me i havent found one just thought i would ask???

---

### Post by CorranSW on 2007-04-03
K i think i just got the drivers working.... how do i check to make sure they are there??? Reason i think they are working is because i am now able to run a 1900 Res, and i get the nvidia logo when i start ubuntu???

---

### Post by irish_flu on 2007-04-03
> **CorranSW said:**
> Also i was going to ask how to log in a super admin on the terminal.. forgot the command for that


Sorry I can't help you with Beryl problems, but I can help with this:  If you want to run a command from the terminal as the superuser, type:

sudo command (for instance, if you wanted to run the "nano" text editor as superuser, you'd type "sudo nano").

If you've enabled your root account on the box, and you want to switch to that user in the terminal, use the "su" command to Switch User.

---

### Post by nonewmsgs on 2007-04-03
automatix bleeder does the dirty work for installing beryl.

---

### Post by compiledkernel on 2007-04-04
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)
[https://help.ubuntu.com/community/BerylOnEdgy](https://help.ubuntu.com/community/BerylOnEdgy)
[https://wiki.ubuntu.com/BerylOnFeisty?highlight=%28beryl%29](https://wiki.ubuntu.com/BerylOnFeisty?highlight=%28beryl%29)

Word of caution on using Bleeder, it can cause some system breakage if your not careful, just refer back to a-x site if you run into issues.

---

### Post by x0rsw1tch on 2007-06-04
Well, first install the nvidia drivers. That has to be done before beryl will work at all as it needs hardware acceleration via drivers. You can install them automatically through "System >> Administration >> Restricted Drivers Manager". Thats the easiest way to get them installed.

then open a terminal (Applications >> Accessories >> Terminal):
```
sudo apt-get install beryl beryl-manager beryl-settings emerald emerald-themes
```

After installation, go to "Applications >> System Tools >> Beryl Manager"


done!


enjoy!

---

### Post by x0rsw1tch on 2007-06-04
If you want to install your nvidia drivers manually with the .run file; you need to log out of X first. So log out, then press Ctrl+Alt+F1....

Type In:
```
sudo telinit 3
sudo killalll Xorg X
cd /path/to/drivers
chmod 755 NVIDIA-Linux-x86_64-1.0-9755-pkg2.run
sh NVIDIA-Linux-x86_64-1.0-9755-pkg2.run

```

Then follow the prompts....

After your done....

```
sudo telinit 5
```

to get back into the login prompt. Then follow the steps i posted above to install beryl.

---

### Post by elfstone214 on 2007-06-04
Have you tried this guide?
[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

I have always used it and it always works, I have an Nvidia 7600GT

---

