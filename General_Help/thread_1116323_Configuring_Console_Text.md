---
title: "Configuring Console Text"
date: 2009-04-04
forum: General Help
---

### Post by JKyleOKC on 2009-04-04
I've got one system in which the monitor (17-inch CRT) is nearing the end of its life and even with both brightness and contrast set to 100%, the white-on-black text is almost unreadable at the best of times, and totally unreadable much of the time because it is so dim.

However I've found that running a Knoppix live CD on this box produces clear, bright text during the starting process. It apparently uses the "bold" or "bright" attribute from the ancient days of DOS to add brightness.

Now I'm trying to determine how to get similar results with Hardy. Searching the forums for "console" or "framebuffer" has gotten me close a couple of times, but the "dpkg-reconfigure" command only offered me "fixed" and "VGA" as the fonts and neither seemed to have any effect.

I did find several other posts over the past couple of years that had essentially the same question, but no answers. Anybody know where the config data is stored?

---

### Post by fabricator4 on 2009-04-04
There is a gamma correction there somewhere which I've seen during installation.  I think it might be part of xorg.conf

Yep, look in the manual for Gamma.  it's part of the monitor section and can be specified as a single value or as three RGB values.  I haven't used it yet so I don't know if it's actually supported.

This is really a classic case where a hardware adjustment is the best indicated fix.  Permanent too.  Pull the cover off the monitor and look for a knob on the side of the flyback transformer (the big plastic looking thingy that has a thick lead running from the top of it and jacked into the side of the CRT.

If there's no knob on the flyback transformer, look for a pot on the PCB on the same board labeled "brightness".  

In either case turn the knob up until you seem the background at the edges go _very slightly grey, then turn it back a little.  Your monitor will now be returned to (almost) full functionality.  If the colour has gone a little weird over the years, there's three pots on the back of the video board (stuck on the very rear pointy end of the CRT tube that will adjust red, green and blue.

***WARNING***
There's high voltages in your monitor, and you have to make the adjustments with the monitor turned on.  The high voltages range from several hundred volts DC to several thousand volts on the high tension circuit to the collector (of which the flyback transformer is part - that's what that thick high tension lead going to the back/side of the CRT is for.  I'd suggest that the several hundred volts DC is actually the more dangerous part, however the HT is likely to be extremely painful and is also potentially fatal.

If you are naturally clumsy, drop things when you try to engage more than one motor skill at a time, and don't posses any appropriate electrical screwdrivers, get someone who has all these attributes to do it for you.  Please be honest with yourself if this describes you - or it could just turn out to be the worst day of your life, which isn't really worth saving a few bucks on a new secondhand monitor, is it?


Chris

---

### Post by JKyleOKC on 2009-04-04
If I were 60 again I'd try that -- but since I now live with an implanted cardiac defibrillator and have to be extremely careful about magnetic fields and electric shock I think I'll pass <grin>. Many years ago I was a ham radio nut, and one night took 2,000 volts from a transmitter power supply, so I do know to treat high voltage with respect. If I get really brave I may still open up the monitor and look for an internal brightness control. It uses two pushbuttons and an on-screen display though so it may not have a pot even internally...

I'll check for the gamma settings. The box dual-boots to Win98SE and there I've had to increase the gamma setting to 1.26 to get comfortable brightness, so this may help solve the problem. Or it may be best to just switch out with another machine that's effectively headless but does have a functional 17-inch CRT connected...

---

### Post by fabricator4 on 2009-04-04
Well wise choice, it's not worth the risk.

Old CRT monitors can be picked up for almost nothing these days, as the masses have ditched them in favour of LCD monitors but there's enough of them still around to be considered a nuisance by most.  A lot of perfectly good CRT's are going into landfill because no-one wants them.

Try all your friends/acquaintances in your area and you might be amazed how many of them have an old CRT in a back room that they intend to get rid of.  I just picked up a really nice Samsung 21" 1100p in almost perfect condition simply by asking.  It's now my main monitor and the LCD I just got has been put on reserve.  At the same time I also got a couple of 17" LG CRT's that might need some minor repair.

Good luck with the xorg.conf gamma adjustment.

Chris.

---

### Post by fabricator4 on 2009-04-04
[QUOTE=JKyleOKC;7015072]If I get really brave I may still open up the monitor and look for an internal brightness control. It uses two pushbuttons and an on-screen display though so it may not have a pot even internally...

I should have also said, all monitors still have adjustments internally.  It's how they're set up and configured at the factory (sometimes very badly)

Look for the knob on the flyback transformer first.  If it exists, that's the one you want.  Sometimes they're hard to spot - black plastic knob on a black plastic casing.  

You could always pull the monitor apart and make adjustments with it turned off.  It's possible to do it that way, it just takes a long time because you have to leave the monitor on for a few minutes to make sure it's up to running intensity before judging the adjustment you've just made.

Even with the monitor off, the HT lead to the back of CRT may have a very high potential on it.  There's protection circuits in them these days, which bleed the HT off quite quickly but if that is faulty then your only safety is in common sense.  You're probably pretty safe if you don't go digging under the big rubber cap that covers the HT lead where it jacks into the CRT.  That's part of the common sense bit  :-)

You'll want a rubber mat to put the monitor on, to make sure it doesn't short anything while running with the covers off.  A couple of layers of thick cardboard would also work.

Chris.

---

