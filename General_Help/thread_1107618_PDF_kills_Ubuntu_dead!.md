---
title: "PDF kills Ubuntu dead!"
date: 2009-03-26
forum: General Help
---

### Post by ChrisC on 2009-03-26
Tesla Motors announced their Model S sedan today, and they have a data sheet with the specs.  Loading this spec sheet PDF kills my Ubuntu machine!  Evince loads and then proceeds to thrash the hard drive with no end in sight.  The first time I had to power cycle the machine because I couldn't even get a terminal window open (and Alt-F2 / Alt-Backspace wasn't doing anything either).  The second time I had a terminal window open and was able to determine the PID and kill it before it bogged down too hard.  The third time ... well, pretty much the same thing.

CAUTION:  THE FOLLOWING URL WILL KILL YOUR UBUNTU MACHINE
[http://www.teslamotors.com/display_data/Spec_ModelS_US.pdf](http://www.teslamotors.com/display_data/Spec_ModelS_US.pdf)

Can someone examine this and see why it's so lethal to Ubuntu 8.04's version of Evince?  And takes down the OS with it?

---

### Post by DeathOnJuice on 2009-03-26
Just saying, if this is true, you should really make that not a link. Perhaps put a space in the URL so people have to be really sure before they click it.

---

### Post by bhishan on 2009-03-27
nothing happened when I clicked it. its a cool car.

---

### Post by DeMus on 2009-03-27
> **bhishan said:**
> nothing happened when I clicked it. its a cool car.

Indeed, I opened the pdf file and nothing happened. So, something must be wrong with the OP's installation.

---

### Post by kanikilu on 2009-03-27
Took a few seconds to load, but otherwise, no problems viewing that PDF in evince here...

This also opened fine in xpdf, but interestingly did not open (and produced an error) in gv (ghostview) :???:

---

### Post by Agent ME on 2009-03-27
Judging from the replies, it sounds like a problem with the topic poster's machine, but then again if it did act up for anyone else, they wouldn't be able to immediately post their problem :P


Er, are you using Ubuntu 8.04? Does it do this with 8.10?

---

### Post by kaibob on 2009-03-27
I tried to directly open the PDF in Evince and got a lot of disk-thrashing. Finally, after a few minutes, the PDF did open, but the disk thrashing continued. 

I next downloaded the PDF and found that it contained 635 KB, which should not be a problem. I then tried to open the downloaded copy in Evince, but once again experienced the disk thrashing. 

I opened the downloaded PDF in the Imagemagick display utility and it opened but in reverse video (see screenshot below). I checked the PDF with pdfinfo and did not get any error messages. 

So, I don't know what's going on but there does seem to be a problem. It didn't harm my computer in any way, though.

Great looking car, but I noticed that deliveries don't begin until 2011.

---

### Post by heindsight on 2009-03-27
I suspect there may be something wrong with that PDF after all. When I tried to open it in evince (2.22.2-0ubuntu2), evince proceeded to devour memory at an alarming rate (I killed it before it got completely out of hand).

I can open it in Adobe Reader (acroread-8.1.3-0medibuntu0.8.04.1) but it is incredibly slow...

---

### Post by ChrisC on 2009-03-27
Yeah, I have no doubt that there's something wrong with the PDF, but it shouldn't bring the OS to its knees.

I did not let the hard drive thrashing continue beyond a couple minutes to see what would happen.  I could see from what monitoring was working that it was progressively chewing through resources.

Can someone submit this into the general Ubuntu bug tracker, or better yet the Evince bug tracker, so that they can look at it?

---

### Post by LowSky on 2009-03-27
it may not be a ubutu bug, it could be a bad PDF, ever think of that?

try one of the other 3 PDF viewers, try using adobe's if worse comes to worse, I mean they are the PDF masters aren't they?

---

### Post by bapoumba on 2009-03-27
Just tried with top running. evince (Hardy) was eating up > 70% memory and could not load the pfd..
Closing evince took a while.

Edit: now anything I'm doing I hear the HD and I'm using some swap, which I usually do not.
```
bapoumba@SonyBlue:~$ free
             total       used       free     shared    buffers     cached
Mem:       1025780     373388     652392          0       1808      57720
-/+ buffers/cache:     313860     711920
Swap:       979924     277884     702040

```

---

### Post by Rallg on 2009-03-27
I don't have the courage to try the PDF. But...

Maybe the PDF contains multimedia content, automatically launched by enclosed JavaScript? Considering that it is a car advertisement, that would not surprise me.

---

### Post by bhishan on 2009-03-27
i opened it with adobe reader, took a second to load. No other troubles.

---

### Post by ChrisC on 2009-03-28
Thanks bapoumba and others for confirmation of the problem :)

It could just be a problem with evince, and could be just be a problem with evince and 8.04 LTS.  Anyway, any problem that kills the OS is a serious problem ...

---

### Post by joshedmonds on 2009-05-18
I can confirm this on 9.04 on an Acer Aspire One w/- 1GB ram. I had to REISUB after several minutes of unresponsiveness.

I have had a few problems with evince freezing and consuming all available memory as it does not use tiled rendering (though it is on the roadmap [http://live.gnome.org/Evince/Roadmap]("http://live.gnome.org/Evince/Roadmap")), which I was able to get around by setting the default page view to 'fit page width', however this is different.

---

