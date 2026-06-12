---
title: "no problems, just a story and some questions"
date: 2009-01-15
forum: General Help
---

### Post by standingchair on 2009-01-15
Hello Ubuntu Forums, 
I have a couple of questions about my set up - and it involves a a bit of a story too!

I broke my old laptop. I figured out it was the hard drive that was physically damaged, because it booted but it didn't load the OS.

So I made a Live CD of Ubuntu 8.10, popped it in the drive and it worked (confirming earlier suspicions,) but I couldn't get it installed, due to the lack of a hard drive.

So I created a Live Session USB with persistence, thinking I could maybe use this as a functional computer.

It worked - then I took another USB thumbdrive (16 GB) plugged it into the other slot, and installed Ubuntu 8.10 to that.

And that's what I running from now. Ubuntu 8.10 from a 16GB USB thumb drive.

Now some questions.

Is it true that I can now take this drive anywhere, and have my computer in  my pocket? Will Ubuntu automatically download the drivers needed on other computers?

Was there a way I could have installed Ubuntu to the original USB drive it was on? Installed it to itself?

If I forgot to ask myself any questions, feel free to ask for me:D

Jenn

---

### Post by 5BallJuggler on 2009-01-15
> **standingchair said:**
> 

Is it true that I can now take this drive anywhere, and have my computer in  my pocket? Will Ubuntu automatically download the drivers needed on other computers?

Was there a way I could have installed Ubuntu to the original USB drive it was on? Installed it to itself?

If I forgot to ask myself any questions, feel free to ask for me:D

Jenn

I can answer your 1st question, Yes!
the fact that you created a persistance drive means you can use it any where...
....or anywhere that it will be recognised.
as for downloading the drivers, I don't think it will, 
eg your system will have created a xorg.conf file for your laptop/PC, if you download drivers for another PC then it may mean that you stop it working on yours, Ubuntu will find a way to run in failsafe on most systems, so there should be no need.
As for updates, that's another matter, if they are available I'd download and install them, it's the same as being at home.

the 2nd question is a bit more tricky for me.
you would probably have needed to partition the USB, if you can do that, I see no reason you cant install it to itself, but I think that the way you have gone about it is better anyway.

please bear in mind that i'm relatively new to linux and ubuntu too, the information above might not be 100% correct, but it's what i'm led to believe.

Hope it helps.

Phil

---

### Post by standingchair on 2009-01-16
Hi Phil, 
Thanks for looking at my posts, I appreciated your advice on my other issue earlier yesterday - every piece of info help as I know very little.

I know I can take my persistence drive anywhere, but can I take the USB that has Ubuntu actually installed anywhere to?

Linux is a awesome, I just got a very nice theme installed, and my desktop is shaping up nicely =)
Jenn

---

### Post by 5BallJuggler on 2009-01-16
It sounds like both of your drives are persistant, the easiest way to check is make a small change to your desktop, ie had another workspace and then shutdown.
if you log back in and the change you made is still there then the drive is updatable(persistant)

So in answer to your question, if both drives are persistant then you can take them both anywhere.

Post a picture of your desktop, it's always nice to see what other have done.

---

### Post by redilyn on 2009-01-16
> 
I know I can take my persistence drive anywhere, but can I take the USB that has Ubuntu actually installed anywhere to?


If I understand your setup correctly you can take the liveusb with you anywhere since it is essentially a the same as a livecd and use it on any computer that supports booting from usb.

However you probably will not be able to use the 16GB usbkey to run ubuntu on other computers because ubuntu is installed on it and it is setup for the laptops hardware. I could be wrong on this as I've never tried myself.

---

### Post by mixmaster on 2009-01-16
A (persistent) USB version of the Live CD should boot and run on any machine you could install linux onto.

I don't understand this question: "Was there a way I could have installed Ubuntu to the original USB drive it was on? Installed it to itself?"

you already had a running Ubuntu on this USB.

---

### Post by redilyn on 2009-01-16
> 
I don't understand this question: "Was there a way I could have installed Ubuntu to the original USB drive it was on? Installed it to itself?"


The question was, "can I install ubuntu to the same usbkey that liveusb is setup on."

The answer is, yes - but we are past that point now.

---

### Post by standingchair on 2009-01-16
> **redilyn said:**
> The question was, "can I install ubuntu to the same usbkey that liveusb is setup on."

