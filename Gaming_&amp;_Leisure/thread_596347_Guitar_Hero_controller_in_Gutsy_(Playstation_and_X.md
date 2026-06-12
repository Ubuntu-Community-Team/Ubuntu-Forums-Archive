---
title: "Guitar Hero controller in Gutsy (Playstation and Xbox versions?)"
date: 2007-10-29
forum: Gaming &amp; Leisure
---

### Post by Niklas Schröder on 2007-10-29
Apparently people on the forum have gotten this guitar working in Gutsy...

[http://www.redoctane.com/guitarhero2x-explorer.html](http://www.redoctane.com/guitarhero2x-explorer.html)

But my question is whether this one...

[http://www.redoctane.com/gh-sgcontroller.html](http://www.redoctane.com/gh-sgcontroller.html)

Could work if i had this...

[http://www.radioshack.com/product/index.jsp?productId=2348187&cp=&pg=2&sr=1&origkw=playstation&kw=playstation&parentPage=search](http://www.radioshack.com/product/index.jsp?productId=2348187&cp=&pg=2&sr=1&origkw=playstation&kw=playstation&parentPage=search)

Maybe?

**The answer is yes.  Here's how you do it.**
*(The following is copied from one of my posts located a little further down the page.)*

----------------------------------------------------------------------

```

mkdir ~/.xpad360

```
```

cd ~/.xpad360

```
```

wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c"
wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h"
gedit Makefile

```

Copy and Paste this text:

```

obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)
all:
	$(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)
install:
	mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick/

```

Save and exit.

```

make
sudo make install

```

Close your terminal.  Ok.  Now open it back up.  (Yes, I know I could just cd back to the beginning, but I'm too lazy!  :p )

```

update-modules
sudo depmod
sudo modprobe -r xpad
modprobe joydev 
modprobe usbhid 
modprobe xpad

```

Now to see if everything worked:

```

cat /dev/input/js0

```

You should see a bunch of weird characters.


Elcasey pointed this out...

> 
When I first ran FOF after getting the X-plorer working FOF went crazy when I tried to set the strum bar as Pick button. I had to run "jscalibrator", move the tremolo around and press every button. Then I just saved the config with jscalibrator, exited, and FOF works fine now. So just a heads up if your FOF or other app goes berserk when you first get your X-plorer going.


---

### Post by Niklas Schröder on 2007-10-29
i haven't seen any success stories with wireless controllers, but is there a chance this could work?

---

### Post by Niklas Schröder on 2007-10-29
What about this one...

[http://www.theantcommandos.com/rocking_red.aspx](http://www.theantcommandos.com/rocking_red.aspx)

---

### Post by Niklas Schröder on 2007-10-29
According to...

[http://www.linux.com/articles/13741](http://www.linux.com/articles/13741)

The Play Station controller idea SHOULD work.  But he did it with a normal PS controller, not a Guitar Hero guitar.



Why do I get the feeling that this is gonna be another one of those threads where I share stuff as I learn it, you guys read it, shrug your shoulders, say "cool" and move on?  :p

---

### Post by Anovadea on 2007-10-31
> **Niklas Schröder said:**
> 
Why do I get the feeling that this is gonna be another one of those threads where I share stuff as I learn it, you guys read it, shrug your shoulders, say "cool" and move on?  :p

Well, if it's any incentive, I'm paying attention to the thread as well. I'm very much planning to figure out if this is possible.

Looking at a game called [Digiband]("http://www.digiband.net/") they seem to reckon it's possible to hook up a Guitar Hero controller... they don't mention how.

Still, it's a good indication that it's possible, and they probably consider it to be trivial. Similarly, the [Frets On Fire]("http://fretsonfire.sourceforge.net/") page mentions in their FAQ that the whammy bar doesn't work - that tells me that people have the controller working on there. :)

As for my own approach I think I'm going to go with just getting a PS2 -> USB converter and plug in my guitar controller. I know that since the linux 2.4 days there have been drivers to handle these converters (a friend of mine had a very big and solid DDR dance mat connected to their PC), so if nothing else, I'll be able to play my emulator games in style. :)

Between us, we can keep up to date on this. :)

Regards,
Aoife

---

### Post by Niklas Schröder on 2007-10-31
sweet!  attention!  :p  i think that this thread will take off once i finally convince my parents to let me buy the $60 x-plorer controller for the xbox.  then i'll actually have something to mess with.  ;)  right now i'm just messing with settings and other junk.

---

### Post by Niklas Schröder on 2007-11-02
just wanted to let you all know that i finally bought a used x-plorer controller from the local gamestop.  after about 15 minutes of tinkering with the repos and other stuff, i got it working perfectly!  :D  i'll be posting a how-to (short, concise, and n00b-proof) very soon.  if you don't hear from me for a while, post a reply on this thread or e-mail me (as a kind of digital slap :p ) to remind me to get my act together.  BACK TO FRETS ON FIRE!  ;)

---

### Post by Niklas Schröder on 2007-11-02
ok.  here's a *rough* version.  i'll refine it a little tomorrow, but for now, i'm off to bed.  ;)

----------------------------------------------------------------------

```

mkdir ~/.xpad360

```
```

cd ~/.xpad360

```
```

wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c"
wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h"
gedit Makefile

```

Copy and Paste this text:

```

obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)
all:
	$(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)
install:
	mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick/

```

Save and exit.

```

make
sudo make install

```

Close your terminal.  Ok.  Now open it back up.  (Yes, I know I could just cd back to the beginning, but I'm too lazy!  :p )

```

update-modules
sudo depmod
sudo modprobe -r xpad
modprobe joydev 
modprobe usbhid 
modprobe xpad

```

Now to see if everything worked:

```

cat /dev/input/js0

```

You should see a bunch of weird characters.


Elcasey pointed this out...

> 
When I first ran FOF after getting the X-plorer working FOF went crazy when I tried to set the strum bar as Pick button. I had to run "jscalibrator", move the tremolo around and press every button. Then I just saved the config with jscalibrator, exited, and FOF works fine now. So just a heads up if your FOF or other app goes berserk when you first get your X-plorer going.


---

### Post by Niklas Schröder on 2007-11-02
by the by.  i only own the **wired** x-plorer xbox controller.  it's got a nifty little usb connector on the cord that makes connection extremely easy.  now.  i've heard that with the proper psx to usb adaptor (like the one from radioshack i think i mentioned before), you can connect a **wired** ps2 controller to your computer.  but i don't have one, so i can't help much in that area.

but, Anovadea, and anyone else out there, i'm willing to do everything i can to get you guys up and running too.  :)

---

### Post by Naegling23 on 2007-11-03
I had the wireless ps2 controller working under feisty using the radioshack ps2/usb adapter.  It worked fine.  

However, it no longer works, im trying to figure out why, but I think something is broken, the wireless reciever connects to the guitar, but the guitar never connects to the reciever.  Im going to try a new ps2/usb adapter to see if that works(I already replaced a broken wireless reciever, makes sence that both would break at the same time).  Anyway, the ps2/usb adapter works.

---

### Post by Niklas Schröder on 2007-11-03
awesome!  any chance you could post the repos or other files we need to get it working on our machines?

---

### Post by Niklas Schröder on 2007-11-03
ok.  i just found a problem.  if you unplug the guitar, on your next session, it doesn't recognize it at all.  i can get the computer to see it, but frets won't use it...

---

### Post by Niklas Schröder on 2007-11-03
a quick fix for the above mentioned problem...

if you happen to unplug your guitar, reboot (do **not** plug in your guitar until i say), wait for the login screen, plug in the guitar, login, and enjoy some quality time with "the foo fighters."

---

### Post by Azzco on 2007-11-08
I tried to follow your mini howto... when running the make command I get

```
make modules -C /lib/modules/2.6.22-14-386/build SUBDIRS=/home/azzco/.xpad360
make: *** /lib/modules/2.6.22-14-386/build: No such file or directory.  Stop.
make: *** [all] Error 2
```

Oh and BTW you could have written ~ instead of /home/username ;)

---

### Post by Niklas Schröder on 2007-11-08
based on the output, i'd say the error is because you're using kubuntu.  you don't have the same kernel as me, which is producing errors.

---

### Post by Burgundavia on 2007-11-09
Kubuntu uses exactly the same kernel as Ubuntu. As do Edubuntu, Xubuntu, Studio, etc. 

Corey

---

### Post by Niklas Schröder on 2007-11-09
hmmm...  ok...  but it's obviously not finding the file it needs.  and the 2.6.22-14-386 is a kernel.  are you using your own build?

---

### Post by Azzco on 2007-11-09
```
azzco@Azzco-Desktop:~$ uname -r
2.6.22-14-386
```

I've been messing with compiling kernels but I'm only using the stable ones.

---

### Post by Niklas Schröder on 2007-11-09
this is quite strange.  anyone with more experience want to lend a hand?  i'm stumped...

---

### Post by Azzco on 2007-11-09
I have no idea what the difference was but I followed the old thread around here about xbox360 gamepads on feisty and ended up getting it to work.
Too bad I'm more used to the keyboard now. =/

---

### Post by Niklas Schröder on 2007-11-09
lol!  yeah.  i had that same problem (about being more used to the keyboard).  

glad you got it fixed!  :D

---

### Post by Anovadea on 2007-11-11
Well... PS2->USB converter and a PS2 guitar controller works fine with it.

Makes me want to explore what I can do with the converter now... 

Aoife

---

### Post by Niklas Schröder on 2007-11-11
the ps2 works with this tutorial?

---

### Post by Anovadea on 2007-11-12
Actually it's mostly down to just plugging and playing.

With the EMS 2 controller, it will set up 2 js devices in /dev/input and frets on fire picks it up easily enough.

If you want to check that it's receiving signals easily enough just us "jstest" - I think. If it's not installed, it will tell you to "apt-get install joystick" (I think, I'm not at my ubuntu machine right now).

The whammy bar doesn't register at the moment with the convertor, but none of the analog signals do. I read something in a recent Linux format saying that the analog joysticks didn't work on the ubuntu box that they were using for testing. Now, they used feisty, but it seems it hasn't changed since then (I doubt it's a major concern for linux kernel devs).

But guide is: plug and play, and look for the device files in /dev/input/js*, and test them with jstest.

Aoife

---

### Post by Niklas Schröder on 2007-11-19
here's a little hint that should smooth out a few problems.

type...

```

sudo gedit /etc/modules

```

and add...

> 
# Modules needed to set-up my guitar hero controller
usbcore
joydev
xmod


to the bottom of the file.

this allows your computer to load the needed modules on start-up.  helped a bit for me.  ;)

---

### Post by Un-Blackmetal on 2007-11-22
Hey guys, im new to this site and im fairly noobish when it comes to linux, i have found this thread a few times while trying to get my guitar hero 2 PS2 controller working in ubuntu. i have failed thus far, it seems almost like i dont have joystick support at all, when i type cat /dev/input/js0 into the terminal i get this back 

> cat: /dev/input/js0: No such file or directory


Not quite sure what steps i need to take to get joysticks working properly, any help would be greatly appreciated.

---

### Post by Niklas Schröder on 2007-11-22
that's because you're trying to get a ps2 controller working.  this guide is only for the xbox controller (so far).  maybe we can attract some attention from someone a little more skilled though shall we?

---

### Post by xDCx on 2007-11-23
I've got the Wired x-plorer 360 guitar, and i followed all the code you posted, but still got an error.

```
xdcx@breaky:~$ cat /dev/input/js0
cat: /dev/input/js0: No such file or directory
```

---

### Post by devguy on 2007-11-29
The same thing happened to me when I tried the tutorial.  It seemed to help rebooting the machine 2 or 3 times and each time not plugging in the guitar until you see the login screen.  Eventually, it seemed to recognize it and work fine.

However, I find it odd that it won't work strictly as plug and play.  Is there anyone who can find a fix for this?  Or even better, if I leave the guitar plugged in while the OS is booting, it will hang on the boot every time.

---

### Post by Niklas Schröder on 2007-11-29
i've found that it's more effective to plug in the guitar once the boot process gets past the third or fourth bar in the graphical loader.  works every time!  :)  but yes, we *do* need plug-and-play.

---

### Post by elcasey on 2007-11-29
I just bought an X-plorer off of eBay so in a week or so I'll hopefully be rocking out *sans* keyboard. It's just too hard to go to F5 for that last fret and I have to reach too far to use 1-5 keys...

Do we have a *definitive* procedure yet? I don't wanna jump through a bunch of hoops and load a bunch of modules if, as Anovadea says, all I need to do is install the "joystick" package and plug in the controller.

I'll check around on FOF forums and KOF forums and see if I can't find anything else.

---

### Post by djbon2112 on 2007-12-18
I tried this, but it doesn't work. I get to the last step, and it says:

```
cat: /dev/input/js0: No such file or directory
```

and the ring of lights on the controller just flashes. Any suggestions? I've got GH3PC working under Wine and I want to play it but I need the guitar ;)

---

### Post by Niklas Schröder on 2007-12-18
which version of the guitar are you using?  the new wireless one? or the white wired usb one?

---

### Post by djbon2112 on 2007-12-18
The white wired Xplorer one from Guitar Hero 2 X360.

---

### Post by Niklas Schröder on 2007-12-18
you sure you followed all the steps and have all the dependencies (if any) you need?

---

### Post by djbon2112 on 2007-12-18
Yes, followed all the steps to the letter, and it all seems fine (no errors or anything) until that last step.

I'll try doing it again from the beginning, maybe it was just a fluke.

EDIT: Ok, I tried again. I followed [http://ubuntuforums.org/showpost.php?p=3695364&postcount=8](http://ubuntuforums.org/showpost.php?p=3695364&postcount=8) again to the letter with the guitar unpluged, then pluged it in. The lights now flash once then stay off (all four), but it still doesn't work in the game. I tried redoing the steps with the guitar plugged in, but now it gets stuck on:

```
modprobe -r xpad
```

... and if i close the terminal while it's doing this, open up a new one and complete the steps, I get:

```
cat: /dev/input/js0: Input/output error
```

EDIT 2: After realizing WHAT modprobe is... I think it was a bit stupid to just close the command, but I'm running it again, and it seems to be doing the same thing, just sitting there after entering this command. Is it supposed to take forever?

EDIT 3: I tried running the cat command again, even while modprobe was running, and I got the crazy characters. But the game STILL doesn't detect it and there's still no lights on on the controller. Linux really needs plug and play ASAP...

---

### Post by Niklas Schröder on 2007-12-18
you might want to try rebooting too.  ;)

---

### Post by djbon2112 on 2007-12-18
D'oh. Definitely forgot THAT step. Doing that now >.<

---

### Post by djbon2112 on 2007-12-18
Rebooted, game STILL doesn't detect it. Is there something I have to configure in Wine to make this work?

---

### Post by Niklas Schröder on 2007-12-18
oh!  wait.  didn't pay attention to your first post this morning.  didn't see you were running through wine.  have you tried it in frets on fire?  that's what this guide's really meant for.  not so sure if it'll work through wine (what with all the limited permissions and all).

---

### Post by djbon2112 on 2007-12-18
I'm not a fan of FoF, so I haven't tried it. I'll go ask in the Wine forum though ;)

---

### Post by Niklas Schröder on 2007-12-18
that'd be a good idea.  :)  i'm not a fan of running windoze programs in linux (just feels weird), so i avoid it at all costs.  ;)

---

### Post by elcasey on 2007-12-19
These are the errors I'm getting:
```
[ch@natalya:src/xpad360]% sudo modprobe joydev usbhid xpad        (12-19 12:41)
FATAL: Error inserting joydev (/lib/modules/2.6.22-14-generic/kernel/drivers/input/joydev.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Then when I "see dmesg" I get:
```
[398334.559111] usbcore: deregistering interface driver xpad
[398343.563922] usbcore: registered new interface driver xpad
[398343.563929] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[398416.576683] usb 4-2: USB disconnect, address 3
[398421.859707] usb 4-2: new full speed USB device using uhci_hcd and address 4
[398422.076850] usb 4-2: configuration #1 chosen from 1 choice
[398641.347261] usbcore: deregistering interface driver xpad
[398654.071939] joydev: Unknown parameter `usbhid'
[398705.271070] joydev: Unknown parameter `usbhid'
[398729.642052] joydev: Unknown parameter `usbhid'
```

I'm assuming I need to install "usbhid" but there is no package for this. I'll look around for info about making it, but I think it'd be helpful if you covered dependencies in a lot more depth.
I'm hoping to get this resolved soon. I FINALLY (after a string of UPS shipping screw-ups) got my X-plorer today and I'm neither a patient nor serene man. I almost threw the damn thing across the room earlier. Please help, for the sake of the children. :P

---

### Post by Niklas Schröder on 2007-12-19
have you rebooted?  i had a similar error that was fixed by restarting.

---

### Post by elcasey on 2007-12-19
The problem is that I don't have "usbhid." I tried looking around for a package or some way to install it, but nothing showed up. :confused: And yes, I have linux-headers-2.6.22-14-generic installed.

---

### Post by Niklas Schröder on 2007-12-19
did you try rebooting?

---

### Post by elcasey on 2007-12-20
LOL, yes I rebooted. We shouldn't have to reboot to load hardware modules, but I still have this usbhid issue. It works fine in Windows (when I rebooted, I figured I'd give XP a go) and still blinks nonstop under GNUlix (as I like to call it).

