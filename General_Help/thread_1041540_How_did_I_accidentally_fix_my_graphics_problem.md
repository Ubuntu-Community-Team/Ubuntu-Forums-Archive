---
title: "How did I accidentally fix my graphics problem?"
date: 2009-01-16
forum: General Help
---

### Post by Firestem4 on 2009-01-16
Ok well I am running Kubuntu 8.10 on an older Dell Inspiron 6000. (Intel 915m, 1gig ram, 1.7ghz Pentium M).

Ever since i started using Kubuntu on this laptop i have had a graphics corruption issue. (aside from the graphics garbage when a new window is rendered. That is a KDE.4.x+ problem). Anything that required (i believe) OpenGL, i would have Corruption. For example i tried starting LinCity, and (while the static image on the main screen was fine) anything that was an active object like the buttons for selecting various things. like Play, quit etc. Would become corrupted. Colors and odd chunking issues. I get a lot of slow response and graphics lag (very choppy).

No one seemed to know what the problem is. But recently I downloaded through Synaptic KDEBase among other stuff. And it included XScreensavers. When I enabled the XScreensaver Daemon it completely fixed my rendering problem and it works fine now. Can anyone please explain why? 

The reason I am asking is I want to know (i can guess it was the Daemon). What is a Daemon? Why did the XScreensaver Daemon fix my rendering problem? Does anyone know if this Daemon was apart of Kubuntu to begin with and I could have activated it through Terminal?

Any info would be great. I am very curious by nature and I would like to know what happened (and I want to really learn linux well. I've only been using it for almost 4 weeks now).

Thanks in advance.

---

### Post by dcstar on 2009-01-16
> **Firestem4 said:**
> O
......
No one seemed to know what the problem is. But recently I downloaded through Synaptic KDEBase among other stuff. And it included XScreensavers. When I enabled the XScreensaver Daemon it completely fixed my rendering problem and it works fine now. Can anyone please explain why? 

The reason I am asking is I want to know (i can guess it was the Daemon). What is a Daemon? 
......

A "daemon" is a program that runs in the background of your Linux system all of the time - instead of an application that you start and stop manually.

You may have downloaded and installed a later version of something that fixed your problem - just be happy it now works!

---

### Post by Firestem4 on 2009-01-17
Ok cool. Thanks for the explanation.

Yeah im happy it is working. I just wish i knew how.

---

