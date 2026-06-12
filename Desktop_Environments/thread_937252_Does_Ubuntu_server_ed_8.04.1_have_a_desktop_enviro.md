---
title: "Does Ubuntu server ed 8.04.1 have a desktop enviroment?"
date: 2008-10-03
forum: Desktop Environments
---

### Post by serpentsilver01 on 2008-10-03
This is my first time and I am installed it on a old computer (was runing windows 98se)and there is no desktop enviroment. I was wondering if it because its a old computer/CPU or if it just doesn't have one and if there is can I get it to run on my old computer. Thanks in advance for any help. 

Processor: AMD-k6-2
Processor speed: 533/97 MHz

---

### Post by sayakb on 2008-10-03
Try openbox:
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by mali2297 on 2008-10-03
The server edition does not come with a graphical user interface, but you can install one from the repositories.

How much RAM does the computer have?

---

### Post by serpentsilver01 on 2008-10-03
> **mali2297 said:**
> The server edition does not come with a graphical user interface, but you can install one from the repositories.

How much RAM does the computer have?

So it's not the old cpu then... 

What repositories are you talking about? You mean you can install a graphical user interface for the CD, or another source?

I has 192MB ram and a 30 GB hard drive. Not much I know but I'm just experimenting with it and had this old computer sit there so I thought I'd give it a go for fun.

To: LinuxIsInnovation

Thank for the link I'll try it when I have some time. Seem to have great step by step information.

---

### Post by mali2297 on 2008-10-04
> **serpentsilver01 said:**
> 
What repositories are you talking about? You mean you can install a graphical user interface for the CD, or another source?

Primarily from the internet, see
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Also see
[http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)

Can't connect the computer to the internet?
If so, see
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

> 
I has 192MB ram and a 30 GB hard drive. Not much I know but I'm just experimenting with it and had this old computer sit there so I thought I'd give it a go for fun.


I think the specs are good enough to run a trimmed down version of ubuntu.

---

### Post by Linux Rookie on 2008-10-04
Greetings to all;

I am as my name says a Linux Rookie, I am a network admin that has mostly worked within the Windows environment, with a short detour into the IBM AS/400 world... terribly evil, I was put in the position this week of decommissioning a Windows 2000 server and commissioning a Linux Ubuntu server.  

Things being the way they are, I got the Ubuntu installed and up and running.  I have years ago, also dabbled in Redhat and slightly into Fedora Core.  With Ubuntu, I feel almost totally lost.  I am not a coder at all.  

What you may ask am I babbling about, I would like to install and run GNOME X-Windows on the box, but I have become frustrated with locating the pieces needed to make the installation happen.  May I seek guidance please?  After I am able to get this installed an running  I then need to install Apache 2.x, the main goal of the box is to become our company web server.  Do I understand it correctly that I will need to load LAMPS?

Thank You all for your understanding and asistance in this matter.

---

### Post by mali2297 on 2008-10-05
> **Linux Rookie said:**
> 
What you may ask am I babbling about, I would like to install and run GNOME X-Windows on the box, but I have become frustrated with locating the pieces needed to make the installation happen.  May I seek guidance please?  After I am able to get this installed an running  I then need to install Apache 2.x, the main goal of the box is to become our company web server.  Do I understand it correctly that I will need to load LAMPS?

You can install the meta package [gnome-core](http://packages.ubuntu.com/hardy/gnome-core):
```

sudo apt-get install gnome-core

```
You might also want to install gksu and synaptic. However, many people don't think a server should have a GUI.

For the rest, have you seen this [guide](https://help.ubuntu.com/8.04/serverguide/C/index.html)?

---

### Post by serpentsilver01 on 2008-10-05
Thanks for the info, but I have a question/problem. I tried to install openbox like suggested, but can seem to load it. it seem to have install alright, but when I type the command:

   openbox-session

it gives me and give me:

   error: xdg-autostart requires PyXDG to be installed

   Openbox-Message: Failed to open the display from the DISPLAY 

   environment variable.

Can someone help this newbie with this? Help Greatly appreciated.

---

### Post by mali2297 on 2008-10-05
You can search packages with apt-cache or on the web at [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

In this case, it seems that you need to install the package **python-xdg**:
```

sudo apt-get install python-xdg

```

---

### Post by serpentsilver01 on 2008-10-05
> **mali2297 said:**
> You can search packages with apt-cache or on the web at [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

In this case, it seems that you need to install the package **python-xdg**:
```

sudo apt-get install python-xdg

```

Thanks some progress, but I still have the openbox-message: Failed to ...

any ideas? :(

---

