---
title: "Compiz &quot;Unsupported&quot; (As well as Unity)"
date: 2011-06-10
forum: Desktop Environments
---

### Post by drgame93 on 2011-06-10
Okay, So on my PC I previously had 10.04 LTS Installed, and I was able to use Compiz perfectly fine with my proprietary **Nvidia** driver. I later upgraded to 10.10, and I still had no issues with my drivers (or hardware). As of right now I'm using 11.04 and Compiz says that my graphics driver is unsupported. Essentially it says I cannot use Compiz at all.

However, I ran the command *compiz --replace* and it began enabling the features i had chosen, and I was able to see the wobbly windows work, but then I was unable to move the windows. All of them went to the upper right hand corner and were stuck. The terminal seemed to have frozen, but I was still able to use everything else. I was even able to turn on unity and use it, but no icons showed up on the left side of the screen (I was able to click them however, and their names showed up as well.)

After attempting this, I decided to forcefully load Compiz, AND Unity when logging in...

And when I logged in the entire gnome shell disappeared and all that was left were my icons. Luckily I had placed icons of Terminal and Chromium on my desktop, so I was able to reverse the changes.

So, I guess my question is, Why can't I use compiz, even though I was able to previously?

Any help would be greatly appreciated.

P.S. Yes I HAVE used google. And I realise there are some issues with Nvidia drivers and other parts (i.e. Plymouth)

---

### Post by sent17inel on 2011-06-10
compiz and unity dont play well together.

---

### Post by drgame93 on 2011-06-10
Well I would be fine with one or the other, Unity seems pretty interesting to be;something new to use on my Ubuntu experience. But I do love the effects of Compiz, it made everything work "better" (I don't know how to describe what I meant, I guess I just like it.)

So is there any way to turn on one or the other? 

I ran the tests and they said Unity and Compiz werent supported, but compiz was at one time.

---

### Post by sent17inel on 2011-06-10
[http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/](http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/)

---

### Post by drgame93 on 2011-06-10
Well, thats nice and all, but I dont have EITHER in use. Thanks for the possible future help though, one of the main compiz settings I love is the desktop cube.

---

### Post by coffeecat on 2011-06-11
> **sent17inel said:**
> compiz and unity dont play well together.

Um, Unity is a compiz plugin. Your posted link about problems with the desktop cube is well-known. It's because Unity needs the desktop wall and the cube needs desktop wall disabled - as the link describes. It's just an example of some compiz plugins being incompatible with each other, although there's a workaround for the cube.

But to the OP's problem...

@drgame93, with 11.04 and nvidia cards you have a choice between the proprietary nvidia driver or an experimental package to complement the open source nouveau driver in order to get 3d acceleration needed for Unity. Both work well with my particular nvidia card, but I have read that some nvidia cards have been problematic.

Some questions. Did you upgrade from 10.10 to 11.04 or did you make a fresh install? If you upgraded I believe the proprietary nvidia driver would have been disabled and you can't get Unity with the nouveau driver unaided by the experimental package. Have you looked in Jockey (Additional Drivers)? What does that say? Lastly, what nvidia card do you have?

---

### Post by drgame93 on 2011-06-11
Well had some issues with 10.10 connecting to my usb wireless adapter, so I did a fresh install of 11.04.

I checked the additional drivers and it showed that I could install the proprietary driver, and the experimental 3d driver. I activated both. 

But now I only have the main option, and it says that the driver is activated but not in use.

My card is: nVidia Corporation NV34 [GeForce FX 5100] (rev a1)

Yes, I do have an old PC (Its like 7 years old now).

---

### Post by VOT Productions on 2011-06-11
Are Window Decorations on? If not, turn them on. Also, you can move windows with ALT if you have no title bar.

---

### Post by drgame93 on 2011-06-11
> **VOT Productions said:**
> Are Window Decorations on? If not, turn them on. Also, you can move windows with ALT if you have no title bar.

Yeah, but I no longer have those issues, right now I just need to enable compiz, and then hopefully Unity.

---

### Post by coffeecat on 2011-06-11
> **drgame93 said:**
> My card is: nVidia Corporation NV34 [GeForce FX 5100] (rev a1)

@drgame93, see which nvidia driver has been activated. If it's what Additional Drivers calls "version current", that won't support your card. You need the "version 173" nvidia driver for the GeForce series 5.

---

### Post by drgame93 on 2011-06-11
It says Version 173 [Recommended].

Edit: After uninstalling compiz and my main driver, I could not do anything, so i decided since the install was only a wubi Install, I would start fresh with a full install. I have now re-installed natty, and my nvidia driver was installed already. So I loaded clasic ubuntu. I then decided to try the "Ubuntu" option, and then nothing showed up. It showed my external hdd, and a message saying I connected to my network, but that was it, and it flickered every two seconds. I am more confused now than previously.

EDIT 2: Ok so I downloaded ccsm, and I activated wobbly windows! (YAY) And they worked... until I decided I wanted to enable the Unity Plugin... Now I have to fully rely on the "move windows" "window decorations" plugins, to even see and use my windows... I guess I need even more help, just to restore compiz to working order.

Edit 3: Everything now works, but after the most recent Unity craziness Im not sure what will happen. Thanks for your help everyone. I'm glad to see that there are people willing to help in this community.

---

### Post by wildmanne39 on 2011-06-11
> **drgame93 said:**
> It says Version 173 [Recommended].

Edit: After uninstalling compiz and my main driver, I could not do anything, so i decided since the install was only a wubi Install, I would start fresh with a full install. I have now re-installed natty, and my nvidia driver was installed already. So I loaded clasic ubuntu. I then decided to try the "Ubuntu" option, and then nothing showed up. It showed my external hdd, and a message saying I connected to my network, but that was it, and it flickered every two seconds. I am more confused now than previously.

EDIT 2: Ok so I downloaded ccsm, and I activated wobbly windows! (YAY) And they worked... until I decided I wanted to enable the Unity Plugin... Now I have to fully rely on the "move windows" "window decorations" plugins, to even see and use my windows... I guess I need even more help, just to restore compiz to working order.

Edit 3: Everything now works, but after the most recent Unity craziness Im not sure what will happen. Thanks for your help everyone. I'm glad to see that there are people willing to help in this community.

Hi, first let fix your problem and then we can get the cube working,use these instructions to get your system back to working. Click on reset unity or compiz in my signature below this text and follow the instructions. To get the cube working use the link.
[http://ubuntu4beginners.blogspot.com...ty-ubuntu.html](http://ubuntu4beginners.blogspot.com...ty-ubuntu.html)
after you have finished with this guide and you change other settings it will mess up you windows again so just log out and back in and they will be fixed. This guide is for unity when you are logged in as ubuntu, and I know it works I have the nvidia 173 driver and cube with a lot of effects. You are using classic I think the reason your windows will not move is you go into ccsm and type move windows in the filter box and click on move windows in classic it is disabled by default, the cube actually works better in unity then classic when set up properly.

---

