---
title: "Ubuntu Just Randomly Crashing.."
date: 2005-06-10
forum: Desktop Environments
---

### Post by Rickie on 2005-06-10
Yeh, as it says in the title Ubuntu just keeps randomly crashing, i can't do anything except move the mouse cursor, if i leave it a couple mins the screen just goes black and i have to turn off the PC, i've no idea why it's doing this, but it's done it about 6 times so far today, Can anyone help? It's really annoying :(

Specs: 800Mhz Duron, 768MB Ram, Gf2, Ubuntu is installed on my 80GB 7200RPM WDC.

Edit:\\ Also, it doesn't save my default resolution (1152*864 @ 72Hz) It uses 1024 * 768 @ 85hz instead, even when i tick the box for default :s

---

### Post by Njall on 2005-06-10
Rickie, 
 
   I am concerned  ](*,)  that you have a hardware problem.   I will make some basic suggestions to check this possibility out.  First however, make a backup of any and all data that cannot be replaced such as your email, accounts, documents and so on.  Don't wait a moment longer.  Get it done now.  That's an order!

1. Check that all the fans are working.  If you come to expect you have a heat problem try removing a case cover to let air move around the system more freely.

2. If the motherboard is so equipped check voltages in the BIOS as the system boots.  You might have a bad power supply.  A power supply can fail gently enough that all it does is supply slightly bad power to the system.  But "slightly bad" is way too much.  

One thing which can cause "slightly bad" voltages is over taxing your power supply.  Asking, as it were, for too much power from it.   At [JS Custom PCs](http://www.jscustompcs.com/power_supply/) is a calculator which can help you determine this.  The power rating of your power supply should be visible close to where the power cord enters the machine.

3. If you can, once the system has booted, examine dmesg to see if there are some glaring errors.   Here I would bee looking for either disk or, more likely, memory errors.  If you see either respond appropriately.

4. If you can open up the case and examine the motherboard.  Look for those little vertical "cans", typically blue or purple, that have aluminium tops with an X impression on them.  Do any of them have something, typically beige or brown, oozing out?  If so, you have bad capacitors which are quite likely are allowing extraneous noise to get into the data paths.  Unfortunately, unless you are a decent technician, you will need a new motherboard.

5.  If you can get [Ultimate Boot CD](http://ubcd.sourceforge.net/) on a CD, boot it.  It has the programs to non-destructively test your disk drives; your memory; and generally run stress tests against your system.  It has helped me isolate hardware problems.

6.  If you can try a different video card.  Is that the "Gf2"?

The system may not be saving your changed video setting because it is crashing.   Treat that as just a symptom for the time being.

I don't know if this is your problem; but eliminating these issues will help, somewhat, to isolate the problem as less likely to be hardware.

---

### Post by NeTo on 2005-06-10
If you have the nvidia driver installed, make sure "RenderAccel" is disabled in xorg.conf. That can cause crashes in graphic intensive programs.

Open the /etc/X11/xorg.conf file and add "Option" "RenderAccel" "false" in the Device section. This particular issue is discussed [thread=24703]here[/thread].

---

### Post by Rickie on 2005-06-10
> **Njall]Rickie, 
 
   I am concerned  ](*,)  that you have a hardware problem.   I will make some basic suggestions to check this possibility out.  First however, make a backup of any and all data that cannot be replaced such as your email, accounts, documents and so on.  Don't wait a moment longer.  Get it done now.  That's an order!

1. Check that all the fans are working.  If you come to expect you have a heat problem try removing a case cover to let air move around the system more freely.

2. If the motherboard is so equipped check voltages in the BIOS as the system boots.  You might have a bad power supply.  A power supply can fail gently enough that all it does is supply slightly bad power to the system.  But "slightly bad" is way too much.  

One thing which can cause "slightly bad" voltages is over taxing your power supply.  Asking, as it were, for too much power from it.   At [JS Custom PCs](http://www.jscustompcs.com/power_supply/) is a calculator which can help you determine this.  The power rating of your power supply should be visible close to where the power cord enters the machine.

3. If you can, once the system has booted, examine dmesg to see if there are some glaring errors.   Here I would bee looking for either disk or, more likely, memory errors.  If you see either respond appropriately.

4. If you can open up the case and examine the motherboard.  Look for those little vertical "cans", typically blue or purple, that have aluminium tops with an X impression on them.  Do any of them have something, typically beige or brown, oozing out?  If so, you have bad capacitors which are quite likely are allowing extraneous noise to get into the data paths.  Unfortunately, unless you are a decent technician, you will need a new motherboard.

5.  If you can get [Ultimate Boot CD](http://ubcd.sourceforge.net/) on a CD, boot it.  It has the programs to non-destructively test your disk drives said:**
> 

Yeah, the graphics card is the Geforce 2, i don't have any others :/

I'll try that UBCD and let you know if it finds anything :)


[QUOTE=NeTo]If you have the nvidia driver installed, make sure "RenderAccel" is disabled in xorg.conf. That can cause crashes in graphic intensive programs.

Open the /etc/X11/xorg.conf file and add "Option" "RenderAccel" "false" in the Device section. This particular issue is discussed [thread=24703]here[/thread].

Damm, that's proberbly my problem, it's all listed there, i'll try and disable that and Restart X when my download has finished  \\:D/

---

### Post by Rickie on 2005-06-11
Right, ran most of the test's on the UBCD, no errors found on my ram, or harddrive, everything else i tested was fine too. Since i've disabled the RenderAccel, it hasn't crashed yet, thanks Guys :)

---

