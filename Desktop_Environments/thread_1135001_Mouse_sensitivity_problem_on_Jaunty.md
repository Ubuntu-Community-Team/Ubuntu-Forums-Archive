---
title: "Mouse sensitivity problem on Jaunty"
date: 2009-04-24
forum: Desktop Environments
---

### Post by MeanEYE on 2009-04-24
After upgrading I've noticed that my mouse is slightly faster than usual. Faster enough to make my regular work day a living nighmare.

Now I tried configuring from System -> Preferences -> Mouse but those controls dont seem to work properly. But I had problems with those before update. The way I use to set mouse sensitivity in previous version was with xset. Now this doesn't work either...

Any ideas?

Oh yes, important thing is... I have Toshiba U400-12R and Logitech VX Nano. So this means I have two pointing devices.

Like I said, everything worked before or at least I was able to configure speed. Now I can't... I didnt play with xorg.conf file and I'd like to leave that as a last resort thing...

Thanx!

---

### Post by Mishootka on 2009-04-25
same problem on Aspire One 150, Jaunty, Genius 355 USB Laser mouse.
sensitivity is uncontrollably high so mouse moves very fast.  
synaptics works fine.

xset m[ouse] doesnt help.

---

### Post by simoncullen on 2009-04-25
Same problem.  I'm using an Evoluent Vertical mouse 3, very high resolution optical sensor.  The Xorg configuration file now says: 

# commented out by update-manager, HAL is now used
#Section "InputDevice"

I don't seem to be able to set the resolution of the mouse anywhere.  This is really frustrating.

---

### Post by MeanEYE on 2009-04-27
Seems to me the proper way to set mouse sensitivity is through hal. Hal has policy files in /etc/hal/policy which are suposed to set that... 

Am gonna research a bit on that matter!

---

### Post by simoncullen on 2009-04-27
> **MeanEYE said:**
> Seems to me the proper way to set mouse sensitivity is through hal. Hal has policy files in /etc/hal/policy which are suposed to set that... 

Am gonna research a bit on that matter!

This sorted it out for me!

Cheers

Simon

```
simon@aristurtle:/etc/hal/fdi/policy$ cat 99*
::::::::::::::
99-x11-mouse.fdi
::::::::::::::
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
        <match key="info.capabilities" contains="input.mouse">
        <merge key="input.x11_driver" type="string">evdev</merge>
        <match key="/org/freedesktop/Hal/devices/computer:system.kernel.name" string="Linux">
             <merge key="input.x11_driver" type="string">mouse</merge>
               <merge key="input.x11_options.Sensitivity" type="string">.2</merge>
               <merge key="input.x11_options.Device" type="string">/dev/input/mice</merge>
               <merge key="input.x11_options.Resolution" type="string">1200</merge>
               <merge key="input.x11_options.SampleRate" type="string">800</merge>
               <merge key="input.x11_options.Protocol" type="string">IMPS/2</merge>
        </match>
    </match>

  </device>
</deviceinfo>
```

---

### Post by MeanEYE on 2009-04-27
Found something that might help... I did mess around a little but more when I find some time!

[Creating fdi policy files for HAL]("http://www.chineselinuxuniversity.net/articles/21232.shtml")

---

### Post by MeanEYE on 2009-04-27
> **simoncullen said:**
> This sorted it out for me!

Cheers

Simon

```
simon@aristurtle:/etc/hal/fdi/policy$ cat 99*
::::::::::::::
99-x11-mouse.fdi
::::::::::::::
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
        <match key="info.capabilities" contains="input.mouse">
        <merge key="input.x11_driver" type="string">evdev</merge>
        <match key="/org/freedesktop/Hal/devices/computer:system.kernel.name" string="Linux">
             <merge key="input.x11_driver" type="string">mouse</merge>
               <merge key="input.x11_options.Sensitivity" type="string">.2</merge>
               <merge key="input.x11_options.Device" type="string">/dev/input/mice</merge>
               <merge key="input.x11_options.Resolution" type="string">1200</merge>
               <merge key="input.x11_options.SampleRate" type="string">800</merge>
               <merge key="input.x11_options.Protocol" type="string">IMPS/2</merge>
        </match>
    </match>

  </device>
</deviceinfo>
```

