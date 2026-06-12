---
title: "Boot failure on &quot;GNOME Display Manager&quot;"
date: 2009-06-16
forum: General Help
---

### Post by AEstergaard on 2009-06-16
Hey all,

So, Ubuntu N00b here.

I formatted my XP box and installed 9.04 from a disc recently and things have gone swimmingly. My video card is an older ATI Radeon X1650 Pro 512MB which is no longer supported. Not knowing that, I tried a few driver setups while Ubuntu was working. No luck, but my box kept on going.

Then, about a week ago, I turned off my tower before heading out of town for a weekend. I have rebooted before, but not powered-off for any length of time.

Returning home, I turned on my PC (3.0Ghz CPU, 1Gig RAM, 120GB HD) only to have Ubuntu fail to boot.

The particular style of failure is such that it seems to boot as normal - loading GRUB and giving me the option to get to the menu before booting from the HD (hd0,0). Then the three-part-circle logo with "Ubuntu" next to it pops up with the red loading bar beneath it. That proceeds to go about 1/3 yellow then it hops over to a text list of boot activity. 

Everything there proceeds in what seems to be a normal fashion. Then it gets to the GNOME Display Manager, spits out two more lines faster than I can read, then the display goes black with a smattering of horizontal red streaks across the top inch of monitor with some green and purple streak clusters below.

That's where it stops. :(

I have tried going into the menu, booting into safe mode and autofixing graphics problems. That compressed the red and green to where the red takes up about a half-inch now and there is more purple with the green, but nothing else has changed.

I've tried leaving it for a length of time to see if it will load properly, but that hasn't helped. Not even punching in my u/p combo at the end of that does anything I can see.

A Linux-savvy friend suggested getting into the boot menu and editing the kernel launch to include a "3" in it so as to disable the graphics, or to include a "1" to disable everything.

These sound like great ideas, but I don't know how to edit the boot argument to include them properly. Here is my kernel boot argument in case it helps any:

kernel  /boot/vmlinuz-2.6.28-11-generic root=UUID=da190219-9bcf-41be-8ecd-4fe9fddf0b59 ro quiet splash

So, apologies if this is overshare on the details but I'm putting out as much info as I can in the hope that someone can help me out with this.

Cheers,
Adrian

---

### Post by scrooge_74 on 2009-06-16
Try hitting control + alt + F2 after it boot so you can go into another console and maybe you could work from there in text mode.

most likely your video card is to blame, either drivers are not working for it or config got screwed.

Check [here]("http://www.linuxquestions.org/questions/linux-hardware-18/config-trouble-with-ati-radeon-x1650-pro-512mb-610120/") for solutions maybe this will help

---

### Post by AEstergaard on 2009-06-16
Hello Scrooge_74,

Thanks for chiming in on my problem!

I've rebooted and tried the Ctrl+Alt+F2. I did it during the boot sequence where I get a text list of the devices loading as Ubuntu boots up. That turned my screen black save for a blinking white cursor in the upper-left corner. After a while, the text list of loading devices returned with a space between each line this time. They seemed to be about halfway through the usual list and when it hit the GNOME Display Manager it crapped out again.

I would try this after Ubuntu boots save that it doesn't seem to actually boot successfully so I'm a bit stuck there.

To make this even more interesting, I haven't a clue how to use Ubuntu/Linux in text mode so even if I do get there, it's going to be tricky. :( 

I'll start going through that site you linked to for other help but I'm still not sure how to get to a state where I can interact with my computer to apply anything I find there.

Cheers,
Adrian

---

### Post by scrooge_74 on 2009-06-16
Sorry, my mistake.  You should hit the CTR+ALT+F2 after it boots and craps

:D  

The idea is that when it craps it is suppose to be at the GDM login screen, so you can then switch to a console and try to fix it from there.

Do you have a live CD you could use to see it at least it will start from it? (That way you can rule out that the video card is damage)

---

### Post by AEstergaard on 2009-06-17
Oh, the graphics card is fine - it displays a batch of graphics as it starts to boot.

Now, I've managed to boot from the install CD - could I get an assist on setting the HD OS graphics drivers back to the default install settings?

If I could get that done, I should be back in business.

Cheers,
Adrian

---

### Post by scrooge_74 on 2009-06-18
Try reading the settings on the xorg.conf that the system is using while under the LiveCD and then modify the xorg.conf that is installed in the HD

---