I just need to figure out how to load the "usbhid" module. Or install it, more appropriately.

---

### Post by Niklas Schröder on 2007-12-20
you probably have, but have you tried it in different usb ports?  my guitar's lights stopped flashing as soon as i started using the terminal for my tut...

---

### Post by elcasey on 2007-12-20
Why would it matter which USB port I have it plugged into? And I use the terminal extensively, I'm not trying to do this in the GUI somehow... :confused:

---

### Post by elcasey on 2007-12-20
OK, my USBHID does actually work. The problem was that you cannot modprobe multiple modules on a single line. Your howto shows:
```
modprobe joydev usbhid xpad
```
It should be a separate modprobe (as well as being run with sudo) for each module (according to someone in #ubuntu-kernel and I stopped getting an errror when I did that).

I went back through the whole tutorial but I still get nothing for /dev/input/js0. I'll try rebooting again, but you should not have to reboot. The controller works fine, it worked beautifully in Windows (go figure). ](*,)

EDIT: Rebooted, redid the whole thing, still nothing. It's not that surprising since I always have a lot of problems with Linux that no one else does, but disappointing nonetheless. I hate Windows, yet I'm still forced to use it for so much.

---

### Post by Bionic Apple on 2007-12-24
So, how would you get the wired Xbox 360 Guitar Hero 2 guitar running natively in Ubuntu?  In the first post, it was mentioned that someone figured out how to do it.

---

### Post by Niklas Schröder on 2007-12-24
that's strange...  i'm now having the same problem as many of you...

---

### Post by Niklas Schröder on 2007-12-24
VERY strange.  the only thing i can tell you guys is to go through with the tutorial again.  it might fix it.  i think the latest kernel update broke it...

---

### Post by elcasey on 2007-12-27
I've gone through two different tutorials multiple times and mine still doesn't work. Plug it in in Windows and it fires right up. Luck of the draw, I suppose. The strength of FOSS is how different and open and personalized a system can be, but it's a bitch of a drawback when it comes time to troubleshoot. :(

---

### Post by Niklas Schröder on 2007-12-27
just to let you know, the reason it works so well in windoze is cause it was made by micro$oft.  :p  i'm actually surprised i was able to convince myself to buy the little guitar.  ;)  i'll look into your problem.  but for now, you may want to search for another option or get real good at playing with the keyboard.

---

### Post by elcasey on 2007-12-27
Well for now I just play FOF in Windows. I played with the keyboard for a good few weeks, but it's just impossible go to Fret 5 with the F-keys. Not that I'm too good at going to Fret 5 on the X-plorer, but that's a whole other issue. :P

---

### Post by elcasey on 2007-12-27
Got it working. The installation script *installs the driver in the wrong path*.

To quote Fitzsimmons:
> The problem is that the install script provided by this package is placing the file in the wrong place.

Specifically, this line:
```
mv -f xpad.ko /lib/modules/2.6.22-14-generic/kernel/drivers/usb/input
```

It appears that drivers/usb/input no longer exists as a directory, so this actually ends up moving xpad.ko to a file named input, in the directory drivers/usb/.

Instead, move the file manually after a successful build:

```
sudo cp -f xpad.ko /lib/modules/`uname -r`/kernel/drivers/input/joystick/
```

I manually moved the driver as described above, rebooted, and it works fine. Those of you still having problems, try this.

On a side note, Guitar Hero III for PC is awesome. If you dual-boot, you should check it out (or maybe the X-plorer will work in GH3-on-Wine?).

---

### Post by Niklas Schröder on 2007-12-27
ok.  happy you got it working.  :)  what should i change in the how-to now?  (i'm feeling lazy.  sorry.)  let me know if any of you get gh3 working through wine.  i'm curious as to whether it can handle that much strain.  ;)

