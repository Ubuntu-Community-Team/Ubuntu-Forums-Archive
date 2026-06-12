---
title: "Right click context menu too fast"
date: 2010-10-14
forum: Desktop Environments
---

### Post by vibrunazo on 2010-10-14
I just upgraded from ubuntu 10.04 to 10.10 and noticed that right click stopped working on some applications.

Usually, there are two ways to select items on the right click context menu:
a) press and release right click, hover over option, press and release again
b) press and hold right click, hover over option, release right click

I lost option a). No matter how fast I press and release the right click button, it will select the first option on the menu as soon as I release it. So for example, the first option on the context menu on the chrome browser is "back". So if I try to open the context menu it will just go back. Because it selects the back option as soon as I release the right mouse button.

So far I only noticed this on Chrome and Eclipse. Firefox and the other default ubuntu apps are working properly.

Googling it, I found some other people with this issue, but no solution. Any idea what this could be about and how to fix it?

---

### Post by UpSignal on 2010-10-22
> **vibrunazo said:**
> I just upgraded from ubuntu 10.04 to 10.10 and noticed that right click stopped working on some applications.

Usually, there are two ways to select items on the right click context menu:
a) press and release right click, hover over option, press and release again
b) press and hold right click, hover over option, release right click

I lost option a). No matter how fast I press and release the right click button, it will select the first option on the menu as soon as I release it. So for example, the first option on the context menu on the chrome browser is "back". So if I try to open the context menu it will just go back. Because it selects the back option as soon as I release the right mouse button.

So far I only noticed this on Chrome and Eclipse. Firefox and the other default ubuntu apps are working properly.

Googling it, I found some other people with this issue, but no solution. Any idea what this could be about and how to fix it?

Annoying as hell. Happens to me also. You can add Skype and gnome easy tag on that list too. Specially skype is super annoying, you select a contact with your left click, and then you want to right click to select "chat" but instead, the right click happens so fast that it auto selects the first option, which is "call". So, i end up calling my contacts instead of text messaging. 
I never really searched for a solution for this, but yeah..it's a lot anoying

---

### Post by geoffjay on 2010-11-07
I don't know if I'm imagining this or not but I just turned the pointer sensitivity all the way down and it seems better. The number of new folders that I've created by accident in nautilus was really starting to get to me.

---

### Post by timchen on 2010-12-06
bump, I got this problem too.

Is there any way to disable the menu item select on right mouse button release? 

It is extremely annoying especially when you are using a mouse with high dpi and sensitivity...:(

---

### Post by vibrunazo on 2010-12-16
> **geoffjay said:**
> I don't know if I'm imagining this or not but I just turned the pointer sensitivity all the way down and it seems better. The number of new folders that I've created by accident in nautilus was really starting to get to me.I've tried turning sensitivity down. But it doesn't do anything.

Does anyone have a solution for this yet?

Also, where is this bug on? Is it a gnome specific bug? Or an ubuntu specific bug? What does Skype, Chrome and Eclipse have in common? I have no idea where to report this bug to. :O

---

### Post by geoffjay on 2010-12-17
This doesn't appear to be a gnome issue, I'm running in Mint 10 right now and am not having this problem.

I'm wondering if it's related to the mouse or the USB driver for it, I changed my mouse at work (32-bit Lucid) and it stopped.

---

### Post by mikemintz on 2011-01-08
> **vibrunazo said:**
> 
Also, where is this bug on? Is it a gnome specific bug? Or an ubuntu specific bug? What does Skype, Chrome and Eclipse have in common? I have no idea where to report this bug to. :O

Is this the bug? [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/681567](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/681567)

---

### Post by snimavat on 2011-01-22
> **UpSignal said:**
> Annoying as hell. Happens to me also. You can add Skype and gnome easy tag on that list too. Specially skype is super annoying, you select a contact with your left click, and then you want to right click to select "chat" but instead, the right click happens so fast that it auto selects the first option, which is "call". So, i end up calling my contacts instead of text messaging. 
I never really searched for a solution for this, but yeah..it's a lot anoying

Did any one got any solution to this issue ? Its really annoying ..

---

### Post by snimavat on 2011-02-01
Bump.. 

I have exactly same problem, and its really annoying.. did any one find any solution.

Note: 
Its not ubuntu running inside vmware, I have installed ubuntu on a separate HDD.
I am using logitech mouse with default driver provided by ubuntu

---

### Post by wishfullink on 2011-02-05
i've got the same issue, it's super annoying...

---

### Post by dmi on 2011-03-04
Quick solution was to connect my A4Tech X-750F USB mouse via USB-to-PS/2 connector.
That solved the problem.

Happened to me on Ubuntu 10.10 in Eclipse, gedit and konsole. Never happened in Firefox.

---

### Post by UpSignal on 2011-03-16
I still have the same problem on maverick. And as far as things are going, i don't think this would ever be fixed.
anyway, i'm starting to get used to the "press right button and don't release it untill you move the mouse to the desired option" lol. decreasing the sensitivity doesn't work for me

---

### Post by snimavat on 2011-05-14
Is there any update on this issue ! Its a pain.
It happens with eclipse, and the ubuntu itself (file manager, context menus etc). Being a developer, I have to work on eclipse whole day, so it's been a major pain.

No problem in firefox for me.

---

### Post by vibrunazo on 2011-05-14
> **snimavat said:**
> Is there any update on this issue ! Its a pain.
It happens with eclipse, and the ubuntu itself (file manager, context menus etc). Being a developer, I have to work on eclipse whole day, so it's been a major pain.

No problem in firefox for me.

Do you use an USB mouse? Try changing to a PS-2 one, or use an adaptor. And see if that helps.

---

### Post by kmajor on 2011-08-29
This appears to be a USB issue of some sort, if you follow this thread [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/681567](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/681567)

People were able to fix this by hooking up their mouse via PS2 port, of course that only works if you have one.  Do they sell firewire mice :-)

---

### Post by notany on 2012-01-16
I confirm this also. Clicking desktop few times solves it temporarily. Then it happens again. 

Might not be related, but Eclipse also freezes at random intervals and same solution forks for it. 

[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/326477](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/326477)

---

