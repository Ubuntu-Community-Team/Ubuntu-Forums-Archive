---
title: "NIGHTMARE attempting to install GBA Emulator."
date: 2008-04-14
forum: Gaming &amp; Leisure
---

### Post by adi116 on 2008-04-14
First off, i'd like to point out that VBA Express seems to have some sort of issue on my computer, as the audio is all choppy and slow, even though i'm running the ROM at around 100%. beyond that, whenever i attempt to close VBA express, it simply freezes the window that i am playing in, it doesn't close it at all. i'm just about done attempting to make VBA express work.

i downloaded the regular VisualBoyAdvance, but whenever i double click on the icon, nothing happens. i can't find it anywhere on the system, but it says that it's installed. i can't even run it through the terminal. so i gave up on it, because i heard about mednafen.

mednafen was no better. i attempted to install it using the deb package, but it's telling me that it couldnt satisfy a dependect on "libasound2." i installed it through the terminal, but do not know how to run it. i type in "mednafen" and it shows me a little script, but nothing actually happens.

what's the deal here? can i get some help, please?:confused::confused::confused::confused:

---

### Post by FranMichaels on 2008-04-14
Install mednafen from synaptic. Remove the one you installed (sounds like it didn't have the dependencies built in.) 

Then right click on your gba rom, go Open With other application, click custom, type 
mednafen (it will remember from now on, this is a one time thing ;) )

From there mednafen will load, just press F1 for the hotkeys.

Then have fun!

Avoid nightmare installs by using what is in the repo first. :) Also, mention where you got the debs, what version it is, etc. Installs should normally be super simple!

---

### Post by adi116 on 2008-04-14
thank you so much! i got it to start working... BUT!

- no sound. :(
- when i attempted to configure sound, i ended up messing up the button mapping, and now the buttons dont work. :(

i tried reinstalling mednafen again, but the buttons problem remained. :(

what do i need to do now to get both problems fixed?

---

### Post by FranMichaels on 2008-04-14
In nautilus, your home folder, press ctrl + h ( or go to the view menu choose show hidden files)

The directory .mednafen, has all the saves, configs, etc. Delete the file mednafen.cfg.

Next to time you load mednafen, the file will be created like new. :)

As for the sound, is there a useful message in terminal? Here are my sound settings as they appear in mednafen.cfg

```
;Select sound driver.
sounddriver ALSA

;Select sound output device.
sounddevice sexyal-literal-default
```

---

### Post by adi116 on 2008-04-14
hmm... well, i'm not too sure what my driver or device names are. any way to find out?

---

### Post by FranMichaels on 2008-04-14
After you've deleted the mednafen.cfg, and run mednafen once. 

Open the mednafen.cfg file in gedit.

You can see all the defaults in the file, and change what you like :KS

EDIT: If you meant your machine, Look under System->Preferences->Sound

If you are with the default, it is very likely you have alsa or oss :)

---

### Post by adi116 on 2008-04-22
thank you! i got everything working great, now! :D

---

### Post by Syndacate on 2008-04-22
I tried maybe a month ago to get a GBA emulator working on here and it was miserable failure :(.

Good to hear you got it working.

---

### Post by disturbedite on 2008-04-22
i tried mednafen years ago & didn't like it cuz i wasn't very proficient with command line at that point.  i'll give it another try.

just for the heck of it, i looked for a frontend & the only one i could find is kemuexec.  (its included in kdeaddons-emulation.  it isn't available in the repo, but there are deb packages on kde-apps/sourceforge).

---