---

### Post by elcasey on 2007-12-28
The only thing you need to change in your howto (I should've caught this right from the beginning) is this line in the Makefile:
```
install:
	mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick
```

Should be this instead:
```
install:
	mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick/
```

Hardly any difference. But without the trailing / after "joystick," you've moved the xpad.ko driver into a *file* called "joystick" in the drivers/input/ directory rather than moving it into the drivers/input/joystick/ directory.

As far as GH3-on-Wine, I've seen other posts about it but I don't believe the guy ever got a solution. The requirements for GH3 are steep (requires dual-core, at least a 7600 videocard and 1GB RAM) so it definitely isn't going to run in a virtual machine. Maybe I'll try running it under Wine and see if I can get it to work. 

After all, any game running under Wine where you can use a joystick should pick up the X-plorer as well.

One final thought, when I first ran FOF after getting the X-plorer working FOF went crazy when I tried to set the strum bar as Pick button. I had to run "jscalibrator", move the tremolo around and press every button. Then I just saved the config with jscalibrator, exited, and FOF works fine now. So just a heads up if your FOF or other app goes berserk when you first get your X-plorer going.

---

### Post by Niklas Schröder on 2007-12-28
ok.  thanks!  all fixed now.  :)

---

### Post by elcasey on 2007-12-30
This is still on topic, so I figured I wouldn't make a new thread.

