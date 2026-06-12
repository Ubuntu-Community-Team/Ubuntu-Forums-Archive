---
title: "Frequent Kernel Panic"
date: 2009-01-31
forum: General Help
---

### Post by Unanimated on 2009-01-31
Yeah, I get a kernel panic almost 3 to 4 times a week. I won't even be doing something system-intensive, I'll just be opening Firefox and it'll panic. Today, even, I was playing Urban Terror and the map was loading, and there was a kernel panic. When I'm listening to music and browsing the Internet, there is sometimes a kernel panic. What is causing these? They only started happening when I upgraded to 8.10.

---

### Post by Hobgoblin on 2009-01-31
Have you tried running memtest from the grub menu (or liveCD)?

---

### Post by Unanimated on 2009-02-01
How long should I run it for?

---

### Post by XanTrax on 2009-02-01
Please run this command:

```

sudo dmesg > ~/Desktop/dmesg.current
```

and also run these:

```

sudo cp /var/log/dmesg.0 ~/Desktop/
sudo chown USER.USER ~/Desktop/dmesg.0

```

where USER (before and after the . ) is your username.  Then, take both the dmesg.0 and dmesg.current, put them in an archive, and upload them here.  Thank you.

---

### Post by Unanimated on 2009-02-01
Thanks for the help.

---

### Post by XanTrax on 2009-02-01
> **Unanimated said:**
> Thanks for the help.

Since you have been on the 2.6.27-11 kernel, have you been seeing kernel panics still?  Can you be specific as to what happens when you are experiencing a kernel panic?  What used to happen for me was that the caps lock light would blink and my screen and everything would be frozen.

Also, I am going to need the dmesg.0 and 

```

sudo dmesg > ~/Desktop/dmesg.current

```

Right after a kernel panic.  Also, please include the kern.log and kern.log.0 file (second one may be named wrong but you get the idea).

---

### Post by Unanimated on 2009-02-01
I got a kernel panic yesterday when I was just about to open a new tab in Firefox. The current tab was Meebo. The only other app that I had open was Songbird and Google Desktop, and I have my Bluetooth adapter plugged in. Nothing happened on my old USB keyboard, the screen would just freeze and any sound that was being made would loop at a certain point (like if it was saying the word "the," I would hear "thththththththth" until I restarted). Now, with the new keyboard that a friend gave me a few days ago, all the lights shut off and the Scroll Lock and Caps Lock lights just blink together. The same thing happens on the screen. Sometimes it'll panic when I turn it on and open Firefox.

---

### Post by XanTrax on 2009-02-01
> **Unanimated said:**
> I got a kernel panic yesterday when I was just about to open a new tab in Firefox. The current tab was Meebo. The only other app that I had open was Songbird and Google Desktop, and I have my Bluetooth adapter plugged in. Nothing happened on my old USB keyboard, the screen would just freeze and any sound that was being made would loop at a certain point (like if it was saying the word "the," I would hear "thththththththth" until I restarted). Now, with the new keyboard that a friend gave me a few days ago, all the lights shut off and the Scroll Lock and Caps Lock lights just blink together. The same thing happens on the screen. Sometimes it'll panic when I turn it on and open Firefox.

Ok, so, if you could get me a dmesg log from the exact day that you had the kernel panic AND a dmesg log after fresh boot, it would help greatly.

---

