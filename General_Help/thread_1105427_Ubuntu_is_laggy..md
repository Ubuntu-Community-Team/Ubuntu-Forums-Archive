---
title: "Ubuntu is laggy."
date: 2009-03-24
forum: General Help
---

### Post by BramWillemsen on 2009-03-24
Hello everyone,

I installed ubuntu on my desktop yesterday since it works great on my laptop. The first thing i noticed though is that scrolling is really laggy. I installed the ATI proprietary drivers, just like i did on my laptop (got an ati x1950pro). Things still lagged. Scrolling in firefox let my CPU go up till 100% usage. I turned the resolution down from 1680*1050 to a lower resolution, and things seemed to be smoother. When i turned it back up to 1680*1050 it wasn't as laggy as before, but it still isnt smooth. When i'm at the 'change resolution' screen, there is a big red square which looks like a monitor that says 'unknown'. when i ddcprobe in the command line, it does detect that i am using a syncmaster though. Writing this message, the systemmonitor still shows that both cores are fluctuating around 45%. When i activite firefox by clicking on the minimized tab, the numbers go to 60%. When i click on 'system monitor' with firefox on the background (still visible), cpu goes down to 20% again. 

I have no clue why everything is lagging so badly, ** could it be that i have to install my monitor ? I heard xorg.conf can be configured for that, but i dont know how.**Or do i have to optimise my dual core ? My processor is a 5600+ X2 dual core AMD. The lagging occured before and after i installed the ATI proprietary drivers. Every bit of help would be greatly appreciated:)

Bram

---

### Post by BramWillemsen on 2009-03-24
i see posts about people adding stuff to their xorg.conf file to get proper support for their monitor. Could my lag be explained by not having such a thing?

---

### Post by BramWillemsen on 2009-03-25
i'm using intrepid btw

---

### Post by BramWillemsen on 2009-03-25
Does anyone have a tip of something that i could try? I am probably overlooking something

---

### Post by RansomStark on 2009-03-25
I used the Windows drivers package to install support for my monitor, all it needed was the .inf file and it was able to read the correct sync, refresh etc rates needed for the monitor.

---

### Post by 3Miro on 2009-03-25
KDE 3 had some tools for editing the monitor settings and I had to select a monitor from a list. I remember I first had some issues on 7.10 with the monitor that I got. Those were later resolved in 8.04. I cannot find where the setting manager is in GNOME, it gives me one for the scren resolution + detect display, but manual select display.

---

### Post by BramWillemsen on 2009-03-25
> **RansomStark said:**
> I used the Windows drivers package to install support for my monitor, all it needed was the .inf file and it was able to read the correct sync, refresh etc rates needed for the monitor.

Thanks for the suggestion. I've been looking at the .inf file now, but **i'm not really sure which line to add to xorg.conf.** This is all the .inf file contained. BTW, @3miro: would KDE allow me to select a screen ? This is what i get when i click on screen resolution: ** clicking detect display doesn't do anything ** 

[http://i35.photobucket.com/albums/d174/Brasempje/Screenshot-MonitorResolutionSetting.png](http://i35.photobucket.com/albums/d174/Brasempje/Screenshot-MonitorResolutionSetting.png)


Thanks for the help btw :)

---

### Post by BramWillemsen on 2009-03-25
sorry for the bump

---

### Post by BramWillemsen on 2009-03-25
bump

---

### Post by BramWillemsen on 2009-03-25
I copied some of the xorg.conf stuff from another user. I'm still seeing this when i go to the resolution manager. [http://i35.photobucket.com/albums/d174/Brasempje/Screenshot-MonitorResolutionSetting.png](http://i35.photobucket.com/albums/d174/Brasempje/Screenshot-MonitorResolutionSetting.png) . It's still not detected

**Do i have to change the screen section too in xorg.conf ? **

I attached xorg.conf, Can someone with some knowledge please give me a hint ?:)   (could only attach it as a .txt file)

---