Do we have any reports on getting the wireless controllers like the Freedom V or the new official GH controllers working? How about the Shredder (obviously I'm only concerned about the newer Shredder, since the old one sucked).

I'm wondering how successful people have been with PS2->USB adapters, specifically with the wireless stuff. I wanna rock a Flying V!

---

### Post by Mr.NiceGuy on 2007-12-30
sry for asking but where are you guys getting this radioshack adapter, i click on the link and it says its not there. i bought a crappy adapter that doesnt work and now i wan to try this one but i cant find it. plaese help.

---

### Post by macogw on 2008-01-11
> **elcasey said:**
> Why would it matter which USB port I have it plugged into?

Seems odd, but my DAP will not charge when plugged into the first USB port, but works fine on the last one.

---

### Post by Ibattou on 2008-01-12
IF you are trying to hook up a guitar hero controller, i think that the Xbox360 has a USB 1. I know that rock band has a USB guitar controller.... i wonder how that would work out with the drums..:guitar::guitar::guitar::guitar:

---

### Post by MACRI on 2008-01-23
any chance of getting this to work with Rock Band Guitar for 360?

---

### Post by Niklas Schröder on 2008-01-23
not sure...  i don't own one and am not exactly heading the xpad project.  ;)

---

### Post by elcasey on 2008-01-26
EDIT:

Not sure what was up, but I just kept retrying, remaking and recompiling and eventually it worked. Didn't look like anything was off in my original Makefile, but there ya go...

---

### Post by NoThanksM$ on 2008-02-25
Has anyone experienced a startup delay after following Niklas Schröder's instructions?  Following the instructions got the guitar working, which has been great, but it has made it so that there's a 1-2 minute delay on the Ubuntu splash screen, when the progress bar is about 20% of the way across.  I wouldn't mind the delay itself, but it seems to have resulted in breaking VMWare Server.  As confirmation that this is the problem, after a recent update to the Headers, the guitar stopped working but the delay was gone AND VMWare Server worked again.  once I went through the instructions again, the guitar worked but the delay returned and VMWare no longer worked.

---

### Post by Niklas Schröder on 2008-02-25
The solution to the problem is to plug the guitar in AFTER the progress bar gets past the 20ish% mark.  It's a dirty, fix, but a fix nonetheless.

---

### Post by mmasloski on 2008-03-05
Nicklaus - I can't thank you enough.
It could not be simpler - I am loving Frets now!!!

---

### Post by Niklas Schröder on 2008-03-05
You're very welcome.  :)  Glad all my testing and writing payed off for someone.

---

### Post by NoThanksM$ on 2008-03-09
Thanks for your reply, Niklas, I'll give it a shot.  ( I would have replied sooner, but I thought I was getting email updates to this thread and I guess I wasn't.)

