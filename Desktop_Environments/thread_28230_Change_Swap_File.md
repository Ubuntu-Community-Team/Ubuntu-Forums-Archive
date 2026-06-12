---
title: "Change Swap File"
date: 2005-04-19
forum: Desktop Environments
---

### Post by wayne on 2005-04-19
I don't believe my swap file is being used.  I initially installed Hoary on hda1 (3.1G) with a swap file on hda5 (180M) on the same drive.   The apps seems rather slow so I thought I would move my swap file to my second hard drive in hopes of speeding things up.  I deleted the swap on hda5 and created a 180M swap on the second hard drive in hdb5 partition.

Well, things didn't speed up and occassionally when I open an application it will close immediately.  I used vmstat to check the swap file usage and it shows 0 under swpd and si/so.  I also checked with the command free and swap usage is 0 with 177M total and free.  I check the fstab file and it is pointed to /dev/hdb5.

Can someone give me some help with this?  What do I need to do or check to make sure my swap file is being used?

Thanks
Wayne

---

### Post by GrumpySmurf on 2005-04-19
Not using swap isn't necessarily bad.  If you have enough RAM, your swap file may never, or rarely, get used. 

How much memory do you have?  What is the output of 'free'?  Here's a sample from a production server, which has barely touched its swap file.

```

$ free
             total       used       free     shared    buffers     cached
Mem:       2064432    2014108      50324          0     132896    1106248
-/+ buffers/cache:     774964    1289468
Swap:       311996      16876     295120

```

---

### Post by wayne on 2005-04-19
I have 320M of RAM and here is the output from free:

                  total         used           free     shared   buffers    cached
Mem:        321876     307168      14708          0      61376     103100
-/+ buffers/cache:     142692     179184
Swap:       177368          0          177368

Hope you can understand this.

Wayne

---

### Post by GrumpySmurf on 2005-04-19
[QUOTE=wayne]I have 320M of RAM and here is the output from free:
```

                  total         used           free     shared   buffers    cached
Mem:        321876     307168      14708          0      61376     103100
-/+ buffers/cache:     142692     179184
Swap:       177368          0          177368

```[/QUOTE]

Sure can understand that.  You are using 307M of your 320.  However, you have 61M buffered and 103M cached, which means you have about 180M "free".  What are you running on your system?  Standard desktop environment with applications?  If so, you should have enough memory for most tasks and rarely hit your swap file, if you've still got 14M "free".

The kernel does some voodoo memory management and I'm not 100% on how it works, but really, you don't want to be swapping.  Swapped programs perform worse than programs cached or buffered.  Hope this helps.

---

### Post by wayne on 2005-04-19
I'm running kde and using mostly Firefox browser, Thunderbird mail & calendar.  

Coming from the Windows world where the page file is used constantly I just assumed Linux would do the same.  That's what I get for assumming.

Thanks for the info,
Wayne

---

### Post by GrumpySmurf on 2005-04-26
[QUOTE=wayne]Coming from the Windows world where the page file is used constantly I just assumed Linux would do the same.  That's what I get for assumming.[/QUOTE]
That is an inaccurate assumption.  Windows XP memory management is the best out of any version of Windows I've used, but it is still inefficient and sometimes makes heavy use of the swap file for no apparent reason.  

At least, it's not apparent once a user has been running Linux for awhile ;).

---

