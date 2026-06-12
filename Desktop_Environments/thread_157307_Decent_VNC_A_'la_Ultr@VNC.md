---
title: "Decent VNC A 'la Ultr@VNC"
date: 2006-04-08
forum: Desktop Environments
---

### Post by holotone on 2006-04-08
Any suggestions for a DECENT VNC viewer program? vnc-viewer / tight vnc just isn't cutting it, especially with a lack of screen scaling and GUI to manage / save connection settings.

I mean, there's gotta be SOMETHING more powerful, right?

Thanks!

---

### Post by dermotti on 2006-04-08
FreeNX owns VNC.  100x faster

---

### Post by holotone on 2006-04-08
Sounds great and all, but it needs to be a VNC based solution since the general use will be from my Ubuntu laptop to various Win boxen across the US running Ultr@VNC server. Basically what I"m looking for is Ultr@VNC viewer, but for Linux.

---

### Post by neilmusgrove on 2006-04-09
Try XVNC Viewer from the breezy repositories.

Neil

---

### Post by holotone on 2006-04-11
[QUOTE=neilmusgrove]Try XVNC Viewer from the breezy repositories.

Neil[/QUOTE]
Does XVNC include screen scaling (I'm connecting to a 1280x1024 resolution Win box from my 1024x768 Ubuntu laptop) and a decent GUI for saving connection settings and the such?

Thanks for the tip, either way!

---

### Post by neilmusgrove on 2006-04-11
[QUOTE=holotone]Does XVNC include screen scaling (I'm connecting to a 1280x1024 resolution Win box from my 1024x768 Ubuntu laptop) and a decent GUI for saving connection settings and the such?[/QUOTE]

No gui afaik, you just run "xvncviewevr ipaddress", makes it easy to save connections as shortcuts. As for screen scaling i'm not sure, i don't use it much and when i do it's the other way round to you and so it appears as a smaller window on my screen.

---

### Post by holotone on 2006-04-11
Well, crap. I seriously can't believe that no one here knows of a decent VNC viewer that supports the most basic functions that any *win VNC viewer does. Hell, I'd be happy with just screen scaling, so I didn't have to use the slider bars every time I wanted to see the top right hand corner of the remote screen.

How about compiling Ultr@VNC from source? Is it possible?

---

### Post by xenmax on 2006-04-11
Try Applications->Internet->Terminal Server Client - Select VNC for protocol - this actually then starts up vncviewer itself, but this program provided a GUI that remembers your connection settings - 

It also has a Display tab where you can specify screeen size - but i do not know if it can do "gui scaling" as you termed it. My VNC connection is at 1024x768 to use it at that resolution at work, where at home, i prefer 800x600 - whatever resolution setting i give, i just get 1024x768 with sliders like you mentioned. I dont know if anything else needs enabling for this to work

PS: The display setting works better for RDPv5, but there it does not actually scale, instead of scaling *down* the resolution, all i get is a 800x600 size screen which is just 800x600 part of screen starting top-left with rest cut-off :???:

---

### Post by holotone on 2006-04-11
[QUOTE=xenmax]Try Applications->Internet->Terminal Server Client - Select VNC for protocol - this actually then starts up vncviewer itself, but this program provided a GUI that remembers your connection settings - 

It also has a Display tab where you can specify screeen size - but i do not know if it can do "gui scaling" as you termed it. My VNC connection is at 1024x768 to use it at that resolution at work, where at home, i prefer 800x600 - whatever resolution setting i give, i just get 1024x768 with sliders like you mentioned. I dont know if anything else needs enabling for this to work

PS: The display setting works better for RDPv5, but there it does not actually scale, instead of scaling *down* the resolution, all i get is a 800x600 size screen which is just 800x600 part of screen starting top-left with rest cut-off :???:[/QUOTE]

Thanks for the idea, but vncviewer is the exact app that isn't cutting it for me. Screen scaling is a MUST. It is incredibly annoying to have to use the sliders to see the full screen of the remote machine I am viewing. Even if the remote machine is 1024x768, I still get sliders because of the local machine needing space to render the window.

I really can't imagine that I'm the only person with this problem, but a thorough search of the forums and this thread here hasn't turned up anything.

Thanks again!

---

### Post by GeneralZod on 2006-04-11
Have you tried [krdc](http://etotheipiplusone.com/krdc.png)? If so, what did you find was missing from it?

---

### Post by holotone on 2006-04-11
[QUOTE=GeneralZod]Have you tried [krdc](http://etotheipiplusone.com/krdc.png)? If so, what did you find was missing from it?[/QUOTE]

Wow! _Exactly_ what I was looking for.. Thank you! Is it in the ubuntu repos, or does it need to be compiled from source?

Thanks again!

---

### Post by GeneralZod on 2006-04-11
[QUOTE=holotone]Wow! _Exactly_ what I was looking for.. Thank you! Is it in the ubuntu repos, or does it need to be compiled from source?

Thanks again![/QUOTE]

Oh ... cool :) I was hesitant to post the suggestion as a) this is the Kubuntu support forum and b) as far as I'm aware, krdc is actually included in the default Kubuntu install, so I'd assumed it was the first thing you'd tried!

krdc is indeed in the repos - good luck! :)

