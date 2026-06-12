---
title: "Odd aMSN webcam experience"
date: 2006-07-25
forum: Desktop Environments
---

### Post by ironfistchamp on 2006-07-25
Ok hows this for interesting

I have two webcams. Trust Spacecam 120 and  Labtec something or other. So both my computer and my brothers computer have Dapper installed today with the same kernel and the same aMSN version (0.97b from a post around here). So anyway on his comp the Spacecam works but the trust doesn't. On mine it is almost the other way around. The Spacecam doesnt work at all (no device plugged in message) and the Labtec one starts to be recognised and crashes aMSN (killall wish time).

Any ideas people. This has got me baffled. Doesn't take much I know but still.

Thanks

Ironfistchamp

---

### Post by llamakc on 2006-07-25
Do a diff on the modules installed on both machines. Compare the output from dmesg on both machines. I'd start there. . . .

---

### Post by ironfistchamp on 2006-07-25
Do a what now? Err I'll type dmesg on each and see what happens :p
EDIT: It appears he has 

[17191496.216000] drivers/usb/media/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. SONIX sn9c102 + Pas106 

And I do not. The question is how on earth did it get on there. I know that I didn't put on there. The only difference in software installed is that he has ndiswrapper on there and I don't. Everything else should be the same (at least user installed stuff).

Ok so what may have put it on there (any logs to see) and if we can't figure out what put it on there how can I get it. It's my bloody camera :o

Thanks

---

### Post by llamakc on 2006-07-25
In the Terminal you can look at some of the logged messages with the command `dmesg`. Typically you will see output there when a device like a webcam is plugged in.

On computer A, you can get a list of the currently installed kernel modules with the command (from a Terminal):

lsmod

I would do that on both computers and compare them for differences. Also, I would do a fresh run of updating the package information and dist-upgrading with either the commandline apt frontend or Synaptic/Adept (whichever you choose to use).

---

### Post by ironfistchamp on 2006-07-25
Ok just checked using lsmod. I have it too so why wasn't mine working when I plugged it in?

---

### Post by llamakc on 2006-07-25
Try a different USB port. Are ya'll using the same kernel version? Is hotplug installed on both computers? 

I fought for the longest time trying to get a digital camera recognized by Ubuntu, thinking it was something with Dapper. Turned out I had a bad USB port. Merely choosing a different one worked for me.

Are you both using Gnome or KDE?

---

### Post by ironfistchamp on 2006-07-25
Right ok so we are both using Gnome. I tried putting it in a different USB slot and clicked configure webcam. Wahey now instead of not recognising it it freezes. Seems like progress to me. So I think well I am using the 0.97b I'll go back to the 0.95 in the repos. Now running from console and I am told 

Segementation Fault.

What is one of those and how do I fix it?

Thanks
 

Ironfistchamp

EDIT: The 0.96RC1 gives me the same error :(

---

### Post by llamakc on 2006-07-25
You can't fix seg faults but you can figure out why they happened.

Check the program's --help output by typing something akin to:

amsn -h

or

amsn --help

See if there is a -v (or --verbose) mode. Then, run the program with that flag.

amsn -v

and see what happens when it segfaults.

Does 0.95 support webcams at all?

---

### Post by ironfistchamp on 2006-07-25
0.95 should and so should 0.96 and 0.97, So anyway after running with those flags I got Seg Faults all the time. I think I heard something about there being a prob with the Ubuntu ones. I shall try it from source and see what happens.

---

### Post by ironfistchamp on 2006-07-25
Ok big news. using the Bitrock installed from the site I got 0.96RC1 working. Thats good but I still have the prob of amsn freezing when I try to configure the webcam.

Would a screenshot help?

EDIT: Tried global install of 96. That screwed it up completely. Won't even install to home dir now so I am back using the 97b deb. This is doing my head in. I'd switch to gaim but I can't stand it. ](*,)

---

