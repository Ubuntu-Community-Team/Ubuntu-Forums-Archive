---
title: "Make a program use swap space instead of Ram"
date: 2009-05-07
forum: General Help
---

### Post by Dracu@l on 2009-05-07
I wondered if it was possible at all to make a program (in my case firefox) use mainly swap space instead of RAM. 
I like to multitask and would like to keep firefox out of the RAM when I run CPU and RAM heavy processes, like DAWs and graphics.

---

### Post by DLG102282 on 2009-05-07
Swap space is so much slower then RAM that it would be a stupid thing to even attempt to do. Adding more RAM would make more sense.

---

### Post by Alterax on 2009-05-07
Strictly speaking, DLG is right.  It is much slower, and would end up bottlenecking your system more.  Not to mention that excessive use of swap space can lead to a condition called disk thrash--which can (aside from drive you nuts by slowing down your system) lead to premature failure of your hard drive.

Really, you have two other options open to you:

1.  If your motherboard can handle it, increase the amount of memory you have.  It's not very expensive today; mine was $65 a gig which comes out to less than 10 cents per megabyte.

2.  If that's not an option, try reducing the amount of load on your memory.  I switched from 24-bit to 16-bit color on my laptop (since the memory is shared between the mobo and graphics card)--instant performance boost and I can't tell the difference.  Also, firefox is kind of RAM-intensive as of late; using a lighter-weight browser such as Epiphany can help out on that too.  Even disabling some add-ons and plug-ins that you can live without will speed things up a lot.

---

### Post by Dracu@l on 2009-05-07
:/ i just wanted to know HOW to do it, i know that its much more efficient installing more ram, reducing work load,etc. but some apps generally dont need the power of the RAM, nor the speed. if you dont have any suggestions on how to make a program use swap space, <beep>

---

### Post by mcduck on 2009-05-07
> **Dracu@l said:**
> :/ i just wanted to know HOW to do it, i know that its much more efficient installing more ram, reducing work load,etc. but some apps generally dont need the power of the RAM, nor the speed. if you dont have any suggestions on how to make a program use swap space, please do not reply, your answer will be useless.

It's simply not possible. Processors can't access data directly from the disk, that would be way too slow compared to the speed your processor works at. Even if you forced Firefox to keep it's data in swap instead of RAM, every time Firefox would do something it would have to read the data back to RAM, do what it needs to do and then write the data back to swap. In the end you'd need the same amount of RAM but you'd get a lot of disk access as well to slow things down.

If you want to use less RAM, you just need to use programs that need less RAM. There's no way around it.

---

### Post by Dracu@l on 2009-05-07
Okay, so this is it, Ubuntu, the path to freedom.
so I though I wanted some control over my applications.
I want to route the memory my multitasking apps use to a swap space
(flash drive) instead of using the RAM, I just want to see if this works
(or is possible) installing more RAM is not an option because im only
trying to re-route between 100-300 MB.  
Apps I'd like to re-route to the swap space:
 (IRC, pidgin, Firefox, Mail Client, (maybe utorrent, but that one is running on wine) and maybe my media player) 
:)
even if its not a smart idea, I want to try it.

---

### Post by HermanAB on 2009-05-07
Howdy,

The Linux kernel scheduler and memory manager knows best.  Don't worry about it.  Just let it do its job.

---

### Post by cariboo on 2009-05-07
Linux uses swap differently from Windows. Swap is only used when you run out of ram. Have a look at this [article]("http://www.linux.com/feature/121916") on working with swap.

---

### Post by overdrank on 2009-05-07
Sorry cariboo907 :P  Threads merged :KS

---

### Post by mcduck on 2009-05-07
> **Dracu@l said:**
> Okay, so this is it, Ubuntu, the path to freedom.
so I though I wanted some control over my applications.
I want to route the memory my multitasking apps use to a swap space
(flash drive) instead of using the RAM, I just want to see if this works
(or is possible) installing more RAM is not an option because im only
trying to re-route between 100-300 MB.  
Apps I'd like to re-route to the swap space:
 (IRC, pidgin, Firefox, Mail Client, (maybe utorrent, but that one is running on wine) and maybe my media player) 
