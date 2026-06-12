---
title: "Buying first PC. Is this enough?"
date: 2007-06-13
forum: Dell  Ubuntu Support
---

### Post by Burbank on 2007-06-13
Hello:

I've been using Mac's for 20 years. But now, I'd like to order my first PC to play around with Ubuntu Linux and maybe (probably not) install XP. I'm thinking about ordering this DELL configuration. Any guidance as to whether this is "enough" hardware would be appreciated.

1	222-8910	Dim E520N, Intel Core 2 Duo Processor E6320 (1.86GHz,1066FSB) with 4MB cache
1	311-6461	1GB DDR2 SDRAM at 667MHz
1	310-8164	Dell USB KEYBOARD
1	320-5210	22 in (22 in viewable) E228WFPWide Aspect Digital Flat Panel
1	320-5088	256MB nVidia GeForce 7300LE TurboCache
1	341-3280	250GB SATA II Hard Drive (7200RPM)
1	341-4028	No Floppy Drive Requested
1	420-7143	Ubuntu Desktop Edition version7.04
1	310-7965	Dell USB 2-button mouse
1	430-0412	Integrated NIC card
1	313-3137	No modem requested for Dell Dimension
1	313-4583	16X DVD-ROM and 16X DVD+/-RW
1	313-2758	Integrated Audio
1	313-2198	No Speaker Requested

Also, with the above configuration can anyone tell me if there will be an unused hard drive bay?

Thanks!!

Dave

---

### Post by hsweet on 2007-06-13
It's more than enough for me.  It'll run well on less hardware than that.  Unless you plan on doing really heavy lifting like rendering feature length films or something like that.

---

### Post by hardyn on 2007-06-13
If its a resonably priced option i would move into a video card that has its own ram.  not a turbocache card.

---

### Post by Burbank on 2007-06-13
> **hardyn said:**
> If its a resonably priced option i would move into a video card that has its own ram.  not a turbocache card.

I think I only had two choices: A DELL video card or the nVidia I ordered.

Dave

---

### Post by imsorryidontdowindows on 2007-06-13
That looks like a good package, ummm don't put the virus on it LOL :popcorn:

---

### Post by syadnom on 2007-06-13
This is actually a GREAT system for ubuntu.

I went with the C521n myself.  thats the athlon x2 3600 version.  same specs otherwise.

you will have a tiny bit of trouble with the nvidia graphics card in full accelerated but if you boot the 7.04 disk in safe graphics mode and turn on restricted drivers that will work.  otherwise you can use the 'nv' driver which is open source and that will be great for 2d and the desktop but no BERYL or COMPIZ.

---

### Post by mojorising on 2007-06-14
Definitely enough for most purposes. 

I am typing this message on a 650 mhz P3 laptop with 512 MB RAM and my system runs great (the RAM really helps).

I think you'll like Ubuntu coming from a Mac. It is just as refined (or at least very close) as Mac and many would say, more powerful. I'm also betting you won't find much use for Windows either. Linux does all the same stuff, only better. 


Mike

---

### Post by Burbank on 2007-06-14
> **mojorising said:**
> Definitely enough for most purposes. 

I am typing this message on a 650 mhz P3 laptop with 512 MB RAM and my system runs great (the RAM really helps).

I think you'll like Ubuntu coming from a Mac. It is just as refined (or at least very close) as Mac and many would say, more powerful. I'm also betting you won't find much use for Windows either. Linux does all the same stuff, only better. 


Mike

Great! I can't wait. -- Funny thing: I placed the order on the Dell site. They said the computer should ship in early July. Then, everything shipped today! With any luck, I'll have my new machine before the weekend.

---

### Post by jarocooke on 2007-06-14
> **hardyn said:**
> If its a resonably priced option i would move into a video card that has its own ram.  not a turbocache card.

As I understand it, a card with TurboCache doesn't mean that it doesn't have its own Video RAM.  What it does mean though is that once that Video RAM is full, the GPU can use the main system RAM as additional VRAM.

The "Black Window Bug" that these cards currently suffer from is due to "GLX_Texture_from_Pixmap" working fine while you are using the dedicated VRAM.  However once this is full and the GPU starts using the system RAM "GLX_Texture_from_Pixmap" is broken, resulting in the "black windows" (as Beryl/Compiz require "GLX_Texture_from_Pixmap" to function).

---

### Post by syadnom on 2007-06-14
with turbocache the card still has some of it's own memory but not very much.  if a card says 128MB turbocache it most likely has something like 16-32mb onboard and fetches the rest from system memory.  if you can fine a way to disable the turbocache then the black screen problem would be gone.  i dont expect that beryl/compiz needs more than 32mb on ram.

---

### Post by dannyboy79 on 2007-06-14
> **syadnom said:**
> with turbocache the card still has some of it's own memory but not very much.  if a card says 128MB turbocache it most likely has something like 16-32mb onboard and fetches the rest from system memory.  if you can fine a way to disable the turbocache then the black screen problem would be gone.  i dont expect that beryl/compiz needs more than 32mb on ram.

the card has 128mb onboard. Unless he's going to be decoding HDTV and whatnot, that's plenty for even compiz or beryl!! I have a 6200 128mb ddr ram and it works great!

---

### Post by Gwasanaethau on 2007-06-14
> **Burbank said:**
> …I've been using Mac's for 20 years. But now, I'd like to order my first PC to play around with Ubuntu Linux and maybe (probably not) install XP…

Ugh, no way! If you've been using Macs for 20 years, then I'd guess you probably won't have any software (usually games) that requires Windows XP to run. If that's that case, don't touch XP with a zillion-foot long cattle-prod! :lol: The only reason why I still have 20% of my hard-disc being eaten up by 'the virus' as  'imsorryidontdowindows' so eloquently put it is due to games. If I find some way of getting them to run in some form of Linux, I'll be disinfecting the remainder of my hard drive faster than you can say "Microsoft"! :lol:

Seriously, if you can avoid it, don't put XP on your new computer - you'd be better off with one of your old Macs for anything that doesn't run in Ubuntu.

---

### Post by djchandler on 2007-06-14
I'm currently on a computer running Feisty with the following configuration:

Pentium III @ 550 mhz
512 mb ram
Nvidia GeForce 2 MX 200
cdrom
20gb hdd

I am not doing any video editing or recording video or audio. I don't play games, and I'm more than happy with Gnome 2.18.  I do word processing, manage a blog, email and most of my internet browsing in Ubuntu due to its relative safety compared to Windows. It is a smooth running little old computer, and is probably running under less strain than if I was using Windows NT 4, which would be about right for hardware specs of this age. (I hate to say this here, but all my heavy lifting is done in XP due to the professional necessity of using Adobe software and more flexible font management and a huge library of high quality typefaces, I quit using Macs 12 years ago they went to the PowerPC platform.) 2D graphics are fine, which is really all I require, but this setup won't do acceptable 3D. Just try all the screen savers and see if they run without a hitch. There are a few in the default installation that will eat your cpu and gpu both if you don't have enough juice. I would say you have power to spare, but I would upgrade that video card as everyone else is saying. But my personal thought is that no manufacturer puts enough graphics hardware on board unless you are willing to overpay dearly. I would probably go with what you are getting, then upgrade the graphics card later yourself. There are remarkable deals from time to time. My favorite online new hardware vendor is Newegg, but I still compare their pricing with pricewatch.com.
:popcorn:

---

