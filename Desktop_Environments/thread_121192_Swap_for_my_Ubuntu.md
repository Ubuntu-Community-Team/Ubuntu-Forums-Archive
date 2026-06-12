---
title: "Swap for my Ubuntu"
date: 2006-01-24
forum: Desktop Environments
---

### Post by bathini on 2006-01-24
Hello friends

My laptop with Ubuntu 5.10 constantly freezes while running either applications and web browser. My thinking says, install swap space because I have only 256 MB memory and when I installed Ubuntu I did not add swap space. I think this can answer my problem. How do I add swap space when Ubuntu is already installed? or does anyone has any ideas?

Regards

Ubuntu

---

### Post by rmjokers on 2006-01-24
You have two options basically...one is to use a partition for swap...which is what people normally do when they install Ubuntu.  If you dont have any extra space on your drive to create a new partition and dont want to go through the trouble of resizing an existing partition which can be a major pain, you can actually use a file for swap.  The article below has details on how to do both methods.  It was written for redhat 8 but will still work with Ubuntu.

Note: You probably want a swap area larger than the 64 Megs used in the example.  Something like 256 or 512 would be a good size for you.

[http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html)

---

### Post by bathini on 2006-01-25
Thanks I will try this. Hopefully I will see a difference.

Bathini

---

### Post by az on 2006-01-25
You should notbe running out of ram like that with 256 megs.  How much memory is consumed (look in the system monitor or type "free" from a command line.)  You will see a lot of memory cached, but that gets flushed out when you need more memory - I don't hink you are running out unless you have twelve images opened at the some time in the gimp.

Did you partition automatically or did you do it by hand?  The automagic partioining makes a swap for you.

---

### Post by bathini on 2006-01-25
Azz

Thanks for the advise. I just used PArtition Magic on Windows and just installed Linux without configuring swap and I think that is why my Ubuntu was freezing a lot. I have made a swap file now and it has not freezed since. I made a 256 mb swap file. We will see how far it goes.Now the only problem is Internet is slow, when I connect from page to page. I will have to figure that one out.

Cheers

Bathini

---

