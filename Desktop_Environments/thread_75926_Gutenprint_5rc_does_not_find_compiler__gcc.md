---
title: "Gutenprint 5rc does not find compiler / gcc?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by ibanez88 on 2005-10-14
I'm trying to compile the latest Gutenprint driver.  I'm using a fresh kubuntu install, also installed kernel headers.  I have gcc 4 and 3.4 on my system.  

on typing ./configure I get an error saying a compiler could not be found.  I installed gcc 3.3 just to see if that might work, but I'm not sure if I have to state any options as I issue the command to get ./configure to see a different compiler version.

Are there any other dev packages that I should install?  Or does anyone know the correct options to issue in order to get this to ./configure, make, make install without errors?  

If anyone has had any luck with this, I'm sure it would help.. thanks.

---

### Post by Freddy on 2005-10-14
Get the build-essentials through apt-get.
```
sudo apt-get install build-essentials
```

---

### Post by GeneralZod on 2005-10-14
Have you tried

```

sudo apt-get install build-essential

```

?

Possibly "build-essential*s*"; I can never remember :)

---

### Post by ibanez88 on 2005-10-14
Wow, fastest replies ever!  Thanks guys!  Yes it is build-essential, no "s" on there.

It is compiling as we speak.  I think I need gutenprint to get my Epson Stylus Photo R200 to print directly onto CDs using its CD tray, IMO the best thing ever... If I actually get it working I will post a how-to!  (I'll also trash my Windows computer as that's the only thing I use it for.)

cheers

---

### Post by Freddy on 2005-10-14
Yes of course Zod, you are correct as usual :) but you could also use:
```
sudo apt-get install build-essential*  :)
```
without the smiley though, sorry for this input it was totally pointless and should be ignored ;).   /// Freddan

---

### Post by mervc on 2005-10-26
[QUOTE=ibanez88]Wow, fastest replies ever!  Thanks guys!  Yes it is build-essential, no "s" on there.

It is compiling as we speak.  I think I need gutenprint to get my Epson Stylus Photo R200 to print directly onto CDs using its CD tray, IMO the best thing ever... If I actually get it working I will post a how-to!  (I'll also trash my Windows computer as that's the only thing I use it for.)

cheers[/QUOTE]

Just curious if you were successful?  I also need the latest for my Epson.  However I have been warned it might be tricky since it may need more than just the removal of the existing gimpprint drivers.

Cheerio

---

### Post by ibanez88 on 2005-11-09
Sorry for the delayed response.

I'm recompiling it now as I type.  I had it working on Kubuntu and now on a fresh Ubuntu install.  I think I was able to get the gutenprint drivers to produce regular text documents.  I never did get to use it for my intended purpose (yet).

My intended purpose:  to print directly onto CDs, a great feature of the Epson Stylus Photo R200.  I'm having a hard time getting a template (gimp? openoffice?) that will let me do that.  Haven't had time to figure out how to build one myself.  

I don't think that you have to remove any other drivers.  However I might be wrong, please don't blame me if nothing works afterwards.  ;) 

Good luck!

---

### Post by juliux on 2005-11-25
hi,
has you test to print to a cd?

I can configure it correctly.
Can please write a litte howto, what exactly you do did?

regards

juliux

---

