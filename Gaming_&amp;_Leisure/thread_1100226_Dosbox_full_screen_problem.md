---
title: "Dosbox full screen problem"
date: 2009-03-19
forum: Gaming &amp; Leisure
---

### Post by babujbf on 2009-03-19
I set my resolution in the dosbox.conf file, and still when I hit alt-enter the game goes full screen but I can only see half of the game. The other half is black.

---

### Post by babujbf on 2009-03-19
anyone? help please

---

### Post by Utemetsu on 2009-03-19
Ok, Its been a while since I've used DOSbox, but I think I have you problem fixed:


In the .conf file, near the top, you will see this 'paragraph'

```
fullscreen=false
fulldouble=false
fullresolution=original
windowresolution=original
output=surface
autolock=true
sensitivity=100
waitonerror=true
priority=higher,normal
mapperfile=mapper.txt
usescancodes=true

```

I'm assuming that you have changed the value of 'fullscreen' to true.

Now, Depending on what your resoultion is, (I'll use 1024x78 as an example), change the file so the line that reads
```
fullresolution=original
```

is edited to read
```
fullresolution=1024x768
```

You can use any resolution in place of 1024x768 AS LONG AS YOUR VIDEO CARD SUPPORTS THE RESOLUTION. I would not suggest entering a resolution that is is not supported.

---

### Post by babujbf on 2009-03-19
did that... and still the full screen only shows half of the game... is there any other way of entering full screen than hitting alt-enter?

---

### Post by babujbf on 2009-03-20
anyone help?

---

### Post by Utemetsu on 2009-03-20
Do the same thing to the windowed resoultion entry thats in the .conf file. The trick is figuring out your native resolution. What is your current resolution? Thats the value you should be entering, not the example I gave (unless you're running at the example's res!)

---

### Post by babujbf on 2009-03-20
im running with 1280x1024 my ubuntu, I got Geforce 8500 gt... if that makes a difference... It just appears as if the window when it goes full screen is not centered because the game is off center to the upper right and the bottom left of the screen is just left black.

I did the full and window resolution thing. made now difference

UPDATE

update... it had to do with the .conf file location now the problem is different. It does go full screen and the game is centered, but its tiny!

---

### Post by Utemetsu on 2009-03-20
Ok, so, If I'm understanding you correctly, your .conf file looks like:

```
fullscreen=false
fulldouble=false
fullresolution=1280x1024
windowresolution=1280x1024
output=surface
autolock=true
sensitivity=100
waitonerror=true
priority=higher,normal
mapperfile=mapper.txt
usescancodes=true
```

At this point, I can reccommend two things:
change
fullscreen=false
to 
fullscreen=true
or revert the file to it's original settings if you moved it somewhere else.

---

### Post by babujbf on 2009-03-20
yeah... did that but the game screen is little, its centered but little so is the dosbox when mounting C:

---

### Post by babujbf on 2009-03-22
any ideas?

---

### Post by ]\/[adman on 2009-04-11
switch resolution in config file back to original, and change your desktop resolution to 800x600 before running dosbox. I had the same problem and it worked for me

---

### Post by irwa82 on 2009-06-13
Hi,

I have solved the problem of the black border on my computer by changing the fullscreen resolution and window resolution to be the same that my computer is using.

You also must set output to overlay instead of surface for it to stretch to fill the whole screen.

hope this helps people out.

regards,
Anthony Irwin

---

### Post by rosswmcgee on 2009-06-15
How do you do this?

---

### Post by irwa82 on 2009-06-16
Hi,

First you will need to generate a dosbox.conf file to do this open up dosbox. Then when in dosbox run the command "CONFIG -writeconf dosbox.conf" without the quotes to generate a config file.

Close out of dosbox and open the dosbox.conf file that is now in your home directory.

At the top of the file in the [sdl] section you will want to change the following options:

fullscreen=true
fullresolution=1680x1050
windowresolution=1680x1050
output=overlay

Obviously you will change the 1680x1050 to what ever screen resolution you are using.

Another handy thing to add at the end of the file in the [autoexec] section is the following:

mount c /home/yourusername/dosgames/
c:

the top line will automatically mount a c drive obviously you need to point it to where you want your c drive to be. The second line will automatically point dosbox to the c drive so you are ready to go when dosbox starts.

Hope this helps.

---

