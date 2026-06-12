---
title: "Resize desktop"
date: 2009-03-16
forum: General Help
---

### Post by Schr0dinger on 2009-03-16
Hello, I just recently installed Ubuntu on my computer, and I'm using an HD LCD TV as a monitor, but the outer edges of my desktop are cut off, by the monitor, I've tried changing the resolutions, but that doesn't work, I have a program on my Windows computer where I can resize it, but I can't seem to find anything like that on Ubuntu, I hope you guys can help

I have a Nvidia 8800GT if that helps

---

### Post by Schr0dinger on 2009-03-16
bump, please there has to be someone that knows how to fix this, it's really frusterating

---

### Post by Schr0dinger on 2009-03-17
BTT. Please! this is making Ubuntu unusable for me, and it is very frustrating

---

### Post by VeryLost on 2009-03-17
Where did you get the program from?

See if there is a linux version of it.

I am a linux newb, but a windows jedi. Usually, manufactures of software have different versions on their site.

Also, there is something called WINE that you can install to run windows program on linux.

But since the program is changing setting I do not know if wine will help you out.

---

### Post by ruel- on 2009-03-17
first of all, it's a bad idea to triple post.. :(

I suggest you install restricted drivers(the latest ones) and use it..

System > Administration > Hardware Drivers


also, max your resolution and check for the refresh rate.. try each value...

---

### Post by Schr0dinger on 2009-03-17
> **ruel- said:**
> first of all, it's a bad idea to triple post.. :(

I suggest you install restricted drivers(the latest ones) and use it..

System > Administration > Hardware Drivers


also, max your resolution and check for the refresh rate.. try each value...

Well first of all, nobody was helping

second of all I've done all that

and the program that I can resize with came with my video card, but it doens't come with the drivers for linux, it's called NVIDIA control panel

---

### Post by mdurham on 2009-03-17
I have a tool installed called nvidia-settings that might allow you to do what you want, it's in the repos.
Cheers, Mike

---

### Post by Schr0dinger on 2009-03-18
no, I've recently tried that, and it's not working

---

### Post by ruel- on 2009-03-18
have you tried changing settings from your monitor?

---

### Post by Schr0dinger on 2009-03-18
> **ruel- said:**
> have you tried changing settings from your monitor?

multiple times, nothing seems to work

---

### Post by ruel- on 2009-03-18
try installing nvidia settings,

```
sudo apt-get install nvidia-settings
```

it's something similar in windows.. I have it, if you want, I'll give you a screen shot..

---

### Post by Schr0dinger on 2009-03-18
> **ruel- said:**
> try installing nvidia settings,

```
sudo apt-get install nvidia-settings
```

it's something similar in windows.. I have it, if you want, I'll give you a screen shot..

could you submit a screen shot please? I'm currently trying to go through Nvidia X server settings which I opened using the command sudo nvidia-settings 

if that is the same thing I cannot seem to find a way to resize the screen

thanks for the help, hopefully I can get this resolved, as I don't want to have to go back to windows

---

### Post by ruel- on 2009-03-18
well, you found it.. and you don't need a screenshot.. it's the same as the nvidia control panel in windows isn't it?

if you still can't find it..

install envy, and install your drivers from there, maybe it will help.. good luck!

---

### Post by Schr0dinger on 2009-03-18
> **ruel- said:**
> well, you found it.. and you don't need a screenshot.. it's the same as the nvidia control panel in windows isn't it?

if you still can't find it..

install envy, and install your drivers from there, maybe it will help.. good luck!

alright, and no, it's very different, seems kindof stripped down, I will try the envy thing, thank you

---