The answer is, yes - but we are past that point now.

Hi Redilyn, 

It's a bummer that I can't use my 16GB install as my pocket OS, but this only makes me want to get an Eee PC even more:D

For next time, how would I do it? Could you point me to a site/thread/etc where I could find more information?
I didn't have any luck with Google.
Is it something along the lines of creating a separate partition?

Thank you!
Jenn

---

### Post by redilyn on 2009-01-16
Atually, i you wanted to use the 16GB as a pocket os, you would just have to boot the ubuntu livecd or a dedicated install and choose Administration -> Create a USB startup disk and then install the ubuntu OS to the flash key, pretty much the same as you did before.

I would try the install you have on the 16GB USB on another computer and see if it will work.

---

### Post by lavinog on 2009-01-17
I don't see why you cant use the installed 16g flash on any computer.
The setup is generic so it should work on any computer that doesn't need alot of tweaking with a normal install. (wireless may not work and you wont be able to use custom xorg.conf files)
The xorg.conf file should be blank by default i think since X automatically detects which driver to use on each startup.

Another limiting factor will be that there are still many computers that don't like to be booted by usb. My laptop and one of my desktops can boot just fine, but my newest gigabyte board isn't playing well.

Does the 16g boot faster than the live usb?
I wish I had the $ to get a 16g flash.

---

### Post by standingchair on 2009-01-17
Redilyn, I tried that using my live cd but it didn't work.

"The xorg.conf file should be blank by default i think since X automatically detects which driver to use on each startup."

So the installation is a blank slate? I should be able to load my installation on "any" computer and if all goes well I should be up and running. Maybe minus the internet, but that's ok. I could still carry around my files and system.

What could happen if it doesn't boot from the USB? Could it damage my computer in anyway? I start school in a few days, and I'd like to have a working computer to distract me from my studies.

"Does the 16g boot faster than the live usb?"

No, it has to load the kernel and that takes sometime. 
The boot time all in all is pretty bad, but you also have to take into account my system.

16GB isn't that expensive, and I actually feel I could have gone with 8 and have been fine. This is what I'm using.
[http://www.microcenter.com/single_product_results.phtml?product_id=0281032](http://www.microcenter.com/single_product_results.phtml?product_id=0281032)

---

### Post by redilyn on 2009-01-17
> 
What could happen if it doesn't boot from the USB? Could it damage my computer in anyway?


Nope, you just won't be able to boot from the usb key.

---

### Post by standingchair on 2009-01-17
Ok, 16GB install works on my Toshiba Satellite A305-s6829 - no real problems. 
I can get on the internet, and surprisingly I didn't need any drivers and such.

This leads to my next question though. 
All my settings/downloads are on here. I have Emerald theme manager installed, running compiz fusion. But, I can't get the cube to work. All the settings are good in the manager and appearance - everything is enabled but no cube.
Any one know how to fix, or the reason behind this? Does it have to do with the xorg.conf file?
Thanks 
Jenn

---

### Post by lavinog on 2009-01-18
> **standingchair said:**
> 
All my settings/downloads are on here. I have Emerald theme manager installed, running compiz fusion. But, I can't get the cube to work. All the settings are good in the manager and appearance - everything is enabled but no cube.
Any one know how to fix, or the reason behind this? Does it have to do with the xorg.conf file?
Thanks 
Jenn
most likely, depending on the video card...not all cards are supported by the standard drivers.
Many ATI and nVidia cards require their proprietary drivers to use compiz.
but adding the proprietary drivers might (but not sure) prevent the flash install from booting properly on non ATI/nVidia systems.
Edit: but if the rest of the effects are working, then the problem is that cube is disabled by default. you have to install the compizconfig settings manager

---

### Post by standingchair on 2009-01-18
On my other computer, the one with no hard drive, the drivers were installed automatically and the cube worked. Now, when I try my install on my Toshiba, no drivers are needed, and no cube. But, i think it's because I don't have a ATI card as I did on my other laptop) or an nVIDIA card on the Toshiba, I  only  have a Mobile Intel® Graphics Media Accelerator X3100 - which probably explains it. 

It's ok, I'm happy, I have a pocket OS I can take around with me and modify. The cube was just an extra piece of eye candy.

I'm trying to learn how to use the terminal now and I have some more questions on themes and stuff - but I'll start a separate thread. 
Thanks for all your help, 
J

---

