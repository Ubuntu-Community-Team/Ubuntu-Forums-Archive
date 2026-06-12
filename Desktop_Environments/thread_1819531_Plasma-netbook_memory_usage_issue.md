---
title: "Plasma-netbook memory usage issue"
date: 2011-08-06
forum: Desktop Environments
---

### Post by abedayyad on 2011-08-06
Salutations. 

After some earlier problems, I undid desktop effects for KDE. Nonetheless, I still have a major issue with plasma-netbook eating up huge amounts of CPU. Shortly after logging on today, it was up to over 80%; this, thankfully went down to about 40% later. Still, I don't understand why it should ever take up so much memory, and in fact it spikes to above 60% from time to time ... I read somewhere about switching from plasma-netbook to plasma-desktop (?), but I do not know if that would be wise or even what promises that holds. 

Has anybody else had similar issues?

---

### Post by SalHelder on 2011-08-07
What are your computer specs?

---

### Post by abedayyad on 2011-08-07
> **SalHelder said:**
> What are your computer specs?


Dear Sal, 

I'm running a Toshiba notebook with an AMD Sempron 2.1 GHz processor with 1.8 Gb RAM; it's not the fastest computer in the world, but I don't see why it should be eating up this much. This is also a fairly recent problem: sometimes there are spikes, but it's been about 3 days now for this problem to be consistent.

---

### Post by SalHelder on 2011-08-07
Ok, your computer doesn't seem to handle it very well, the problem about KDE4 is that it's quite heavy even if it doesn't consume much RAM, you'll need a more modern processor to do the job.

Anyway how does it behave with only plasma desktop without the plasma-netbook working? It might be a bug of some short, but I doubt that's the case.

---

### Post by abedayyad on 2011-08-07
Yeah, about that: I think I've not got the plasma-desktop installed (at least this seems to be the case when I check for it with dpkg). So I'm thinking now that I'm either going to install that or go with the upgrade to 10.10 or something, to see if that fixes it ... thanks very much for your help, Sal.

---

### Post by ankspo71 on 2011-08-08
Hi,
The process 'plasma-desktop' should not be using that much power. Something else is causing it to do that, or it is likely to be a bug. Is that the only process that uses that much power? Have you tried turning off desktop search features to see if it helps? Try also changing the quality of graphics at System Settings > Application Appearance > Style > Fine Tuning > Graphical Effects. Change this to a Low CPU option. You can also try turning off previews on the desktop and inside Dolphin to see if that helps.

If the process called "plasma-netbook" is giving problems while your computer is idle, then I think it has a bug or something else is causing it. I personally think single core processors above AMD 2.0 Ghz *should* be able to handle running the later KDE4 desktops (excluding games and flash videos), mainly because older Intel Pentium4 3.0ghz runs KDE4 nicely (including most games and videos), and my wife's older AMD Sempron 1.6ghz has a little bit of a struggle with KDE4 (but it is still usable for everyday use). The process "plasma-desktop" (and "plasma-netbook") continues to run at 0%-2% cpu usage on my P4 system. 

However, if you are seeing high cpu usage and spikes only while you are using heavier applications, then your computer might be too underpowered for what you normally do on your computer. In this case a lighter desktop might help fix it .

Depending on your version of KDE/Kubuntu, You might be able to switch between the 'plasma-netbook' and 'plasma-desktops' by going to System Settings > Workspace Behavior > Workspace, then change from notebook to desktop.

You can also choose layouts (aka activities) from "Desktop View", "Folder View", and "Search and Launch" (netbook style) by right clicking on your desktop and choosing "Configure Search and Launch" (or similar), then in the view category change the "layout:" option in the dropdown menu.

With that in mind, it is possible to do a mix of both. For example, use the search and launch layout with the desktop style KDE panel (plasma-desktop with search and launch layout/activity).

An upgrade in KDE packages or Kubuntu (or Ubuntu with KDE) might help fix the problem for you. You can also report this problem as a bug to the ubuntu developers. You can do this by opening your terminal and pasting the following command:
```
ubuntu-bug plasma-netbook
```
That command will collect bug information about plasma-desktop and send it to [https://bugs.launchpad.net/](https://bugs.launchpad.net/). (You will need to create an account there to report bugs)
Here is where you can report KDE specific bugs: [https://bugs.kde.org/](https://bugs.kde.org/)

Hope this helps.

---

### Post by abedayyad on 2011-08-08
Thanks ankspo, your suggestions were very helpful. Indeed, I have seen similar processors, or even slower processors, run this and more advanced OSs/DEs successfully; at the end of the day, I have been using this setup for about a year and this problem only really became a nuisance in the last week or so. 

I do report my bugs  ... and yes, I am kind of connecting this to other issues I have had with plasma-netbook (for example when switching between windows). 

In the meantime, what I've done is to put a little AutoRun script which launches plasma-desktop and closes plasma-netbook on login, and any way, I think I might stop using KDE.

Thanks again to both of you for all of your help.

---

