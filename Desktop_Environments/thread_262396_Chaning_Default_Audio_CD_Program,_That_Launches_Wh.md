---
title: "Chaning Default Audio CD Program, That Launches When A CD Is Inserted"
date: 2006-09-21
forum: Desktop Environments
---

### Post by buzlink on 2006-09-21
How do I change the default Audio Program that launches when I insert a CD?

Right now Sound Juicer launches and I'm wanting to change the default program to Banshee instead.

Thanks!

---

### Post by reclusivemonkey on 2006-09-22
> **buzlink said:**
> How do I change the default Audio Program that launches when I insert a CD?

Right now Sound Juicer launches and I'm wanting to change the default program to Banshee instead.

Thanks!

Try Preferences --> Removable Media

Apologies if that's not quite right I am at work ATM, but you should be able to find it. When you do, just enter banshee instead of soundjuicer.

---

### Post by buzlink on 2006-09-25
Nope
Any ideas?

---

### Post by bettermentflux on 2006-10-31
Got it:

On the Main Menu go to System/Preferences/Removable Drives and Media.

Under the Multimedia Tab Change the "Audio CD Command" to 

```
banshee --play --audio-cd /dev/hdc
```

The will autoplay audio CD's through Banshee when the CD is inserted.

---

### Post by pingswept on 2007-08-26
If you're not sure of the /dev name of your CD player, you can use:

```
banshee --play --audio-cd %d
```

The %d will get filled in with the correct drive name when the command is executed in response to a CD getting inserted.

---

### Post by rdsherwood on 2008-04-06
> **bettermentflux said:**
> Got it:

On the Main Menu go to System/Preferences/Removable Drives and Media.

Under the Multimedia Tab Change the "Audio CD Command" to 

```
banshee --play --audio-cd /dev/hdc
```

The will autoplay audio CD's through Banshee when the CD is inserted.

Another Newbie question: I'm using Xfce, and can't seem to find the place to change these defaults (there isn't a System/Preferences in Xfce, that I can find. 

Can somebody point me in the correct direction to make the same change using Xfce? 

Thanks!! 

Ron

---

### Post by rdsherwood on 2008-04-06
I found the answer to my own question. For anyone else:

Open Thunar then select edit>preferences>Advanced. Then under Volume Management click "configure".

---

### Post by bartonski on 2008-04-19
> **bettermentflux said:**
> Got it:

On the Main Menu go to System/Preferences/Removable Drives and Media.

Under the Multimedia Tab Change the "Audio CD Command" to 

```
banshee --play --audio-cd /dev/hdc
```

The will autoplay audio CD's through Banshee when the CD is inserted.

Ok. I'm running Hardy Heron with a Gnome Desktop... I don't have a multimedia tab under System/Preferences/Removable Drives and Media. Any hints on a) how to enable this tab or b) what to do instead?

---

### Post by bartonski on 2008-04-19
A little more poking around shows that this is found under

System/Preferences/File Management

in the "Media" Tab.

---

### Post by kimvall on 2008-04-25
Ok, am I missing something here?

System/Preferences/Removable Drives and Media: Can't find any CD option here (but I have for one Tablets - great!)

System/Preferences/File Management -> I don't have this option at all.

What the heck am I doing wrong? Or is there some command which the autoplay function off completely? That's really what I want to do.

---

### Post by ethanay on 2008-05-18
system > preferences > main menu

scroll down and select "preferences" and check the box next to "file management" on the right in order to display it

for future reference, you can also get to the main menu editor by right clicking on the ubuntu menu and selecting "edit"

---

