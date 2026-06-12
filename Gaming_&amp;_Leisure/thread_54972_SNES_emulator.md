---
title: "SNES emulator"
date: 2005-08-06
forum: Gaming &amp; Leisure
---

### Post by ItIsMe on 2005-08-06
Is there any way to install a SNES emulator, like Snes9x or ZSNES, using synaptic? And what is the repository needed to find it?

---

### Post by eelozano on 2005-08-06
sudo apt-get install zsnes

or 

search for 'zsnes' in synaptic

---

### Post by eelozano on 2005-08-06
If its not included with the 'normal' repositories.

Follow these directions and you should be good to go.

[http://www.frankandjacq.com/ubuntuguide/5.04/#extrarepositories](http://www.frankandjacq.com/ubuntuguide/5.04/#extrarepositories)

P.S. The link will help you with a lot of other problems you may have as well :)

---

### Post by ItIsMe on 2005-08-07
Thanks.

---

### Post by 2manydrugsago on 2008-01-22
I downloaded Snes9x 1.51 in a .tar.gz  file. How do I install it, will it be ok in Ubuntu 7.10?

---

### Post by dannyboy79 on 2008-01-22
> **2manydrugsago said:**
> I downloaded Snes9x 1.51 in a .tar.gz  file. How do I install it, will it be ok in Ubuntu 7.10?

first put the tar gzipped file where ever you'll want it unpacked. then cd to the folder that the tar gzipped file is residing in. then issue

tar -xvvf foo.tar.gz
(or in case you put it in a location that only root can write to, you'd have to use sudo.)

this will unzip it all into a folder. then you cd into that folder and read the README or INSTALL file which tells you how to install it. it's most likely 3 commands
./configure
make
sudo make install
you'll need the developers tools first though. they're in the build-essential package. see here for more help: [http://ubuntuforums.org/showthread.php?t=323939](http://ubuntuforums.org/showthread.php?t=323939)

---

### Post by 2manydrugsago on 2008-01-22
Ill try that thanks.

---

### Post by inversekinetix on 2008-01-22
you shouldn't post links to nintendo emulators, nintendo have made it clear that emulation is illegal and they have their own emulation patents.

---

### Post by DoktorSeven on 2008-01-22
Emulation isn't illegal, never has been, regardless of Nintendo's objections in the past.

Links to *copyrighted ROMs*, however, certainly is.

---

### Post by inversekinetix on 2008-01-23
talk to nintendo's legal dept about that.  the emulator can only be used with dumped roms the roms themselves cannot be plugged into a PC as standard.  therefore nintendo argues that the sole purpose of the emulator is to facilitate the use of illegally dumped roms.  

That's not even mentioning the legality of the  BIOS files.

---

### Post by acoustibop on 2008-01-23
Nevertheless, emulation of the SNES, if not done using Nintendo's own copyrighted code, is legal: this was pretty well established by the cases Sony brought and lost against Connectix VGS and Bleem!

While the vast majority of SNES9x/ZSNES users probably do obtain their ROMs illegally, this doesn't mean it's not possible to dump your own ROMs and use those - which would be perfectly legal, and hence legitimises the emulators, as they can therefore be used perfectly legitimately.

There again, many people consider that, going back to Sony again, probably the most litigious of the console makers, the fact that Sony only used mod protection on US Playstation games, while they used copy protection in Europe and Japan, is because they consider that preventing the games being copied in the US might be illegal, while preventing them from being played on an altered (modchipped) console would be defensible in law.  So copying games as such is not illegal: it's distributing or receiving copies that breaks the law.

Again, emulators that need a BIOS either don't include one or use one the the emulator developer has written themselves, not using the console manufacturer's code.  This was, again, established to be legitimate in the case of Sony versus Connectix.  And users of the emulator, again, can dump their own BIOSs.

---

### Post by inversekinetix on 2008-01-23
i guess everyone must have one of these

[http://www.tripoint.org/kevtris/Projects/copynes/index.html](http://www.tripoint.org/kevtris/Projects/copynes/index.html)

then.

---

### Post by acoustibop on 2008-01-23
Not necessarily, inversekinetix.  They may have just borrowed the kit to rip their games, or got someone else to do it for them.

The bottom line is that, as long as nobody says they've done any thing illegal (like asking for support for a game they admit is downloaded) or tries to induce others to participate in illegal acts ( like people who post asking where they can get ROMs), there's nothing illegal about discussions of emulation, including links to software that is not illegal and support of the software.

The legality, of course, can vary from country to country.  As a rule of thumb, the laws that would apply to any particular forum would be the laws of the country where it is hosted.

But, another point about the legality of emulation: do you really think Ubuntu would allow emulator packages into the repositories if they were illegal?

---

### Post by disturbedite on 2008-01-23
zsnes is the better emulator.  it has better implementation of the snes hardware last time i checked.

---

### Post by inversekinetix on 2008-01-23
> **disturbedite said:**
> zsnes is the better emulator.  it has better implementation of the snes hardware last time i checked.

+1

---

### Post by 2manydrugsago on 2008-01-27
I got snes9x working. Now how to I configure the controls. I dont know what button does what. I am using a keyboard. I figured out d=a and c=b  but thats it.

---

### Post by rysin on 2008-01-27
is there a way to get a logitech gamepad to work with snes9x?

---

### Post by 2manydrugsago on 2008-01-27
Unfortunately  this box has a old vodoo 3 3000 card and  zsnes doesnt like porting the graphics to it so snes9x works. Less intuitive but works with my old system.
I found the default key settings for snes9x in case anyone has problems similar to mine.

Z,B,W = Top Right button
A,V,Q= Top Left
SME = Xbutton
XR = right button
DT = A button
CY = B button
enetr = start
space bar = select
Shift + F!-9 save states
F1-9 load states

---

### Post by Perfect Storm on 2008-01-27
Closed for investigation

---

### Post by Perfect Storm on 2008-01-27
reopen.

---

### Post by inversekinetix on 2008-01-27
doesnt snes9x have a joypad keymapper built in?

---

### Post by dtruong0884 on 2008-01-28
it does but i'm finding that if i use it i get "snes9x error message 1".  emulation works fine if i'm just using the keyboard.  i have a logitech dual action gamepad... has anybody else experienced the same issues?  also, how do i get the directional pad to work instead of the analog sticks?  thanks for your help.

EDIT nm i found a thread dealing specifically with my problem... silly me not searching gamepads first... kthxbai

---

### Post by darundal on 2008-01-31
Anyone know of any other SNES emulators other than snes9x and zsnes for ubuntu?

---

### Post by Hiro2k on 2008-06-20
> **dtruong0884 said:**
> it does but i'm finding that if i use it i get "snes9x error message 1".  emulation works fine if i'm just using the keyboard.  i have a logitech dual action gamepad... has anybody else experienced the same issues?  also, how do i get the directional pad to work instead of the analog sticks?  thanks for your help.

EDIT nm i found a thread dealing specifically with my problem... silly me not searching gamepads first... kthxbai

How did you get it to work? I'm using Hardy AMD64 and can't get this logitech to work. I have the exact same problem and this is so frustrating!

---