Yay, works for me too... I have logitech VX Nano for my laptop and G9 for desktop PC :)...

---

### Post by Lester_Burnham on 2009-05-15
Thanks,

Fixed my Toshiba laser retractable cord version too.

Lester

---

### Post by pcollins on 2009-08-12
I'm having the same issue on both my Jaunty desktop as well as my Jaunty laptop.

My next computer is going to be a Mac. I've been using GNU/Linux for about ten years, and I'm done.

---

### Post by MeanEYE on 2009-08-13
> **pcollins said:**
> I'm having the same issue on both my Jaunty desktop as well as my Jaunty laptop.

My next computer is going to be a Mac. I've been using GNU/Linux for about ten years, and I'm done.

Why do you apple fans always have to brag about macs? This is Ubuntu forum. We are here either to get or provide help, not to listen to whining kids.

I might be trolling here but am kinda sick of it. If ubuntu made it's own brand of computers wouldn't you think they would have perfect drivers for it? I like ubuntu exactly the way it is. You just go ahead and buy over-expensive intel wrapped in a white plastic design of a brick. I'll stay here and help everyone who wants this system :)...

Have fun, kay?

p.s.

If in that period of "about ten years" you haven't managed to get a grip on how to configure your Linux, then you really need to use Mac!

---

### Post by pcollins on 2009-08-16
> **MeanEYE said:**
> Why do you apple fans always have to brag about macs? This is Ubuntu forum. We are here either to get or provide help, not to listen to whining kids.

I might be trolling here but am kinda sick of it. If ubuntu made it's own brand of computers wouldn't you think they would have perfect drivers for it? I like ubuntu exactly the way it is. You just go ahead and buy over-expensive intel wrapped in a white plastic design of a brick. I'll stay here and help everyone who wants this system :)...

Have fun, kay?

p.s.

If in that period of "about ten years" you haven't managed to get a grip on how to configure your Linux, then you really need to use Mac!

Thanks for the "help" there chief.

Just about every sentence in your post betrays you as a poser.

This is not a driver issue. It's a configuration issue that affects every single Jaunty machine in use today. This has been a known issue for months and nothing has been done about it.

Lots of folks, experienced developers included, have a limit to how much they're willing to cut and paste config changes they find on the Web and hope for the best, to get basic features of their machines to work.

Linux on the desktop is a mirage: you seem to make progress but you never get closer to the goal. Every release of Ubuntu, and they're better at desktop Linux than anyone else, fixes 25 fundamental problems and introduces 25 new ones.

One more thing. "It's" is a contraction of "it is". When you try to insult someone, don't let people know you can't pass the third grade.

---

### Post by MeanEYE on 2009-08-25
> **pcollins said:**
> Thanks for the "help" there chief.

Just about every sentence in your post betrays you as a poser.

This is not a driver issue. It's a configuration issue that affects every single Jaunty machine in use today. This has been a known issue for months and nothing has been done about it.

Lots of folks, experienced developers included, have a limit to how much they're willing to cut and paste config changes they find on the Web and hope for the best, to get basic features of their machines to work.

Linux on the desktop is a mirage: you seem to make progress but you never get closer to the goal. Every release of Ubuntu, and they're better at desktop Linux than anyone else, fixes 25 fundamental problems and introduces 25 new ones.

One more thing. "It's" is a contraction of "it is". When you try to insult someone, don't let people know you can't pass the third grade.

Me, a poser? OK troll if you say so... Because it is obvious that you are a troll since in last 2 years you made 2 posts on this forum and both of them were in this thread. Anyway I don't care.