Really appreciate you putting in the time to write up the instructions and continue monitoring the thread - this is the only thing out there I've found to get the guitar working in Ubuntu.  Thanks!

---

### Post by Niklas Schröder on 2008-03-09
Lol.  You're welcome.  It was my pleasure.  Twas quite a learning experience on my part.  ;)

---

### Post by stfudonnie on 2008-03-19
Ummm how long will the weird characters scroll for? Mine have been scrolling and beeping for about 10 minutes now and still going.

I also got a Segmentation fault on the last modprobe, I also had to sudo all the modprobes, otherwise they wouldnt work. but cat still showed weird characters as you said it would. Problem is it doesn't show any sign of stopping.

Using Gutsy with the white xplorer GH2 360 controller.

Update: After a while my PC locked up and after rebooting, my Xserver was borked! I could not get into Ubuntu, getting a textual message that no screens were detected (funny, considering I got this message on my screen). Using recovery mode, I used Envy to remove then reinstall my nvidia drivers and now I'm back in. I have no clue what went so horribly wrong during my attempt. I followed your instructions to the letter.

---

### Post by Niklas Schröder on 2008-03-20
Hmmm.  NO IDEA what went so wrong with yours...  but the strange character scrolling is just a sign that it worked.  You don't have to let them scroll.  I'm guessing the problem was that you let them scroll too long or something.  Just try again and close out the terminal.

