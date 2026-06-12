---
title: "BIOS loads extremely slow, then Ubuntu won't load at all"
date: 2009-01-01
forum: General Help
---

### Post by Nimaran on 2009-01-01
Hey, I'm helping a friend out on this one, so I may not have all the details and specs needed, but I'll give it a try anyway.

The computer's BIOS loads extremely slow...... then finally once it tries to load Ubuntu it works for a tad as it is loading then the screen distorts with the cursor as an x and just sits there forever. (Oh it is a Dell Optiplex something or other, not new, but not bad)

There was nothing important on the hard drive so we tried a fresh install (what the heck why not, that fixes everything, right?) but I can't get it to install. Booted into the live CD, normal install steps, until it came to actually hitting install... I can't remember the exact error, I would get two different ones, but one of them said it just couldn't install it, the other said it couldn't install and then mentioned something about the swap partition. (and both listed the hard drive designations)

Sorry I don't have more details, oh, and the computer had been working, and I don't know what he did to it, but it sounded like he was just playing with some settings and that doing a clean install should fix it, if he had actually broken it. 

Any ideas? Thanks in advance, I know it isn't a lot to go on, but you guys rock!!

---

### Post by Titan8990 on 2009-01-01
If your BIOS load is noticeably slow, I recommend inspecting the board for physical damage. Look for things such as bulging compactors and melted plastic.

---

### Post by melojo on 2009-01-01
Do you mean Grub?

Grub menu is when it asks you what operating system to load.

---

### Post by theozzlives on 2009-01-01
> **Titan8990 said:**
> If your BIOS load is noticeably slow, I recommend inspecting the board for physical damage. Look for things such as bulging compactors and melted plastic.

Yeah, if it's slow at POST... it's not Ubuntu but hardware.

---

### Post by oldsoundguy on 2009-01-01
yep .. the bios chip .. has nothing to do with the OS.  I just had a PIII that has been giving me intermittent crap for a year or so (freezes mouse going away, keyboard disappearing, USB disappearing .. yada yada) FINALLY go .. first it went into a splash screen boot loop with the OS (or with a live CD in the drive) .. then it went into a splash screen boot loop with the NVidia card, and finally it just refused to even seek any drives.
I pulled the motherboard and we tested .. yep the chip!  But the processor and the memory are still good .. so they are bound for eBay!!

---

### Post by skern03 on 2009-01-01
> **Nimaran said:**
> Hey, I'm helping a friend out on this one, so I may not have all the details and specs needed, but I'll give it a try anyway.

The computer's BIOS loads extremely slow...... then finally once it tries to load Ubuntu it works for a tad as it is loading then the screen distorts with the cursor as an x and just sits there forever. (Oh it is a Dell Optiplex something or other, not new, but not bad)

There was nothing important on the hard drive so we tried a fresh install (what the heck why not, that fixes everything, right?) but I can't get it to install. Booted into the live CD, normal install steps, until it came to actually hitting install... I can't remember the exact error, I would get two different ones, but one of them said it just couldn't install it, the other said it couldn't install and then mentioned something about the swap partition. (and both listed the hard drive designations)

Sorry I don't have more details, oh, and the computer had been working, and I don't know what he did to it, but it sounded like he was just playing with some settings and that doing a clean install should fix it, if he had actually broken it. 

Any ideas? Thanks in advance, I know it isn't a lot to go on, but you guys rock!!

Have you reset the BIOS? There should be a jumper labeled CMOS or CMOS1 with three pins. Move the jumper from pins 1-2 to 2-3 or whatever the opposite is. You might have to look for tech specs on Dell to locate the jumpers and find out which pins need to be shorted. Anyway, let it sit a few secs, move the jumper back to the original positions, and then try rebooting. You'll have to hit a function key as I recall, but whatever, you need to edit the BIOS settings. Dell's BIOS is pretty funky - or at least it is on my Dell laptop.

As for the live CD, if you tried 8.10, it is really picky about the systems on which it will run. It loaded fine on the laptop, but wouldn't load on my desktop until I added a new HDD, and replaced the DVD drive. I'm sure the issue was with the DVD.

If you don't want to hassle with replacing the DVD, then try 8.04. It seems to be a lot more forgiving.

Otherwise, I agree with the other poster who said it smells like a hardware issue.

---

### Post by melojo on 2009-01-01
> Sorry I don't have more details, oh, and the computer had been working, and I don't know what he did to it, but it sounded like he was just playing with some settings and that doing a clean install should fix it, if he had actually broken it.


Was he making changes to the cmos setup utility or with ubuntu system settings?

---

### Post by Nimaran on 2009-01-01
> **melojo said:**
> Do you mean Grub?

Grub menu is when it asks you what operating system to load.

No, when the actual Dell logo appears and the little loading bar under it, it takes that forever then.

But, yeah, hardware, that was my suspicion as well, but I will:

1) Look for any abnormalities on the board.

2) Try the pin thing.

3) Does anyone think flashing the BIOS might hold any luck? Or is that the equivalent of the pin thing?

4) Or I will see what I could get for the parts on ebay? :)

5) Any other ideas? One last thing, whatever this problem is, does it make sense that it suddenly would have just happened, or could he have actually caused this, and if so, how?