You still didn't have to brag about buying a Mac and honestly I don't think many users from ubuntu forums care at all. 

As far as "passing the third grade" is concerned, English is not my native language. And many users of this forum share the same fact. If you are trying to turn this thread in something more than mouse sensitivity issue discussion please stop doing so. 

Go troll somewhere [else]("http://www.disney-forums.com/")...

---

### Post by Brad54 on 2009-10-08
PCCollins and Meaneye. Go simper on AOL this is about a mouse issue. Am using Jaunty and have had mouse lag issue not seen in fresh jaunty install. I had been playing w. compiz (uninstalled) and Tor w. vidalia (uninstalled). Lag seen in firefox not seen using openOffice. Hmmm.

---

### Post by Brad54 on 2009-10-08
I tried using epiphany web browser and Open Office. The lag seems to dissapear when I'm not using Mozilla Firefox. No lag using epiphany. How odd. Maybe I'll export my bookmarks, and uninstall firefox followed by a fresh install.

---

### Post by MeanEYE on 2009-10-08
> **Brad54 said:**
> I tried using epiphany web browser and Open Office. The lag seems to dissapear when I'm not using Mozilla Firefox. No lag using epiphany. How odd. Maybe I'll export my bookmarks, and uninstall firefox followed by a fresh install.

That is really odd. Am not sure how Firefox affects mouse behavior. 

Please note that by removing Firefox you don't actually remove local settings. They are located in ~/.mozilla/firefox. 

I would suggest trying to backup and remove that directory first, before removing Firefox from your computer. It's possible that some of your add-ons or local settings are causing the lag.

---

### Post by suzenon on 2009-11-04
> **simoncullen said:**
> This sorted it out for me!

Cheers

Simon

```
simon@aristurtle:/etc/hal/fdi/policy$ cat 99*
::::::::::::::
99-x11-mouse.fdi
::::::::::::::
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
        <match key="info.capabilities" contains="input.mouse">
        <merge key="input.x11_driver" type="string">evdev</merge>
        <match key="/org/freedesktop/Hal/devices/computer:system.kernel.name" string="Linux">
             <merge key="input.x11_driver" type="string">mouse</merge>
               <merge key="input.x11_options.Sensitivity" type="string">.2</merge>
               <merge key="input.x11_options.Device" type="string">/dev/input/mice</merge>
               <merge key="input.x11_options.Resolution" type="string">1200</merge>
               <merge key="input.x11_options.SampleRate" type="string">800</merge>
               <merge key="input.x11_options.Protocol" type="string">IMPS/2</merge>
        </match>
    </match>

  </device>
</deviceinfo>
```

what name of this file starts with 99? will it work if i will name it like "whatever.fdi"?

---

### Post by MeanEYE on 2009-11-04
> **suzenon said:**
> what name of this file starts with 99? will it work if i will name it like "whatever.fdi"?

It should. I think every fdi file is read from that directory. But am not sure about this. It's only my opinion. That's the way I would :D program it to work :)

---

### Post by suzenon on 2009-11-05
damn, noticed now i wrote "what" instead of "why" - sorry :(

well... since i don't see much entries in xorg.conf i guess new ubuntu 9.10 is using these fdi files, so i'm considering making one for my razer mice

just wonders if this number at the beginning of file has anything to do on how ubuntu will or won't use it

---

### Post by MeanEYE on 2009-11-05
> **suzenon said:**
> damn, noticed now i wrote "what" instead of "why" - sorry :(

well... since i don't see much entries in xorg.conf i guess new ubuntu 9.10 is using these fdi files, so i'm considering making one for my razer mice

just wonders if this number at the beginning of file has anything to do on how ubuntu will or won't use it

I think you can name file anything you want but I've put config for my Logitech G9 in preferences.fdi file. So if everything else fails ;) you can do it like that...

---