---

### Post by zman0900 on 2008-03-20
> **Niklas Schröder said:**
> ok.  here's a *rough* version.  i'll refine it a little tomorrow, but for now, i'm off to bed.  ;)

Thank you so much, it worked perfectly for me.:guitar:

---

### Post by Niklas Schröder on 2008-03-20
Lol.  I'm getting a lot of attention now!  :p

---

### Post by zman0900 on 2008-03-20
So, I've gotten my controller to work in Ubuntu gusty, but there's one major flaw.  Once I unplug the controller, I cannot plug it back in and have it work until after I restart the computer.  I've tried running ```
sudo modprobe -r xpad
``` both before and after removing the controller, but either way, modprobe freezes up and when I check in the system monitor, it says it is interruptible.  When I plug the controller back in after this, nothing happens at all.  Normally, the lights flash then go off, but that doesn't happen, and the buttons don't work.  If I restart first, then it works fine again until the next time I unplug.  With a little snooping around in xpad.c, I found this code, and it is making me wonder if the driver is either not getting the usb disconnect message, or if it is just not handling it properly.  

```
/**
 * driver init entry point
 */
static int __init usb_xpad_init(void)
{
	int result = usb_register(&xpad_driver);
	if (result == 0)
		info(DRIVER_DESC " " DRIVER_VERSION);
	return result;
}

