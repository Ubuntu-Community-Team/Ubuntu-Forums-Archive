---
title: "Only first created user can print...."
date: 2006-01-02
forum: Desktop Environments
---

### Post by Bil-E-daKid on 2006-01-02
Hey there guys,

All of a sudden it seems (perhaps in the last month or so), only I can print on my home workstation. All other users print jobs just seem to disappear - no error messages show on screen or anything.  Intermittantly, other users *may* be able to print a test page - but not from any other application.

It looks to be some kind of permissions problem but I'm not entirely sure - and I'm not sure where to even start looking to find out.  I've searched the forums and googled for answers but have so far turned up nothing.

Could someone possibly guide me through troubleshooting this problem?

Many thanks in advance.

---

### Post by Bil-E-daKid on 2006-01-04
Sorry - wrong. Did some more digging and found that other users can print ok so it doesn't appear to be a permissions thing. 

The one user that is having a problem can now print test pages ok and can print from GEDIT.  Firefox, Acrobat and Thunderbird are some of the applications that don't print ok.  A print job shows up in the queue and then disappears after a while - with nothing coming out of the printer.

Not sure exactly why yet - any one else got any ideas for me to try?

Thanks! (I hope someone is out there!)

---

### Post by Bil-E-daKid on 2006-01-04
Just gone through recreating a new home directory for that user and also recreating user login as well. Neither worked - same non-printing result (with job showing up in the queue if I pause the printer - and then disappearing once unpaused).

I'm at a loss now unfortunately. I'd rather not do a format and reinstall but, with my lack of ability to fix the problem, that's where I'm headed.....

Anyone?

---

### Post by ritger on 2006-01-04
Gnome printing through CUPS only works for Gnome applications that support this. Thunderbird and Firefox don't support this, some for xpdf. I worked around this by installing `gtklp' (it's in the universe repository) and changing the command used to print from these programs in their options. This pops up gtklp whenever you want to print and has all the CUPS printers to choose from. 

Hope this helps.

---

### Post by Bil-E-daKid on 2006-01-06
Awesome - thanks Ritger!

I apt-got gtklp and then modified the print command in Acrobat reader and Firefox 1.5 (about:config) - this has fixed Acrobat, Firefox and Thunderbird.

You, my fellow Ubuntu-er, are a genius!!

Many thanks
Bil-E-daKid

---

