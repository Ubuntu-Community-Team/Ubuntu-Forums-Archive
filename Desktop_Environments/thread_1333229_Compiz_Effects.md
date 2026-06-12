---
title: "Compiz Effects"
date: 2009-11-21
forum: Desktop Environments
---

### Post by Geffers on 2009-11-21
I've got 9.10 installed on my Acer Aspire One netbook and am pleased with the setup.

Recently I tried a Live version of Knoppix on the netbook and the compiz effects seemed to work very well (Spinning transparent desktops etc) but I cannot seem to get this in URM.

Synaptic shows compiz to be installed but the normal compiz key shortcuts don't have any effect.

Anyone had this working on URM

Geffers

---

### Post by yossell on 2009-11-21
I don't know URM (netbook remix?)

At least in Ubuntu, there are various window managers. The default is metacity - while running metacity you can make all the changes you like to compiz - and nothing happens. Could this be happening for you?

On Ubuntu, you can start compiz proper either by going to preferences ->appearances, choosing visual effects tab and then ticking 'extra'. Alternatively, you can press alt+f2 and enter `compiz --replace' in the command line, or run it from a terminal. 

I don't know what the equivalents of these are in URM - maybe this will give you some ideas of what to try. 

yossell

---

### Post by Geffers on 2009-11-21
> **yossell said:**
> 

I don't know what the equivalents of these are in URM - maybe this will give you some ideas of what to try. 

yossell

Thanks, I'll give this a try but one of the problems with URM is the desktop layout, the extra 'desktops' do not appear or I haven't twigged how to switch between them.

Geffers

---

### Post by yossell on 2009-11-21
It still might be of help if you told me what URM meant.

It may just be different terminology, but for me `desktop' isn't the same as 'window manager.' 

For me, different desktops are just different virtual spaces where you keep various collections of windows. I don't think this has anything to do with your issue. A window manager controls the appearance of windows (the frames and buttons) and gives you a way of interacting with them. I think this *may* have something to do with your issue - you want to make sure that the windows manager compiz is running.

yossell

---

### Post by Geffers on 2009-11-23
> **yossell said:**
> It still might be of help if you told me what URM meant.

It may just be different terminology, but for me `desktop' isn't the same as 'window manager.' 

For me, different desktops are just different virtual spaces where you keep various collections of windows. I don't think this has anything to do with your issue. A window manager controls the appearance of windows (the frames and buttons) and gives you a way of interacting with them. I think this *may* have something to do with your issue - you want to make sure that the windows manager compiz is running.

yossell

Apologies for lack of explanation.

URM is Ubuntu's netbook version and stands for Ubuntu ReMix, it is a cut down version of a normal desktop/laptop OS and uses Gnome. The actual desktop is optimised for the smaller screen and as such lacks some of obvious features of the Gnome Windows Manager.

Geffers

---

