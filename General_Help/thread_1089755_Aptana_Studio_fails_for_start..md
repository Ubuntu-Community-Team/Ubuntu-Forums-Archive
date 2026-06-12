---
title: "Aptana Studio fails for start."
date: 2009-03-07
forum: General Help
---

### Post by M03BIUS on 2009-03-07
I've just installed Aptana Studio on my Ubuntu 8.10 machine.  I had to download Java JRE for it to run and now when I start up Aptana Studio, it loads with the splash screen then nothing happens.  Nothing happens at all after the splash screen loads.  What could be the problem?  

I've tried using Kompozer, but it crashes everytime I choose something out of the File menus... plus I can't open anything.

I need a Wysiwyg html,php editor for my website.  So far I have had no luck with Ubuntu.

---

### Post by kellemes on 2009-03-07
> **M03BIUS said:**
> I've just installed Aptana Studio on my Ubuntu 8.10 machine.  I had to download Java JRE for it to run and now when I start up Aptana Studio, it loads with the splash screen then nothing happens.  Nothing happens at all after the splash screen loads.  What could be the problem?  

I've tried using Kompozer, but it crashes everytime I choose something out of the File menus... plus I can't open anything.

I need a Wysiwyg html,php editor for my website.  So far I have had no luck with Ubuntu.

Have you tried starting these programs from the terminal? This way you'll often get some output that could be informative.

By the way, Aptana never worked for me too..

---

### Post by sefs on 2009-03-14
I am having the same problem, it tells me look in some log file ... but of course I cannot decipher the gibberish there.

I also have problems with it as a plugin in eclipse.

---

### Post by sefs on 2009-03-14
I think this may work...

[http://forums.aptana.com/viewtopic.php?t=7147](http://forums.aptana.com/viewtopic.php?t=7147)

Update: This worked nicely...

The only thing i had to change was in the last line of the launch script ... I did not need to put on the "-vm /usr/lib/jvm/blah blah blah" part ... just the path to the AptanaStudio launcher.

---

### Post by martrn on 2009-03-14
> **M03BIUS said:**
> I've just installed Aptana Studio on my Ubuntu 8.10 machine.  I had to download Java JRE for it to run and now when I start up Aptana Studio, it loads with the splash screen then nothing happens.  Nothing happens at all after the splash screen loads.  What could be the problem?  I've tried using Kompozer, but it crashes every time I choose something out of the File menus... plus I can't open anything. I need a Wysiwyg html,php editor for my website.  So far I have had no luck with Ubuntu.

I tried Aptana Studio too and got it to work servral times before an update and then it was no go.  Kompozer works / should work but it is not brilliant.

It might be something to do with the java runtime engines installed on your workstation.  Sometimes changing the default java runtime engine works there is a sun JRE and a GNU java runtime engine, and also settings regarding how much memory the java engine is 'allowed' to manage.  I can't say this will work for certain though.

---