:)
even if its not a smart idea, I want to try it.

It's not question of freedom, or Linux, or whatever operating system. The thing is simply that this is how computers work, CPU processes data and instructions it reads from RAM and that's it. You always need to have the data in RAM before your processor can use it.

If you want to change that you can't do it by changing how your operating system behaves. You have to invent a new way for computers to work. :)

---

### Post by bodhi.zazen on 2009-05-07
You will need to do some serious reading :

[http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management](http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management)

[http://linux-mm.org/](http://linux-mm.org/)

[http://tldp.org/HOWTO/KernelAnalysis-HOWTO-7.html](http://tldp.org/HOWTO/KernelAnalysis-HOWTO-7.html)

[http://www.linuxhq.com/guides/TLK/mm/memory.html](http://www.linuxhq.com/guides/TLK/mm/memory.html)

[http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm](http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm)

As you will find if yo do a google search, and on this thread, what you are wanting to do will be difficult and negativly impact system performance.

It is far far easier , and will give you better performance, to simply close applications you are not using, such as firefox. alternately , use a lighter wight distro or application, such as dillo.

---

### Post by bodhi.zazen on 2009-05-07
> **Dracu@l said:**
> Okay, so this is it, Ubuntu, the path to freedom.
so I though I wanted some control over my applications.
I want to route the memory my multitasking apps use to a swap space
(flash drive) instead of using the RAM, I just want to see if this works
(or is possible) installing more RAM is not an option because im only
trying to re-route between 100-300 MB.  
Apps I'd like to re-route to the swap space:
 (IRC, pidgin, Firefox, Mail Client, (maybe utorrent, but that one is running on wine) and maybe my media player) 
:)
even if its not a smart idea, I want to try it.

See the links I gave you and start learning C and kernel programing. What you are wanting to do can be done, it will require a lot of effort.

---

### Post by bodhi.zazen on 2009-05-07
Another option is to use nice / renice

[http://linux.die.net/man/1/nice](http://linux.die.net/man/1/nice)

[https://lists.tce.edu/pipermail/glugot/2005-September/000409.html](https://lists.tce.edu/pipermail/glugot/2005-September/000409.html)

[http://www.computerhope.com/unix/unice.htm](http://www.computerhope.com/unix/unice.htm)

[http://www.cyberciti.biz/faq/change-the-nice-value-of-a-process/](http://www.cyberciti.biz/faq/change-the-nice-value-of-a-process/)

---

### Post by ibuclaw on 2009-05-07
If you are looking for DAW and graphics applications to have a greater access time to the CPU, then why don't you just renice or manipulate the real-time attributes of the processes that you want the most resources dedicated to.

Here is a good guide on Low Latency sound in ALSA: [http://www.alsa-project.org/main/index.php/Low_latency_howto#PAM]("http://www.alsa-project.org/main/index.php/Low_latency_howto#PAM")
Do note that the service "softirq-timer" is now named "**ksoftirqd**".

[Here]("http://books.google.co.uk/books?id=OWxsVjef1iIC&pg=PA179&lpg=PA179&dq=ubuntu+process+priority+nice+renice&source=bl&ots=MnYqAo-tQq&sig=0963q_ifMiC3Hmh1-9Le1P_a5GY&hl=en&ei=nCUDSsrTNJWsjAfd-sH4BA&sa=X&oi=book_result&ct=result&resnum=7") is a small guide on nice/renice too.

Regards
Iain

---

### Post by ddrichardson on 2009-05-07
Prioritising is not straight forward but it is straight forward to set how the kernel prefers to use swap when it tries to free memory, its a bit of a suck it and see [process]("http://www.linode.com/wiki/index.php/Swappiness") but given the different memory requirements for Firefox and image processing then you should be able to find a suitable balance.

---

