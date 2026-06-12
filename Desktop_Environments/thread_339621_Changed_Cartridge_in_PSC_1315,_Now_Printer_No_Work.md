---
title: "Changed Cartridge in PSC 1315, Now Printer No Worky"
date: 2007-01-16
forum: Desktop Environments
---

### Post by rajan on 2007-01-16
Hi all, I am having a problem with my PSC 1315 in that it does not want to print in black ink even though I have just changed the cartridge with a new HP 56 black ink cartridge. The printer stopped printing in black a few weeks ago and i ordered a new cartridge thinking that it was simply that there was no ink, but now I'm not so sure. Here are the details of how i've tried to fix this:

1. I changed the cartridge, took all the packaging off (I say that because I have made mistakes that are stupider than that), restarted the computer and printer several times since then. 

2a. Googled

2b. Followed these instructions:
[http://www.ubuntuforums.org/showthread.php?t=265344](http://www.ubuntuforums.org/showthread.php?t=265344)
this thread is very useful, but unfortunately not for me. It did not solve my problem. 

3. I have restarted cups by using 
```
sudo /etc/init.d/cupsys restart
```

4. uninstalled and reinstalled the printer

5. done this --> ](*,)  a lot

None of these things worked and I was hoping that I could get some assistance from someone. Any time I print text from emacs or firefox or something, I only get green ink.

Thanks a lot for reading and for any help you can give.

---

### Post by rajan on 2007-01-17
Update:
Ok so I finally got the printer to print in black and i did this by changing the printer's properties under the "advanced" tab. specifically, I changed the "Resolution, Quality, Ink Type, Media Type" field to include both color and black inks. This sounds simple, but nothing told me it had been changed (and i didn't change it). I assume that once the black cartridge went out, ubuntu recognized this and switched to printing only in color. I have heard that printing on a cartridge that doesn't have ink will ruin a print head so i assume that this is the reason for this automatic switch. 

Is this the only thing to do after you switch a cartridge, or is it also necessary to restart cups or any of the other things i did?

thanks

---

