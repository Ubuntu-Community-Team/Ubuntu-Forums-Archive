---
title: "Why is printing in Ubuntu so bad?"
date: 2009-05-26
forum: General Help
---

### Post by brntoki on 2009-05-26
When I say "bad", I don't mean that I'm not able to get my printer installed and working, or that the printed page is illegible.  I'd even say that the print driver itself, as far as the quality of the actual printed output, is superior to the Epson driver in Windows.  So, serious kudos for Gutenprint and all.

Way over on the other hand, however, why in the crap is it so hard to get apps to print uniformly?  I get crap page setup from one application, and the next one looks fine.  I'm mainly talking about print positioning and orientation here.  If I print with, say, Scribus (if it prints anything at all), it will start printing halfway down the page. OK!  Export it to PDF and I'll be all set (not that it's the most acceptable workaround. Then you have duplicate documents laying around.).  Then print the PDF from Document Viewer.  It orientates it however in the heck it wants to.  I tell it landscape and it prints portrait.  I decide to leave it alone and hope that the "automatic" orientation in the print driver will take care of it.  Nope!  Now it prints it halfway down the page and cuts off the rest.  Try printing from Foxit.  Same thing.  Playing with the settings is simply a crapshoot.  It will print however it darn well wants, but certainly not *the right way*!  Oh!  The preview button, you say?  Hahaha.  The preview always looks right.  What is the purpose of a preview that isn't what is going to be printed?  It just helps me feel confident for a few seconds before my hopes are dashed---again (and this goes for all the apps I mention here and more).

I give up and try Acrobat Reader.  Prints perfect with no fiddling (I was afraid to after my other experiences).  I then did fiddle a little and found that, low and behold, it actually did what it was supposed to.

This is by no means a recent problem.  I've always needed to take some high blood pressure meds before trying to print in Ubuntu---that and have plenty of A4 paper on hand.

In my opinion, automatic orientation is a bad thing.  It seems a culprit many times.  It doesn't jive well with all applications in my experience.  The thing is, you never know when it will or will not work.  If I set it directly with the printer driver, then again with the application's interface, it doesn't seem to always work.

Anyway, it's a frustrating experience every time I have to print.  Aaaargh!

Okay, this is obviously very rantish.  But I would like to know of others' experiences.  Are there ways to make printing life easier?  I've had to boot Windows to print stuff on many occasions.

Epson PM-4000PX

---

### Post by ad_267 on 2009-05-26
I've never had any problems like this. I've got an old HP Deskjet 710.

---

### Post by hyperdude111 on 2009-05-26
Never had any problems with 
HP PSC-950 or
HP C6380

Both work perfectly.

---

### Post by brntoki on 2009-05-27
Wow.  And here I thought HP was supposed to be one of the harder printers to get working.

---

### Post by ad_267 on 2009-05-27
> **brntoki said:**
> Wow.  And here I thought HP was supposed to be one of the harder printers to get working.

Well I did also used to have a Canon ip1600. Had to use the drivers for the ip2200 and was a bit of a hassle getting it working, but when it did print I didn't have any problems like this either. I think your problem must be a driver issue, although I thought Epsons were supposed to be quite well supported too.

---

### Post by tacantara on 2009-05-27
I haven't experienced any problems yet with the HP DeskJet F2280 that I installed recently.  However, I've only printed a few e-mail messages off of Evolution.  I'll take the OPs experiences as a warning, and hope for the best.

---

### Post by dmizer on 2009-05-27
You may have more options available in [http://localhost:631/](http://localhost:631/)

---

### Post by brntoki on 2009-05-27
> **dmizer said:**
> You may have more options available in [http://localhost:631/](http://localhost:631/)

Thanks, dmizer.  I have been using the localhost option as well.  My next printing sessions I think I'll try not setting the automatic rotation, though several moons ago it was buggy too, as I remember.

I suppose that I could probably get this figured out with some dedicated testing.  I don't usually have problems printing from Photoshop or anything, even using it and Qimage through Wine.  I'm thinking it's down to a handful of quirky Linux apps, really.  Like I said, I can open the same PDF in Document Viewer, Foxit, and AcroRead, and without changing any print options AcroRead prints it perfect.  When trying to change Document Viewer and Foxit settings to counter their "counter-intuitive" way of printing, it doesn't help, and often gets worse.

---

