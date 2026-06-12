---
title: "Google Earth"
date: 2009-04-12
forum: General Help
---

### Post by hacker_at_linux on 2009-04-12
Today I installed google earth. First downloaded the package from Synaptic Package Manager and the made the deb file form it.

After successful installation I ran it But it started crashing often and ultimately when I got it to work It showed me some hizzi pics 
I am attaching a screen shot of my desktop Please tell me why is this happening and how to do with it  
[IMG]http://ashmeet.x10hosting.com/Screenshot-5.png

---

### Post by DeMus on 2009-04-12
This almost certain has to do with your graphics card and installed driver. Have look at that.
What card do you have, which driver did you install, did you enable 3D graphics?

---

### Post by hacker_at_linux on 2009-04-12
Well I don;t think so that this is a hardware problem as google earth runs fine in XP

Plus I don't know which display driver is ubuntu using as I was never asked for that ubuntu installed some video driver its self form the net

And lastly how to enable 3D Graphics 



Help

---

### Post by DeMus on 2009-04-12
> **hacker_at_linux said:**
> Well I don;t think so that this is a hardware problem as google earth runs fine in XP

Plus I don't know which display driver is ubuntu using as I was never asked for that ubuntu installed some video driver its self form the net

And lastly how to enable 3D Graphics 



Help

Good, the card used to work fine in Windows. This means it is capable of showing the Google Maps graphics.
Meaning, if it is graphics related, it must be the driver.

First we have to find out what graphics card you use. Is it an nVidia, an ATI or something else? Do you know? Once we know which card you have we can see if you have the right driver.

To find out if you have 3D enabled or not you can simply start a game called Chess. It's in Application - Games - Chess.
Once started go to Settings - Preferences - View and switch on the 3D Chess view. If that works all is well, if not you get an error message.
Write down the names of the two items you are missing, open-up Synaptic Package Manager in System - Administration - Synaptic. Wait for it to load, click on search and type the first of the two names you wrote down. Mark it for installation by clicking on the little square box in front of the name.
Search for the next one and also mark it for installation. Then click on Apply and install the two packages.
Start Chess again, switch on the 3D view as mentioned above and now you should see the chess board in 3D.

---

### Post by hacker_at_linux on 2009-04-12
I have an onBoard Graphic card ie Intel 810 smthing smthing what my XP shows and I installed both the packages that chess game specified.
But still the chess is acting strange 

As I click I returns to 2D mode and as soon as I release the click I is again 3D

Help

---

### Post by DeMus on 2009-04-12
> **hacker_at_linux said:**
> I have an onBoard Graphic card ie Intel 810 smthing smthing what my XP shows and I installed both the packages that chess game specified.
But still the chess is acting strange 

As I click I returns to 2D mode and as soon as I release the click I is again 3D

Help

Good, you have the 3D image of the chess board, more or less.
Can you install a program called Sysinfo? You can do that in Synaptic also. After installation in the menu Applications - System tools you see the launcher.
Start the program and see what it is you have, what kind of graphics card I mean. Tell me please what it says about the Intel graphics.

---

### Post by hacker_at_linux on 2009-04-12
for Graphic card thing it shows :
VGA controller
		Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
		Subsystem: Elitegroup Computer Systems Device 2624
is it a low one ????

---

### Post by DeMus on 2009-04-12
> **hacker_at_linux said:**
> for Graphic card thing it shows :
VGA controller
		Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
		Subsystem: Elitegroup Computer Systems Device 2624
is it a low one ????

Well it can't be a low one since in Windows Google earth accepts it, right? It's also not top of the line but you knew that already. Doesn't have to be.
I have been looking around on the Intel website and if there is one website in the world I hate, it's this one. I never can find what I am looking for. I found your graphics card but no place to download the driver. It says: To download click Download. There is no Download on that page. Where to click? I have no idea.
Maybe you can find it, the address I was looking at is:
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2582&DwnldID=13815&strOSs=39&OSFullName=Linux*&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2582&DwnldID=13815&strOSs=39&OSFullName=Linux*&lang=eng")

Sorry for not being able to help you any further.
I really hope you can get it working. Success.

---

### Post by Lunx on 2009-04-12
If you are running Compiz with extra effects enabled this will often cause GE to not play nicely, try switching to Metacity and give that a try. Also if you get it running but find it very slow and wanting to freeze, try turning off the atmosphere effect in the **View** menu of GE.

---

### Post by hacker_at_linux on 2009-04-12
Thanks Guys worked ouy bt not as well as I thought and as in windows
But over all I am thankful to all of you to reply to me so fats

---

