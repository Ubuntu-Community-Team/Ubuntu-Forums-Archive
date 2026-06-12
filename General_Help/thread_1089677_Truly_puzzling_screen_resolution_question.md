---
title: "Truly puzzling screen resolution question"
date: 2009-03-07
forum: General Help
---

### Post by longcipher on 2009-03-07
I was excited to try out ubuntu after hearing good things about it.

my wife has an old gateway laptop that was just sitting around which has a celeron m processor in it. i was excited to wipe away windows - great feeling there!

i installed - no problems. however, the screen resolution is way too big. It's currently at 1600x1200 with a 0hz refresh rate. when i try to take it down to the proper resolution, the screen is unreadable and overly pixelated - it's impossible to see what's going on at that point.

i read about envy - installed it - but can't even find where it was installed to run it.

i know nothing about the video card although i assume it's an onboard card.

please help - i know nothing about linux but would like to start using this cool OS - but first need to see all the real estate on my screen. :)

---

### Post by dhughes on 2009-03-07
Open up Terminal Applications>Accessories>Terminal and type ```
envyng -k 
```

 That should start Envy. Note the ng part after "envy".

---

### Post by Nano_ext3 on 2009-03-07
If you installed Ubuntu , not Kubuntu, then open up your terminal and type in "sudo apt-get install envyng-gtk"

Once this finishes, It will appear in your applications menu.  You may have just installed the "core" of envyng, which is exactly the front end graphical interface for the program itself.

Once launched, choose whether you have an ATI or NVIDIA graphics card, choose "automatic driver detection" and hopefully all goes well on install.

Cheers!

-Nano

---

### Post by longcipher on 2009-03-07
thanks for the ultra-quick replies!!


I (thought) i installed envy ng correctly, so i dhughes' command in terminal and get this error: "make sure that envyng-qt is installed"

So i tried to reinstall via terminal and get this error:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


sorry i am such a noob, i just don't know anything about linux yet.

---

### Post by dhughes on 2009-03-07
> **longcipher said:**
> thanks for the ultra-quick replies!!


I (thought) i installed envy ng correctly, so i dhughes' command in terminal and get this error: "make sure that envyng-qt is installed"

So i tried to reinstall via terminal and get this error:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


sorry i am such a noob, i just don't know anything about linux yet.


 Is Synaptic or Add/Remove Applications still open but minimized?

 If one is shut it down and you could try again to install, although I prefer Aptitude over apt, just replace "aptitude" where you'd put "apt-get" i.e. aptitude install envyng-qt

---

### Post by longcipher on 2009-03-07
this is so frustrating!

here is what i get after using aptitude:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


what am i doing wrong?

---

### Post by jgoguen on 2009-03-09
Are you running 'sudo aptitude...' or just 'aptitude...'?  If you aren't using 'sudo', it won't work.

If you are using sudo, then something else dealing with package installation is open.  Close Add/Remove Programs, Synaptic, Adept, everything that installs packages, and try again.

---

