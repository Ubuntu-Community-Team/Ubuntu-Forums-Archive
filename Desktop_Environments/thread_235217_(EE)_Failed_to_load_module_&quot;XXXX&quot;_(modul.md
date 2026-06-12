---
title: "(EE) Failed to load module &quot;XXXX&quot; (module does not exist, 0)"
date: 2006-08-12
forum: Desktop Environments
---

### Post by Jerim on 2006-08-12
I was using Synaptic Package manager to remove a few programs I no longer need. I must have hit a few things I shouldn't and now it won't load xorg. It just boots up to a command prompt.

I was able to use apt-get to get gtk and gnome installed back. When I go to configure xorg, the only three video options it gives me is voodoo, silicon and some other one. I am using the Intel 915 integrated video on a Dell Inspiron B130. None of the three options seem to work. 

The error I get when I try the command "startx" is 
(EE) Failed to load module "XXX" (module does not exist, 0)
(EE) No drivers available.
The XXXX is anything I set it to be. For now, I have it set to 
i915 but I am not sure that module is loaded anymore and I don't know how to load it back or even it is the right one. I have tried editing xorg.conf by hand.

The short term question is how do I get i915 installed back? I have already tried using apt-get. However, the longer term question is how do I get back into gnome or even KDE if it would be quicker/easier? 

BTW, It would be incredible if Ubuntu had a repair function similar to Windows. You could just put the livecd in and hit repair. Ubuntu would restore all the system files to their original state, without touching your data. If Ubuntu wants to push into the consumer market, which I think it can, there will need to be an easy "catch all" way to fix any issue such as this.

---

### Post by Jerim on 2006-08-12
Okay, no one has responded in four hours. I am guessing everyone thinks if I just do a Google a search I will find the remedy. Well, I tried a Google search before posting, and I found some suggestions and I tried them. They didn't work. I even found some info that was off topic and not applicable. For instance, the error message was similar but not the same. I even found forums where some have had the same problem as I, but no one responded. So please don't think that I just rushed to ask this forum before even trying to fix it. I spent 36 hours trying to fix the problem first. The only time I post is as a last resort. In fact, if you know of a site that answers my pronblem, please just paste it for me.

---

### Post by Jerim on 2006-08-13
Wow, sure glad I am not running Windows right now. Where is this non-existant Linux support?

---

### Post by dysan100 on 2006-08-13
Did you already try this command?
sudo dpkg-reconfigure xserver-xorg
This will start a program to configure your xserver.
You can choose the VESA driver here.
Finally this program will create a new xorg.conf file in the directory /etc/X11
Now try to start Gnome by typing exit

---

### Post by Jerim on 2006-08-16
Here is the command if anyone is still interested:
[B]
sudo apt-get install gdm ubuntu-des[/B]ktop

That reinstalls everything you need. I actually found that while researching my sound issue. 

(BTW, I am giving serious contemplation to organizing all this data. All the data in the world won't help if no one can find it. If I had never had a sound problem, I would have never found the issue. Data should be organized by error messages or specific questions.)

---

