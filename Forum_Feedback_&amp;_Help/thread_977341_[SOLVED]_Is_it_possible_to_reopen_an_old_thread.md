---
title: "[SOLVED] Is it possible to reopen an old thread?"
date: 2008-11-10
forum: Forum Feedback &amp; Help
---

### Post by akadruid on 2008-11-10
Hi,

There is an old thread here:
[http://ubuntuforums.org/showthread.php?t=283690](http://ubuntuforums.org/showthread.php?t=283690)

Which is the first hit on Google for 'Ubuntu wps' or 'Ubuntu .wps', but basically says you can't open wps files in Ubuntu. 

This is out of date, for a least 3 versions now the bundled version of OO.o has opened .wps, or you can apt-get libwps and convert them.

Is there a way to post an update to that thread?

Thanks

aka

---

### Post by lisati on 2008-11-10
One option is to start up a new thread which refers back to the old thread (as you have done here)

---

### Post by akadruid on 2008-11-10
I don't see how that solves the problem (i.e. #1 google hit incorrectly saying it is impossible to open a .wps file)

---

### Post by lisati on 2008-11-10
Unfortunately I don't use WPS files that often, so I don't have a solution at hand, but at least the question is now active again. Good luck!

---

### Post by akadruid on 2008-11-10
Sorry, perhaps I was not clear:

I found the answer, and I want to post in the original thread so others can find it easily.

Is that possible?

Currently I just get this message:
> akadruid, you do not have permission to access this page. This could be due to one of several reasons:

   1. Your user account may not have sufficient privileges to access this page. Are you trying to edit someone else's post, access administrative features or some other privileged system?
   2. If you are trying to post, the administrator may have disabled your account, or it may be awaiting activation.


---

### Post by lisati on 2008-11-10
> **akadruid said:**
> Sorry, perhaps I was not clear:

I found the answer, and I want to post in the original thread so others can find it easily.

Is that possible?

Currently I just get this message:

I just saw which subforum this is in.......

I don't think so. Some of the threads were archived as part of an update to the forum software earlier this year. Perhaps some more knowledgable forum user may be able to assist.

---

### Post by Elfy on 2008-11-10
I think the only way would be to hope a mod/admin adds to the thread for you.

---

### Post by akadruid on 2008-11-10
Hope? :)

Ah well, I will cross my fingers

Thanks for your help

---

### Post by overdrank on 2008-11-10
> **akadruid said:**
> Hope? :)

Ah well, I will cross my fingers

Thanks for your help

Post your solution and I will link it in the old thread. :)

---

### Post by akadruid on 2008-11-10
Thanks! Didn't have my fingers crossed long :)

Please add this:
> The Ubuntu version of OpenOffice.org has been able to open .wps files since at least version 2.2 (on Ubuntu version 7.04).

Alternatively, you can use wps2html to convert the .wps file.  Install like this:
```
sudo apt-get install libwps-tools
```
and use it like this:
```
wps2html document.wps > document.html
```
This also works on other distros and Windows, more information here:
[http://jamesmcdonald.id.au/it-tips/opening-wps-files-on-linux](http://jamesmcdonald.id.au/it-tips/opening-wps-files-on-linux)

---

### Post by bapoumba on 2008-11-10
@ akadruid: done ;)

---

### Post by overdrank on 2008-11-10
> **bapoumba said:**
> @ akadruid: done ;)

Thanks :)

---

### Post by akadruid on 2008-11-10
Thanks.  I have marked the thread as solved

---

### Post by bapoumba on 2008-11-10
You are both welcome :KS

---