---

### Post by melojo on 2009-01-01
> could he have actually caused this, and if so, how?
> sounded like he was just playing with some settings

Depends on what he was doing.  If he was in cmos setup making changes then yes.  Other than that probably not.

---

### Post by theozzlives on 2009-01-01
> **Nimaran said:**
> 5) Any other ideas? One last thing, whatever this problem is, does it make sense that it suddenly would have just happened, or could he have actually caused this, and if so, how?

Electronics can just stop working out of the blue.

---

### Post by melojo on 2009-01-01
> **theozzlives said:**
> Electronics can just stop working out of the blue.

Most of the reason electronics stop working is because of heat and expansion and contraction, it can loosen connections and break soldering points.

---

### Post by pietjanjaap on 2009-01-01
Flashing your bios, only do this if you think it is needded because of hardware is not working, because your hardware is broken this is not needded, this is the last thing i would do.
Also if flashing goed wrong you can not repair(normally)

Go inside bios disable picture(dell), so you maybe can see where it is stuck.(disable quickboot also). 
try different haddisk.
try different PSU.
Remove all hardware you do not need to start the pc.
Is pc clean inside?
What are temps?

If this does not work, then change all parts 1 by 1 until you find it.

---

### Post by maddog46113 on 2009-01-01
I think i know whats going on...

This has happened to me before. Check your power wires running to your hard drive(s). It could be a power supply problem. Try unplugging all drives in your PC turn it on see if the bios loads slow. If it doesnt then plug in one drive at a time until you find which one isnt working properly. If it loads slow with all the drives disconnected try the same thing only with your RAM. Take them all out put in one at a time. If thats not the problem hopefully you have an old power supply laying around you can try. If its not the RAM hard drives or power supply then its a problem with your motherboard.

---

### Post by maddog46113 on 2009-01-01
I think i know whats going on...

This has happened to me before. Check your power wires running to your hard drive(s). It could be a power supply problem. Try unplugging all drives in your PC turn it on see if the bios loads slow. If it doesnt then plug in one drive at a time until you find which one isnt working properly. If it loads slow with all the drives disconnected try the same thing only with your RAM. Take them all out put in one at a time. If thats not the problem hopefully you have an old power supply laying around you can try. If its not the RAM hard drives or power supply then its a problem with your motherboard.

**edit*** I have no idea why it double posted o.o.... sorry.

---

### Post by Nimaran on 2009-01-01
> **maddog46113 said:**
> I think i know whats going on...

This has happened to me before. Check your power wires running to your hard drive(s). It could be a power supply problem. Try unplugging all drives in your PC turn it on see if the bios loads slow. If it doesnt then plug in one drive at a time until you find which one isnt working properly. If it loads slow with all the drives disconnected try the same thing only with your RAM. Take them all out put in one at a time. If thats not the problem hopefully you have an old power supply laying around you can try. If its not the RAM hard drives or power supply then its a problem with your motherboard.

Okay, when I get a chance to look at it again I will definitely try that and post the results on here. Thanks a bunch!

---

### Post by skern03 on 2009-01-01
> **Nimaran said:**
> 

3) Does anyone think flashing the BIOS might hold any luck? Or is that the equivalent of the pin thing?



No, clear CMOS first. That will cause the BIOS to go back to day one when it was created, so your system time will be set back several years, depending on the age of the BIOS. All the settings will reset to the factory defaults. 

Recently, I had to do this a couple of times when I moved my system to a new case (Antec 900 - sweet case!!! - xmas gift from my wife). I got nothing - just a black screen, no post, nothing. Resetting CMOS and reconfiguring the BIOS fixed it.

If that doesn't help, then don't bother with flashing the BIOS. Even if resetting CMOS does help, in my experience flashing the BIOS should ONLY be done if you need to address a specific issue and you know that the BIOS upgrade will do it. In other words, if the BIOS ain't broke, don't fix it.

---

### Post by thingy87654321 on 2009-01-01
just go to the dell website and go to product support, search your computer model and update your bios version, it work for me, i had it happen on older computers tho, hope it helps

---

### Post by thingy87654321 on 2009-01-01
skern03 the bios could have a corrupt file or is a corrupt state and that would require a reflash of the flash bios

---

### Post by thingy87654321 on 2009-01-01
i have so many freaking computer laying in my office/bedroom i can build like  50 computers, maybe 3 would not have ram

---

### Post by thingy87654321 on 2009-01-02
well it still works, so it is not dead, if it is not a physical problem, it is a mental problem (memory wise) true electronics stop working, but on a computers motherboard everything worked in a group, so if one thing stops working more thingd stop working, like psu failure = nothing works
harddrive failure = cant boot  cpu failure = not booting and not operating correctly, what i am saying is that the computer is not  beeping a error code and is turning one usally leeds to a minor problem that can be fixed causing other things to work properly again

i am not being mean or trying to be a as*hole, i am just try to express myself the best way i know how, arguing about something i know about, computers, i am only 14 but i know more than most people out there about computers because that is my life, also i study computer hardware, software, and the scripting and or coding in programs.

---

### Post by melojo on 2009-01-02
I hope you get it sorted and if you do post back and let us know what it was.

Bruce

---

