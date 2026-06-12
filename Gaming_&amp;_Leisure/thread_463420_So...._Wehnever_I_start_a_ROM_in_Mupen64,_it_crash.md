---
title: "So.... Wehnever I start a ROM in Mupen64, it crashes...."
date: 2007-06-03
forum: Gaming &amp; Leisure
---

### Post by hyrule_man on 2007-06-03
When I open it in the terminal, it gives me this:





david@david-desktop:~$ '/home/david/Desktop/Mupen64/mupen64' 

(mupen64:20461): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",





Then when I start a ROM (Zelda: Ocarina of Time) it gives me this, and then Mupen64 crashes:




rom size: 33554432 bytes (or 32 Mb or 256 Megabits)
file found
rom size: 33554432 bytes (or 32 Mb or 256 Megabits)
rom loaded succesfully
80 37 12 40
ClockRate=f
Version:1449
CRC: ec7011b7 7616d72b
name: THE LEGEND OF ZELDA 
Manufacturer: 43000000
Cartridge_ID: 4c5a
Country : United States
size: 4096
PC= 80000400
md5 code:5BD1FE107BF8106B2AB6650ABECD54D6
eeprom type:0
init timer!
memory initialized
[glN64]: (WW) Couldn't open config file '/home/david/Desktop/Mupen64/plugins/glN64.conf' for reading: No such file or directory
[glN64]: (II) Initializing SDL video subsystem...
[glN64]: (II) Getting video info...
[glN64]: (II) Setting video mode 640x480...
[glN64]: (EE) Error setting videomode 640x480: Couldn't find matching GLX visual
Signal number 11 caught:
        errno = 0 (Success)
david@david-desktop:~$ 




WTF? I just can't figure it out... By the way, I tried changing all the plugins. Same problem.... Help?

---

### Post by hikaricore on 2007-06-03
Have you tried a different video plugin?

Do you have the proper drivers installed for your video card?
Does your video card support direct rendering?  Is it enabled?

Your post was a little too vague to offer anything but standard questions

---

### Post by hyrule_man on 2007-06-03
My video card is a 16mb Nvidia/Vanta TNT2. (My new one gets here Wensday! =D) And if I install drivers for it, my graphics don't load, and I have to kill the upgrade in the terminal -__- So... I didn't understand the rest of what you said.. Lol. Oh and, OHIO FTW! :popcorn:

---

### Post by hikaricore on 2007-06-03
I'm not sure if the linux drivers for your current card support (3d) direct rendering.

```
glxinfo | grep rendering
```
Will give you your answer.  Though from the terminal output here:

> [glN64]: (EE) Error setting videomode 640x480: Couldn't find matching GLX visual
I'm pretty sure my theory is correct.

Probably best to wait until wednesday and go from there.  :)

Hope it's a better Nvidia card, if so then search the forums for a program called "Envy" for easy binary driver info.

---

### Post by hikaricore on 2007-06-03
P.S.  I've been to many great parties in Cincy.
I used to live right around the corner from there in Centerville, OH.

My 1 bedroom apartment turned into a flop house and after I ended up with 6 useless roommates I headed back up here to Columbus.

---

### Post by hyrule_man on 2007-06-03
Naa, it's an Evga 256mb graphix card. Only 50$! 0_0 Newegg FTW.

---

### Post by hikaricore on 2007-06-03
Link it.  I bet it's an nvidia chipset.  :P

---

### Post by hyrule_man on 2007-06-03
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130197](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130197)


^There it is. Oh, and by the way, ya, that kinda sucks. Lol. The 6 room mates that is.. I can see why you'd move. And Columbus is cool too. My brother lived there a few years back. I always used to go visit him.

---

### Post by hyrule_man on 2007-06-04
Bump?

---

### Post by hikaricore on 2007-06-04
Oh yea, GeForce is Nvidia ^_^

Properly setup it should blow your current card out of the water.  It's not the most powerful card ever, but it does the job, I have nearly the same card on my graphic design desktop system at work running Kubuntu.  hehe

---

### Post by hyrule_man on 2007-06-04
Sweet, thanks. Yeah, my current card came with my computer 8 years ago.. Lol.

---

### Post by noerrorsfound on 2007-06-04
You're not running Ubuntu 64-bit, are you? None of the video plugins for Mupen64 work or compile in 64-bit.

---

### Post by hyrule_man on 2007-06-04
I'm PRETTY sure I'm not... My friend got me a direct link, so I'm not sure... How can I check?:confused:

---

### Post by Crube on 2007-06-18
My Mupen64 crashed everytime I tried to run a ROM. I solved it by adding read and write permissions to /usr/bin/mupen directory, switching from dynamic recompiler to interpreter or pure interpreter, switching from Glide64 to glN64 and now everything works perfectly.



EDIT: Game started perfectly, but saving game makes the game crash. This propably has something to do with permissions, becouse running the game in sudo mode works, and it doesn't crash.

---

