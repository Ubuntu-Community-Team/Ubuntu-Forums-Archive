---
title: "Slooow BIOS boot-up on 531"
date: 2007-12-06
forum: Dell  Ubuntu Support
---

### Post by derby007 on 2007-12-06
Has anyone else got a slooow booting BIOS, I have an new Inspiron 531, BIOS Rev 1.0.3. I then upgraded to BIOS 1.0.8 but my BIOS still hangs (or shows the BIOS screen/splash) for **14seconds**. 
Note: my other Dell Dimension has A03 BIOS and its screen only shows for about 1/2 a second  !! (u have to be quick to get into that BIOS !)

---

### Post by inchaos on 2007-12-06
The only time my BIOS has done that was when it was redetecting my hardware settings because I had changed the amount of RAM.

Usually, if there are no changes, your BIOS won't do this scan on every boot.  It sounds like it is for some reason.

Check the Dell website?  I'll do some poking around as well...

---

### Post by derby007 on 2007-12-07
So am I the only one with a slow BIOS??????? I doubt it. Note: this is a new PC & I havent made any changes. I wonder is there an option in the BIOS somewhere to speed it up, ie. untick some self test or scan as inchaos mentions.

---

### Post by inchaos on 2007-12-07
Actually, I'm pretty sure there is.

Let me reboot and check out my BIOS to see what options I've got, my Dell is pretty new as well.

---

### Post by inchaos on 2007-12-07
Ok.  At boot, press F2 to get into your BIOS.
Go to POST test (Power On Self Test) and make sure your 'Fast Boot' option is set to 'Minimal'.  That way it will just go with the last config settings that worked and won't try to redetect your hardware unless you've changed something.

Hope that helps.

---

### Post by derby007 on 2007-12-07
Cheers....I will give it a whirl tonite.......

---

### Post by derby007 on 2007-12-08
I didnt see any POST option, but I did see 'Fast-Boot' and its set to Enabled. But I still have a sloooow BIOS startup.  :(

---

### Post by inchaos on 2007-12-08
:(

I don't know what to tell you...I'll keep searching.

---

### Post by luctor on 2008-04-04
I got an 531 too, and got the same problem
other people too

[http://www.dellcommunity.com/supportforums/board/message?board.id=dim_bios&thread.id=57880&view=by_date_ascending&page=1](http://www.dellcommunity.com/supportforums/board/message?board.id=dim_bios&thread.id=57880&view=by_date_ascending&page=1)

only solution so far is to unplug the cardreader ... ::confused:

---

### Post by derby007 on 2008-05-09
Its a wierd one alright, its a pity they haven't fixed it, it would be interesting if someone has a 531 Dell system with this internal card reader and are booting quickly or is it happening on ALL 531 machines. Surely this was spotted during the Testing stage, ie. before shipping them !!!!!!!

---

