---
title: "Computer hangs after resuming from hibernation"
date: 2009-05-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by riberet on 2009-05-15
I've just realised that my dell Inspiron 1720 hangs upon resume from hibernation. This used to not happen earlier. I'm a total beginner with Linux(just a month). I'm using Ubuntu 9.04.


Could someone guide me as to see why it does not resume successfully. I know some device might not be waking up and this causes the system to freeze. Are there any logs in the system that would have this information.

Thanks,

Riberet

---

### Post by coffeeaddict22 on 2009-05-16
System logs are kept in /var/logs/ and there's a few of them.  the output var/log/messages is any kernel messages, and could be a good pick; kern.log, sys.log and especially in this case Xorg.0.log are good picks.  
You can view them either in a terminal, or by going into System/Administration/Log file viewer; however, in a terminal, if you've got an idea what you're looking for you can use grep to pull out the interesting bits.

Having said that, hibernate has been a problem on some laptops, and there's some fairly challenging tricks that can be causing it; however, there's been a lot of improvement in the last couple of kernels.  Be a bit wary of any older info if you're googling your problem.

---

### Post by riberet on 2009-05-16
Thanks a lot man for your reply. I was going through the logs but I'm not too sure if I'll be ever able to figure out the problem. My next question is - Is there a way to repair the current installation in Ubuntu? As a last resort could I be able to reinstall ubuntu. Now I have a windows partition too. I dont want to loose windows.

I tried reading a couple of forums about reinstalling ubuntu but I was a bit confused. I'll get back to reading in a while.

Thanks

---

### Post by coffeeaddict22 on 2009-05-16
Gotta say, I thought you might be being a bit keen diagnosing the problem quite that early, but you could (quite easily) be smarter than me :-).  The output of ```
dmesg
``` just after you've had the problem would be the best place to look for a dummy spit.
I'd have to google around to be certain, but I think it was the video drivers that have been causing most grief lately.  your Xorg.0.log should indicate if that's the issue.  It also explains the reason why it happens after a good install: usually it's due to changing the driver or the window manager (Compiz...).
If you're going to reinstall, I strongly recommend creating 3 partitions: one for the OS (20 GB is usually plenty unless you're downloading heaps of source/ kernel versions), one for the swap (there's a bit of debate, but AFAIK 2x memory is more than enough, and 1x memory size is probably good if you've got more than 2GB), and the rest as a mount point for /home.  That way when you want/ need to reinstall, all your data **should** (you need to backup the important stuff, of course) stay intact.

---

