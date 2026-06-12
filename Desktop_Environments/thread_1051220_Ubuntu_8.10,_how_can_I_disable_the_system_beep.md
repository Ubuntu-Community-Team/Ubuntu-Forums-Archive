---
title: "Ubuntu 8.10, how can I disable the system beep?"
date: 2009-01-26
forum: Desktop Environments
---

### Post by mesh2005 on 2009-01-26
I checked System->Preferences->Sound but I couldn't find anything there?

---

### Post by snova on 2009-01-26
The way I do it is to unload the driver for the device itself.

Open the /etc/modprobe.d/blacklist file:

```
gksudo gedit /etc/modprobe.d/blacklist
```

And add this line to the end of it:

```
blacklist pcspkr
```

This will take effect the next time you reboot.

For the time being, though, you can issue this command to unload it immediately:

```
sudo rmmod pcspkr
```

---

### Post by Linuxdork on 2009-01-26
Well, I know you can disable it from doing it in gnome-terminal.  Edit > Current Profile... > General (Tab) and uncheck the Terminal Bell box.

---

### Post by paulchinnz on 2009-01-27
I tried the terminal bell box but system beep is still going.  Are there any other options besides unloading the driver?

---

### Post by Linuxdork on 2009-01-27
What are you doing on the system when the beep occurs?

---

### Post by mtbsoft on 2009-01-28
> **mesh2005 said:**
> I checked System->Preferences->Sound but I couldn't find anything there?
Are you not seeing two tabs - Devices and Sounds?  The Sounds tab has the options Play Alerts And Sound Effects and Play Alert Sounds - I have both disabled.  I also have the System|Power Management|General|Use sound to notify in event of error option disabled.  If you have Compiz enabled you should also disable General Options|General|Audible Bell.  I don't get any beeps or other noises with these settings.

Actually, the System|Log Out and System|Shutdown are the two events which don't seem to honour these settings... both subsequent screens beep when you select an action but I can (just) live with that... by not using them.

Edit: finally found it... Also in Compiz|Fading Windows has two options to give you a visual indicator when the bell should beep, Visual Bell and Fullscreen Visual Bell - the screen/window will blink briefly instead of the beep

---

### Post by Linuxdork on 2009-01-28
[IMG]http://img149.imageshack.us/img149/2696/screenshotsoundpreferenur1.png[/IMG]

If you uncheck that it should work.

---

### Post by mtbsoft on 2009-01-28
> **Linuxdork said:**
> If you uncheck that it should work.
I'm curious, what version are you running, because I don't get that third tab in 8.10?

---

### Post by Linuxdork on 2009-01-28
8.04 Hardy

---

### Post by Linuxdork on 2009-01-28
If you don't have that tab you can probably disable it in gconf.

```
gconf-editor
```

do a search for bell and select this option: /apps/metacity/general/audible_bell

Then remove the check there.  I believe that will work.

---

### Post by ShoeYork on 2009-02-03
> **Linuxdork said:**
> If you don't have that tab you can probably disable it in gconf.

```
gconf-editor
```

do a search for bell and select this option: /apps/metacity/general/audible_bell

Then remove the check there.  I believe that will work.

This just worked for me, but I'm curious as to why I don't have that third tab in sound preferences. I'm using 8.1.

---

### Post by Azure.Rise on 2009-02-12
The third tab was removed in 8.10, although I don't know why.

---

### Post by kikazaru on 2009-03-06
I was still getting a beep out of gedit... which gave me heart attacks when wired for sound. The shock was exacerbated due the otherwise silent environment.

I found and unticked (based on gconf editor tip above)

compiz
  general
    all
      screens
        options
          audible bell

---

### Post by chakoshi on 2009-03-06
the best method is the one snova mentioned: unload the driver for the device:

sudo rmmod pcspkr

and to make it permanently disabled:

And add "blacklist pcspkr" to the end of  /etc/modprobe.d/blacklist file

---

### Post by kaivalagi on 2009-03-06
You could just disconnect the pc speaker (if you have a desktop pc)

I dont even have one, there's no need

---

### Post by Potters Son on 2009-04-06
```
I dont even have one, there's no need
```

Not true. I have a laptop, and the pc speaker gets routed through my main speakers (MAN, is it annoying). Well, I'm running 9.04 beta, and the tab is STILL missing (where, oh where has that little tab gone?) Moreover, why would it ever get removed?

I don't know what I would use the PC speaker for, but I feel uncomfortable disabling it. Who knows? I might miss it down the road, but by that time I will have forgotton how I disabled it.

---

### Post by alanhoyle on 2009-05-04
I'm also running 8.10.  Is there a way to force the system bell to trigger a digitized sound?  it seems that the gconf-editor  /apps/metacity/general/audible_bell setting is linked in with the Sound Preferences::Sounds :: Play alert sound setting.  

What I want is for the thing to beep through the speakers rather than triggering the nasty PC speaker bell.  I've also disabled the speaker through the kernel blacklist, but that still doesn't do what I want it to.  I don't want complete silence, I want a subtle audible clue that I can change the volume of using my volume control.

---