/**
 * driver exit entry point
 */
static void __exit usb_xpad_exit(void)
{
	usb_deregister(&xpad_driver);
}

module_init(usb_xpad_init);
module_exit(usb_xpad_exit);

```

Has anyone else experience this problem?  Does anyone have any idea how to fix this, or work around it?

---

### Post by Niklas Schröder on 2008-03-20
Everyone's experienced this.  It's just a bad driver.  At least it works though.  If you find a way around it, be sure to let us know!

---

### Post by zman0900 on 2008-03-20
Ok, at least I know it not my config causing the problem.  My only thought for fixing it was possibly changing the usb_xpad_exit function so that it returns and integer instead of void, like the way the usb_xpad_init function is, but I have no idea what the requirements of the module_exit() thing are.  My idea was to change the code like so:
```
/**
 * driver exit entry point
 */
static int __exit usb_xpad_exit(void)
{
	int result = usb_deregister(&xpad_driver);
	return result;
}
```

I'll give it a try and see what happens...

[EDIT] Nope, it won't compile that way. I get:
```
make modules -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/dan/.xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/dan/.xpad360/xpad.o
/home/dan/.xpad360/xpad.c: In function &#8216;usb_xpad_exit&#8217;:
/home/dan/.xpad360/xpad.c:639: error: void value not ignored as it ought to be
/home/dan/.xpad360/xpad.c: In function &#8216;__exittest&#8217;:
/home/dan/.xpad360/xpad.c:644: warning: return from incompatible pointer type
make[2]: *** [/home/dan/.xpad360/xpad.o] Error 1
make[1]: *** [_module_/home/dan/.xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2
```

---

### Post by the_darkside_986 on 2008-04-16
Will there ever be a package of this? I can't even get this to work now.

---

### Post by Niklas Schröder on 2008-04-16
I've actually moved over to Mac OS X now and don't plan on putting together a package myself (I was never able to do that in the first place).  But anyone else who's willing is welcome to.

---

### Post by Erik765 on 2009-07-01
Hey all. I found this thread, when researching ways to get my guitar hero 3 controller working in Linux.

Maybe it's time to revive it ;)

I've tried gizmod, it recognizes the controller as being plugged in, but it won't pick up events from it (when viewing it in debug mode)

I then tried the instructions on this site and when I type make I get this

> erik@erik-desktop:~/.xpad360$ make        
make modules -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/erik/.xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/erik/.xpad360/xpad.o
/home/erik/.xpad360/xpad.c: In function &#8216;xpad_open&#8217;:
/home/erik/.xpad360/xpad.c:382: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
/home/erik/.xpad360/xpad.c: In function &#8216;xpad_close&#8217;:
/home/erik/.xpad360/xpad.c:408: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
/home/erik/.xpad360/xpad.c: In function &#8216;xpad_probe&#8217;:
/home/erik/.xpad360/xpad.c:496: error: &#8216;struct input_dev&#8217; has no member named &#8216;cdev&#8217;
/home/erik/.xpad360/xpad.c:497: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
make[2]: *** [/home/erik/.xpad360/xpad.o] Error 1
make[1]: *** [_module_/home/erik/.xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [all] Error 2

Any ideas what this could mean?

I'm running Kubuntu 8.10

---

### Post by MasGui on 2010-06-13
@zman0900

this is not the way to do it. module_exit(usb_xpad_exit); mean that when the module will be remove with the rmmod command, the usb_xpad_exit function will be called.

You can read more about linux driver here: [http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)

---

