---
title: "My first printer and I don't know what to do..."
date: 2009-05-05
forum: General Help
---

### Post by t0p on 2009-05-05
I was given a printer the other day - an **Epson Stylus D78**.  This is the first printer I've ever had, and I have no idea how to make it work with my computer.

I'd really appreciate it if someone could point me in the right direction with this.  I'm running Hardy on my (x86) machine.

---

### Post by stretch427 on 2009-05-06
Well I guess the first place to start is to plug it in and see if Hardy recognises it. From there maybe try Epson's website see if they list any Linux drivers or see if other people have installed that printer.

---

### Post by t0p on 2009-05-06
Okay... Hardy recognizes the printer.  But sometimes it doesn't.  I've installed various utilities to try and communicate with the thing, and I'm getting very varied results.

For instance, **escputil**.  I use escputil to check the printer's status and I get a nice reply:

```
t0p@ubunty:~$ escputil -s -r /dev/usb/lp0
Escputil version 5.0.2, Copyright (C) 2000-2006 Robert Krawitz
Escputil comes with ABSOLUTELY NO WARRANTY; for details type 'escputil -l'
This is free software, and you are welcome to redistribute it
under certain conditions; type 'escputil -l' for details.

Unknown printer Stylus D78!
Status: Error
Error: Ink out
Ink Levels:
        Ink colour       Percent remaining
              Cyan                       0
            Yellow                      15
           Magenta                       0
             Black                      21
```

Lovely job.  But I run the same command a moment later and I get jack:

```
t0p@ubunty:~$ escputil -s -r /dev/usb/lp0
Escputil version 5.0.2, Copyright (C) 2000-2006 Robert Krawitz
Escputil comes with ABSOLUTELY NO WARRANTY; for details type 'escputil -l'
This is free software, and you are welcome to redistribute it
under certain conditions; type 'escputil -l' for details.

Cannot open /dev/usb/lp0 read/write: Device or resource busy

```

*Busy?*  Busy doing what?  I haven't told it to do anything...

Similar story with **mtink**.  One moment I get a nice result, the next I get a nasty one...

As for **inkblot**: when I first tried it out, it recognized the printer fine; but every time since it scans for printers and says there are none connected... Grrr... :mad:

I don't know if it's down to dodgy connections on the printer, or the computer or what.  Later on I'll be able to try the printer with another computer, one running intrepid.  Maybe things will go better with that.  I dunno... like I said, I've never had a printer before.  Flaming thing!

One thing I want to know: I've tried getting it to print a test page but to no avail - hardy says the job's "processing" but nothing happens.  I know the ink situation is pretty dry: 0% cyan, 15% yellow, 0% magenta, 21% black.  Is it normal for the printer to not print a test page when ink levels are like this?  Or is this also down to dodgy connection/whatever's going on?  A n00b question perhaps, but I don't know...

---

### Post by wpshooter on 2009-05-06
Have you simply went into the printer section/function of Administration to try to see if there is a Ubuntu/Linux print driver included in Ubuntu for that particular Epson printer ?

---

### Post by t0p on 2009-05-06
> **wpshooter said:**
> Have you simply went into the printer section/function of Administration to try to see if there is a Ubuntu/Linux print driver included in Ubuntu for that particular Epson printer ?

Indeed I have!  The Printer Config window recognizes it and says it uses the Gutenprint 5.0.2 driver.  So it should work, yeah?

*So why doesn't it work?!!*

:(

---

### Post by stretch427 on 2009-05-06
Just for the record if ink levels on certain  printers are too low it might not print. And seeing as how injet cartridge level indicators are not very good at all. I would try popping out and putting the cartridges back in. sometimes it fixes that problem.

---

### Post by wpshooter on 2009-05-07
> **t0p said:**
> Indeed I have!  The Printer Config window recognizes it and says it uses the Gutenprint 5.0.2 driver.  So it should work, yeah?

*So why doesn't it work?!!*

:(

Are there other listed print drivers for this particular printer ?

If so, have you tried all of the ones listed ?

---

