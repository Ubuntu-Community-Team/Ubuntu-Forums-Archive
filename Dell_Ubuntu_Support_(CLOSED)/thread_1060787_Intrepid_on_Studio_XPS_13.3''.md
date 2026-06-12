---
title: "Intrepid on Studio XPS 13.3''"
date: 2009-02-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by n.l.o on 2009-02-05
Hello

Yesterday, I tried to install Ubuntu 8.10 on my new Dell Studio XPS 13.3. :D

At first boot up everything looked OK, then it suggested me to change NVidia Drivers. After that the CLI is everything that shows up. No Gnome, fancy login screen etc. Thats one problem. :(

The second problem has got to do with the boot up. Dell has its own diagnostics partition, and I saved Vista, so when I partitioned in the Ubuntu install:

Dell Diagnostic/Recovery 6%  (15 GiB)
Vista                    37% (80 GiB)
Ubuntu 8.10              57% (~155 GiB)

In the Ubuntu install I choose GRUB, ofcourse. Now it seems it is having trouble booting, sometimes it gets stuck with a flashing marker and when I hit the Ctrl+Alt+Del it reboots and THEN I get to GRUB. Getting to GRUB I can choose between Vista and Ubuntu. Vista starts with no fuzz (typing from it atm), but Ubuntu starts with no GUI, see above. :( :(

Anyone who has prior experiences with this?

Magnus

---

### Post by superm1 on 2009-02-05
It sounds like you might have the system with hybrid graphics.  If so, there is an unfortunate interaction with the NV driver that can't handle hybrid graphics properly.  You will have to specify your PCI ID of the discrete card in your xorg.conf.

---

### Post by n.l.o on 2009-02-05
Well it looks like its something like that. I "lspci | grep VGA" and got two possibilities:
VGA nVidia GS or VGA nVidia G, with PCI:2:0:0 or PCI:3:0:0.
Tried both, were the GS almost worked.
My "Device" section in xorg.conf looks like

:code:
Section "Device"
   Identifier "nVidiaGS"
   Driver "nv"
   BusID "PCI:2:0:0"
EndSection
:code:

When i do "startx" (or reboot) the screen goes black!
Do I have to add some modes to the Screen section?
The "Screen" section is minimal/Default, as the "Monitor" section.
The identifier in the "Device" section matches the one in "Screen".

Magnus :-?

---

### Post by superm1 on 2009-02-05
Don't use the "nv" driver.  It's not supported yet by this hardware.  You'll have to use the closed nvidia driver, or vesa.  Closed nvidia is my recommendation.  177.82 allows you to be able to suspend...

---

### Post by n.l.o on 2009-02-18
Never quite solved it, but Dell came and replaced motherboard, screen and HDD. Now the fan runs at full speed all the time instead. Considering that the unit is less than 2 weeks old, I am returning it to Dell and buying another brand. Dell will have to wait another XX years before I try them again. 

Good try considering the individual parts of the laptop, but failing to comply with common service goodwill and making the parts cooperate into a good laptop is were they fail.

If any moderator reads this, I guess you can close the thread.

Cheers
Magnus

---

### Post by djvishnu on 2009-05-20
+1! I have the same reboot-issue.

Whenever i reboot/boot i have to wait for the flashing marker and press CTRL-ALT-DELETE, really annoying.

I believe this started happening after i installed grub. And since it hangs right after bios, i'm blaming grub for now..

I have no idea on how to start debugging grub, although i'd like to try if i knew where to start. :)


actuall, +2. a friend of mine also has the exact same issue.

---

### Post by thiefy on 2009-05-20
i'd say this is fixed in jaunty. or with the 180 graphics drivers.
i have this model, and i do not have any boot problems.
i've del'd the evil dell partition and del'd the vista and recovery stuff.
so, i have windows 7 and jaunty dual booting.
jaunty is great except that the battery life is a joke - 2 hours i'd say.
and the whole system crashes whenever i close firefox (jaunty took the ctrl, alt, backspace away)

---

### Post by djvishnu on 2009-05-21
> **thiefy said:**
> i'd say this is fixed in jaunty. or with the 180 graphics drivers.
i have this model, and i do not have any boot problems.
i've del'd the evil dell partition and del'd the vista and recovery stuff.
so, i have windows 7 and jaunty dual booting.
jaunty is great except that the battery life is a joke - 2 hours i'd say.
and the whole system crashes whenever i close firefox (jaunty took the ctrl, alt, backspace away)

I have jaunty and 180, and the problem persists.

I upgraded from Intrepid, how does this affect the grub installation? Is it updated as well?

A dell guy is coming over to change my display tomorrow, I'll have him take a look at it, though i fear he'll just tell me to recover the preinstalled vista.

---

### Post by n.l.o on 2009-05-22
When I had my Dell XPS 13 they changed my display as well. Also the HDD and the motherboard... I returned it the next day. 
Dell is not an option any longer.
I say, return yours as well (I now, a bad solution to an existing problem, but a lot easier).

Cheers m8!

> **djvishnu said:**
> I have jaunty and 180, and the problem persists.

I upgraded from Intrepid, how does this affect the grub installation? Is it updated as well?

A dell guy is coming over to change my display tomorrow, I'll have him take a look at it, though i fear he'll just tell me to recover the preinstalled vista.

---

### Post by thiefy on 2009-05-22
they replace the hard drive so that when they leave your house, you have a pruter that has their image loaded from factory.
it's done so that they don't have to ghost it.
if your keyboard j button doesn't work, i bet when they fix that, they'll replace the hard drive as well.

keep in mind, when you return it, what you get back - your stuck with. 
so consider - how bad really is my new laptop?
my cd rom shakes the whole pruter like crazy, but i'm not returning it, i'm just using the cd rom less.
haha

---

### Post by djvishnu on 2009-08-25
I have solved the reboot-CTRL-ALT-DEL issue with ubuntu on Dell Studio XPS 13.3.

Howto:

1. Get a Non-Dell charger
2. Insert it with reversed polarity. You'll hear a small poof, and you will no longer be able to charge your battery.
3. Forget what you did in step 1. and 2., then call Dell and ask them what is wrong.
4. (this one is automatic) Dell replaces your motherboard, and everything works fine.

Let me know if this works out for you.

---

### Post by n.l.o on 2009-09-11
Thats just hilarious. My advice is still not to buy crap from Dell. Try ASUS or even better; IBM instead.



> **djvishnu said:**
> I have solved the reboot-CTRL-ALT-DEL issue with ubuntu on Dell Studio XPS 13.3.

Howto:

1. Get a Non-Dell charger
2. Insert it with reversed polarity. You'll hear a small poof, and you will no longer be able to charge your battery.
3. Forget what you did in step 1. and 2., then call Dell and ask them what is wrong.
4. (this one is automatic) Dell replaces your motherboard, and everything works fine.

Let me know if this works out for you.

---

