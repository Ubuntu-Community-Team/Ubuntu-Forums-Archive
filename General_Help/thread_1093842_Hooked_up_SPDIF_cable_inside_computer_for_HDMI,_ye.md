---
title: "Hooked up SPDIF cable inside computer for HDMI, yet Samsung 750 still has no sound?"
date: 2009-03-12
forum: General Help
---

### Post by PsychedelicWonders on 2009-03-12
Ok I just bought a 46" samsung 750

I have it hooked up to my computer via HDMI via HDMI adapter on my Asus video card.

I've hooked up the SPDIF wire to the card & then the mobo...

But yet I have no sound via the tv?

Is there something else that I have to "activate"?

[http://www.newegg.com/Product/Produc...82E16814121242](http://www.newegg.com/Product/Produc...82E16814121242)

That is the card I currently have...

This is the card I will be adding here in about a week (I have 3, 19" monitors and a 46" lcd)

[http://www.newegg.com/Product/Produc...82E16814121268](http://www.newegg.com/Product/Produc...82E16814121268)

Same cards except the new one will be 9800 GT, the one I currently have is only 9600 GT

Here is the mobo:

[http://www.newegg.com/Product/Produc...82E16813131277](http://www.newegg.com/Product/Produc...82E16813131277)

---

### Post by PsychedelicWonders on 2009-03-13
bump

---

### Post by PsychedelicWonders on 2009-03-16
bump

---

### Post by sdennie on 2009-03-16
I use the HDMI out on my laptop all the time but, I'm not sure what SPDIF is.  I thought the point of HDMI was that it's just one wire for both sound and video.  Regardless, to get sound output, I started gnome-volume-control and enabled all the channels/options via Edit->Preferences.  The interesting ones for me were in the Switches tab and labeled IEC958.  Honestly, the solution in this case is likely, "Enable everything and just start pushing buttons until it works".

Note: You will probably also want to have up to date nvidia drivers.

---

### Post by fooman on 2009-03-16
if sdennie's post does not help...

try installing the "gnome-alsamixer":

```
sudo apt-get install gnome-alsamixer
```after it installs,  find it in applications > sound and video

open it and put a check next to IEC958

if that does not work,  then also find the slider for IEC958 P and turn it *all the way down*....see if that works.

---

### Post by PsychedelicWonders on 2009-03-30
> **fooman said:**
> if sdennie's post does not help...

try installing the "gnome-alsamixer":

```
sudo apt-get install gnome-alsamixer
```after it installs,  find it in applications > sound and video

open it and put a check next to IEC958

if that does not work,  then also find the slider for IEC958 P and turn it *all the way down*....see if that works.

The SPDIF cable is what hooks up the mobo to the sound card internally so that it can feed the HDMI cable sound to the tv.

Now I should say this, I havent been able to get sound via windows or Ubuntu through HDMI, so either its not hooked up right inside the computer, or the tv is not set to the proper settings.  

There is a specific Computer/DVI/HDMI port that I must use on Samsungs, which I am using.

Any ideas on how else to test?

I've attached a picture of everything checked,

I just recently had to check a couple of the IEC958's to get my 5.1 to finally work in ubuntu.

What is this IEC958 anyways?

---

### Post by jocko on 2009-03-30
> **PsychedelicWonders said:**
> What is this IEC958 anyways?
iec958 = spdif


And check the links in your first post. They are broken.

---

### Post by norwoods on 2009-03-30
you may have the pins on the cable hooked up backwards.
you may need to enable the internal mobo spdif output in the bios settings.

---

### Post by PsychedelicWonders on 2009-03-30
> **norwoods said:**
> you may have the pins on the cable hooked up backwards.

I will double check this... 

> 
you may need to enable the internal mobo spdif output in the bios settings.

I did not do this... how do I do it?

---

### Post by norwoods on 2009-03-30
> **PsychedelicWonders said:**
> 

I did not do this... how do I do it?
this depends on which motherboard and which bios version you have.  just start the bios when you boot up and search the different menus for anything with spdif in it and try to make sense of it or ask.

---

### Post by PsychedelicWonders on 2009-03-30
> **norwoods said:**
> this depends on which motherboard and which bios version you have.  just start the bios when you boot up and search the different menus for anything with spdif in it and try to make sense of it or ask.

This may sound elementary, but how do I get into bios at boot up...

I have a wireless keyboard, so my F keys dont work for some stuipd reason.

---

### Post by norwoods on 2009-03-30
on my computer the del key brings up bios, but your screen apparently says an f key.  this why answering questions about the bios is difficult at best and you have not even said what motherboard and bios version you have.  if you have a manual, look for spdif in it to see if the bios enables the port.  and i do not have a wireless keyboard so i have no idea why your f keys do not function but you may need to borrow a wired keyboard.

---

### Post by PsychedelicWonders on 2009-03-31
> **norwoods said:**
> on my computer the del key brings up bios, but your screen apparently says an f key.  this why answering questions about the bios is difficult at best and you have not even said what motherboard and bios version you have.  if you have a manual, look for spdif in it to see if the bios enables the port.  and i do not have a wireless keyboard so i have no idea why your f keys do not function but you may need to borrow a wired keyboard.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131277](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131277)

Thats my mobo

I dont know what version bios I am running right now, I will check tonight.

I honestly dont know if its the F keys to enter bios or not, I just assumed that because thats how you usually do it.

When will it tell me what key is used to enter bios?

Before I hit the grub menu right?

There is just something about wireless keyboards not being registered in bios for the F function keys or something I guess...?

---

### Post by norwoods on 2009-03-31
the manual says:
At power on, hold down the <Delete> key to enter the BIOS Setup. 

i do not anything about S/PDIF out being controlled by the bios.

the correct connections for S/PDIF out to a video card are shown on page 2-32

---