---

### Post by trotski on 2006-04-11
It comes with Kubuntu, under Internet in the K Menu.  So, it should be in the repos.

---

### Post by tagg3rx on 2006-04-12
I agree KRDC is way nice - i didnt know it existed either.

It wasent in my internet menu for some reason but was installed.  Just had to make my own launcher.

I upgraded from ubuntu to kubuntu using the repos.  This isnt the 1st time something was missing that was supposed to be there.

(just posting this if anyone else dosent see it in there menu - it is there - and it is way better than gnomes rdesktop)

---

### Post by xenmax on 2006-04-12
I use gnome DE. I decided to check out krdc following GeneralZod's suggestion. When i try to install krdc using Synaptic, it identifies a bunch of dependent packages. One of dependent packages gives a problem: It is downloaded no problem, but gives an error like this:
> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.4.3-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.4.3-0ubuntu1_all.deb)
  MD5Sum mismatch
by which i assume package data is corrupted - either during transit [unlikely since this is first time and i am seeing such an error and repeated [three to be precise] downloads are also met with same error]. So, could it be that this package in repo sources is corrupt? If so, what can i do abt it? Any suggestions? Is there an alternate location i can find this package and how do i tell synaptic to use that location? 
Thanks in advance for any help in this regard.

Update: Never mind folks. When i tried to post above contents, my DSL router started acting up and i could not connect [even though i was able to ping my dns :???:]. So i turned it off and on again and then i had a lightbulb go in my head - i tried downloading package once again and this time no problems, it downloaded and installed ok

---

### Post by xenmax on 2006-04-12
I tried krdc it is simply put awesome!! Actually i did not care for any of issues which OP mentioned, however one grouse i had with vncviewer was that it did not do this:
 -> I dont the techinal term. Whenever i minimize vncviewer and later go back, instead of having a local picture [image as jpeg,bitmap whatever] and loading that and only applying delta, it would always re-draw my "*entire*" screen - which would amount to 100KB atleast - i was so annoyed with it. The Terminal Server Client i mentioned has  a performance parameter called "Enable bitmap caching" - which i thought might be related to what i wanted, but enabling it had *no* effect on vncviewer - perhaps it only applies to RDP :sick

Thanks GeneralZod for suggestion, you are a lifesaver! KRDC is such a superior application than anything i found in gnome-desktop instlalled by default. It even did  resolution scaling [mine was 1024x768 to 800x600] - which i did not dig anyway -  higher resolution makes fonts smaller and pixels seem to lose a certain sharpness - but more  than that, i was avowed by the feature itself!

---

