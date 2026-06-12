---
title: "Compiz Cube rotation slow in 10.04 with Firefox"
date: 2010-05-19
forum: Desktop Environments
---

### Post by durzagott on 2010-05-19
I have recently done a clean install of Lucid Lynx and set everything up the way I had it in Jaunty (skipped Karmic). However, I am now having problems with the Compiz Cube and Firefox 3.6.

Whenever I rotate my workspace that contains a Firefox window that is active, the animation is very jerky and slow. It is fine if Firefox is a background window. This was never a problem in Jaunty with Firefox 3.0.

Is anyone else having this problem? Does anyone know how I might be able to fix it? I have tried disabling all addons in Firefox.

My PC: Core 2 Duo E7400, Geforce 7010 (onboard), 2GB RAM

UPDATE: starting Firefox in Safe Mode seems to help a little. Not sure why though...

---

### Post by lovinglinux on 2010-05-19
> **durzagott said:**
> UPDATE: starting Firefox in Safe Mode seems to help a little. Not sure why though...

It could be an extension that draws some overlay like the Ghostery bubble. BTW, if you have Ghostery 2.1.1, then update to get get 2.1.2, since it was causing serious Firefox slowdown.

Additionally, check my [optimization tutorials]("http://firefox-tutorials.blogspot.com/").

---

### Post by durzagott on 2010-05-19
> **lovinglinux said:**
> It could be an extension that draws some overlay like the Ghostery bubble. 

I don't use Ghostery, but thank you for the suggestion. The only Addons I have at the moment are: Adblock Plus, Xmarks, Download Statusbar, and Ubuntu Firefox Modifications.

Disabling all of these doesn't seem to help, but starting up in safe-mode does make a difference.  Or if Firefox is a background window.

UPDATE: It looks like I was wrong about safe-mode. I still get exactly the same behaviour when rotating the cube in both normal-mode and safe-mode. It only seems to be Firefox as well. None of my other applications are causing a problem, including other browsers like Chrome.

---

### Post by lovinglinux on 2010-05-19
> **durzagott said:**
> I don't use Ghostery, but thank you for the suggestion. The only Addons I have at the moment are: Adblock Plus, Xmarks, Download Statusbar, and Ubuntu Firefox Modifications.

Disabling all of these doesn't seem to help, but starting up in safe-mode does make a difference.  Or if Firefox is a background window.

UPDATE: It looks like I was wrong about safe-mode. I still get exactly the same behaviour when rotating the cube in both normal-mode and safe-mode. It only seems to be Firefox as well. None of my other applications are causing a problem, including other browsers like Chrome.

Create a new profile with Firefox profile manager and test it, so we can exclude (or not) anything inside your profile as culprit:

```
firefox -P
```

---

### Post by durzagott on 2010-05-20
I created a new profile and sadly I am still experiencing exactly the same behaviour. It seems to get worse depending on the current active page in Firefox. For example, if I have this forum page open, then the problem is very noticeable. However, I have I Google's homepage open then it's absolutely fine.

Firefox doesn't seem to consume any extra resources though. It holds steady at around 100MB of RAM and 2% of CPU no matter which page I am on.

---

### Post by lovinglinux on 2010-05-20
> **durzagott said:**
> I created a new profile and sadly I am still experiencing exactly the same behaviour. 

I wasn't expecting it to fix the problem, I just wanted to make sure.

> **durzagott said:**
> It seems to get worse depending on the current active page in Firefox. For example, if I have this forum page open, then the problem is very noticeable. However, I have I Google's homepage open then it's absolutely fine.

Firefox doesn't seem to consume any extra resources though. It holds steady at around 100MB of RAM and 2% of CPU no matter which page I am on.

I have no idea why this is happening, but I'm going to suggest an experiment. Keep in mind I'm shooting in the dark:

Go to Firefox Preferences and disable javascript in the Content tab. Test the cube. Enable javascript again.

Go to Firefox Add-ons manager and disable the "Ubuntu Firefox Modifications" extension, restart Firefox and then test the Cube. Enable the extension again.

Go to Compiz Config Settings Manager and disable Gnome integration/support or something like that. Test the cube. Enable the integration again.

---

### Post by durzagott on 2010-05-20
Drats, I thought I had it cracked. I tried doing the types of things you suggested and went in the CompizConfig Settings Manager and tweaked some options. My cube rotation was looking really sweet, then I realised that the Settings Manager was still the active window. As soon as Firefox became the active window again the jerky motion returned.

I guess I'll just keep tweak stuff until I stumble upon the right setting. Oh well, thanks for taking the time to reply to my questions, lovinglinux. It's definitely appreciated!

---

### Post by lovinglinux on 2010-05-20
> **durzagott said:**
> Drats, I thought I had it cracked. I tried doing the types of things you suggested and went in the CompizConfig Settings Manager and tweaked some options. My cube rotation was looking really sweet, then I realised that the Settings Manager was still the active window. As soon as Firefox became the active window again the jerky motion returned.

I guess I'll just keep tweak stuff until I stumble upon the right setting. Oh well, thanks for taking the time to reply to my questions, lovinglinux. It's definitely appreciated!

You are welcome. Sorry I couldn't help you any further. I don't even use Compiz anymore, since I use KDE with Kwin now and I don't now much about graphic stuff. I stumbled into your thread because I was looking to help users with Firefox problems. Unfortunately, this is definitely above my skills.

---

### Post by Cajhne on 2010-07-22
I'm having a similar issue with Lucid and Compiz, and found out that the "mipmap" option was bogging down the rotation. I turned that off under "Desktop Cube" in Compiz. Makes sense... I'm not sure why you'd need mip-mapping for a cube rotate. Surely dynamically creating mipmaps for everything (on every desktop) in real-time on the screen is going to take WAY more processor time than just handing the lot to your graphics card to interpolate from full-res (actual) window render data. Not like there's anything else in your 3D desktop world. :) If your cube rotate zooms out far enough for real-time mipmapping to make a difference, well, there's nothing else to render, out there... just a skybox if you have one set up.

It's an isolated, lonely desktop cube world, yessir. Luckily, this makes your graphics processor verah happah. :D

---

### Post by CatmanTiger on 2011-04-24
I had the same problem.  But solved after doing this.
Rotate desktop cube > snap to bottom face > speed = 1.67
In your case It should be below that.:smile:  In my case not related to firefox

---

