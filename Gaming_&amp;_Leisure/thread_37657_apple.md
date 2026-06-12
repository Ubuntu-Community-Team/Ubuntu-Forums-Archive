---
title: "apple //"
date: 2005-05-28
forum: Gaming &amp; Leisure
---

### Post by simple on 2005-05-28
anybody have apple // emulator working ? or can help me get one and get it working so i can hit up some the oregon trail

---

### Post by slux on 2005-05-30
Debian has an "apple2" package. I'm guessing Ubuntu's got the same. The Debian (and no doubt also the Ubuntu) package [description](http://packages.debian.org/stable/otherosfs/apple2) links to the ROM images.

Does that help or were you having some specific issues with an emulator itself?

---

### Post by kevinlyfellow on 2007-01-30
I'm trying to do the same thing myself ;-)  I miss that game so much!  Of course the package is in the multiverse repo, but the hard part is using it!  

Edit:
Wow, its been a while since the thread started!

```

Warning. Cannot open the .apple2 system defaults file.
Make sure it's readable in your home directory.Press RETURN to continue...
ioperm: Operation not permitted
cannot get port access to PC speaker.
sound will not be used.
Using standard VGA 320x200 mode.
Press RETURN to continue...
svgalib: Cannot get I/O permissions.

```

---

### Post by Mike'sHardLinux on 2007-01-31
LOL!! That was a pretty old thread!  :lol: 

Anyway, if you happen to have Cedega, it runs AppleWin and Kegs32 beautifully.

---

### Post by kevinlyfellow on 2007-01-31
I never knew that... but unfortunatly I don't have cedega.  Most of the games I play are open source or old dos games so cedega isn't worthwhile to me.  I'll have to spend some time plugging away at the apple ][e emulator...

---

### Post by Mike'sHardLinux on 2007-02-01
Hi again!

I just tried AppleWin with Wine, and without any tweaks, it works, except for sound. I am trying some things to get sound working. I am using the version of Wine that is in the repos.

Edit: Actually, I just realized my sound in Wine is broken because I installed a Delta 10/10 soundcard and then uninstalled it and haven't figured out where the setting is to change the sound back to the onboard sound as the default. I'd bet your sound will work fine.

Last edit: I fixed my sound problem, and the sound does work for AppleWin in Wine.

---

### Post by kevinlyfellow on 2007-02-01
Excellent!  I'll give that a try....

Its kinda funny, we're emulating an emulator!

---

### Post by slimdog360 on 2007-02-01
you can run Mac classic 7.0.1 from a usb disk
[http://portableapps.com/apps/operating_systems/mac-on-stick]("http://portableapps.com/apps/operating_systems/mac-on-stick")

---

### Post by Malcolm on 2007-05-02
Did you manage to get AppleWin working in full screen? Wine crashes when I try that... So far my best choice has been ApplePC running under DOSBox (another emulated emulator :p).

---

### Post by nythacker on 2007-05-02
Why don't you use [COLOR="Blue"]**KEGS**[/COLOR] instead as it's open source. KEGS is a better Apple II emulator than any other I've tried in Linux. You just need to compile it and go...

**[http://kegs.sourceforge.net/]("http://kegs.sourceforge.net/")**

---

### Post by Malcolm on 2007-05-02
I compiled KEGS32 and have a working Apple IIgs system now, but I'm not sure it's compatible with all Apple ][ software on disk images.

EDIT: Ok, I found out how to do it. The only thing missing is full screen now. :)

---

### Post by Seantiago on 2007-05-07
I got kegs up and running but I can't seem to find any roms for it, even after googling a bit, and even if I did find any I would have the foggiest what to do with them. Any advice?

---

### Post by nythacker on 2007-05-07
> **Seantiago said:**
> I got kegs up and running but I can't seem to find any roms for it, even after googling a bit, and even if I did find any I would have the foggiest what to do with them. Any advice?

Hah, then you really haven't learned how to *Google*! Use the keyword "**[COLOR="Blue"]apple ii gs rom[/COLOR]**" in Google and select the first entry. You should be able to find what you're looking for there.

Just rename the Apple II GS ROM to either **[COLOR="Red"]ROM[/COLOR]** or **[COLOR="Red"]ROM.01[/COLOR]** or **[COLOR="Red"]ROM.03[/COLOR]** (depending on the Apple II GS ROM that you have) and place it inside the KEGS folder and you should be good to go.

Hope this helps...

---

### Post by noerrorsfound on 2007-05-07
> **kevinlyfellow said:**
> Excellent!  I'll give that a try....

Its kinda funny, we're emulating an emulator!
**W**ine **i**s **n**ot an **e**mulator.

---

### Post by nythacker on 2007-05-07
> **Malcolm said:**
> I compiled KEGS32 and have a working Apple IIgs system now, but I'm not sure it's compatible with all Apple ][ software on disk images.

EDIT: Ok, I found out how to do it. The only thing missing is full screen now. :)

The [COLOR="Blue"]Apple // GS[/COLOR] and any version of the [COLOR="Blue"]KEGS[/COLOR] emulator is _**very compatible**_ and can run 99% of all the games and apps made for the entire line of Apple ][ computers (Apple ][ / ][+ / ][e / ][c).

---

### Post by csmth on 2007-10-20
> **Malcolm said:**
> I compiled KEGS32 and have a working Apple IIgs system now, but I'm not sure it's compatible with all Apple ][ software on disk images.

EDIT: Ok, I found out how to do it. The only thing missing is full screen now. :)
I wish to compile KEGS but it fails. I know I must missed some library because:
(1) My Ubuntu 7.10 is newly installed
(2) I had compiled KEGS on Sabayon Linux. There is no reason to believe there is some radical difference between two versions of Linux except the library and packages.

Could anyone indicate what package or library is need?

---

### Post by michelefrost on 2008-01-20
the compiler / linker should indicate it by itself.

Which kind of error messages do you get?
Post them here please.

---

### Post by csmth on 2008-04-15
I find out the issue. I need to install xorg-dev package to compile KEGS. Without xorg-dev, KEG cannot compile.

> **csmth said:**
> I wish to compile KEGS but it fails. I know I must missed some library because:
(1) My Ubuntu 7.10 is newly installed
(2) I had compiled KEGS on Sabayon Linux. There is no reason to believe there is some radical difference between two versions of Linux except the library and packages.

Could anyone indicate what package or library is need?

---

### Post by patrick295767 on 2009-03-17
> **noerrorsfound said:**
> **W**ine **i**s **n**ot an **e**mulator.

man because you arent capable to run linux, then you arent solving this of the guy of this thread:
> 
$ xapple2
Warning. Cannot open the .apple2 system defaults file.
Make sure it's readable in your home directory.Press RETURN to continue...
ioperm: Operation not permitted
cannot get port access to PC speaker.
sound will not be used.
Sorry bud, xapple2 only supports 8bit PseudoColor displays.
Maybe you can fix this!

the guy wants to use linux, not windows/wine :) lol

---

### Post by noerrorsfound on 2009-03-18
> **patrick295767 said:**
> man because you arent capable to run linux, then you arent solving this of the guy of this thread:


the guy wants to use linux, not windows/wine :) lol
Not only does your response make no sense, but you bumped this after nearly a year to say that.

---

