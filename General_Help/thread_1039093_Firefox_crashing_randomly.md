---
title: "Firefox crashing randomly"
date: 2009-01-14
forum: General Help
---

### Post by jambroo on 2009-01-14
Hello,

I have had this problem for a while but just debugged it properly using
```
/usr/lib/firefox-3.0.5/run-mozilla.sh -g /usr/lib/firefox-3.0.5/firefox -d gdb
```

Firefox 3.0.5 crashes every 5-10 minutes. It can be sitting their idle for a while and close or it can be loading a new page and close.

The output from gdb most of the time is:
```
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7f73373606f0 (LWP 6137)]
0x00007f73349f6204 in ?? () from /usr/lib/xulrunner-1.9.0.5/libxul.so
```

But sometimes it is:
```
Program received signal SIGPIPE, Broken pipe.
[Switching to Thread 0x40851950 (LWP 6286)]
0x00007f86c8ce1521 in send () from /lib/libpthread.so.0
```

I've tried reinstalling xul runner but with no avail. From what I have read it could be a problem with GTK2 as similar things happen in xubuntu.

Anyone else experiencing this?

-Jamie

---

### Post by jambroo on 2009-01-15
I think from this [https://bugzilla.mozilla.org/show_bug.cgi?id=427889]("https://bugzilla.mozilla.org/show_bug.cgi?id=427889") I can gather that SIGPIPE isn't bad and you can stop gdb from stopping the program when it reaches it. It still doesn't explain the Segmentation fault on xulrunner, though.

It comes and goes pretty randomly - it is fine now but an hour ago I couldn't even open it and I tried to run apt-get to install something from the commandline and also got a segmentation fault. I'm not sure if they are connected though.

-Jamie

---

### Post by jambroo on 2009-01-31
Sorry for the shameless bump here guys.

I have resorted to starting a fresh with this pc and formatting the hard drives. I installed windows xp and was going to dual boot with ubuntu - but the install keeps dying at a certain section.

Anyway I am in windows now and i think i am getting the same problems with firefox - it is crashing heaps like in ubuntu. Could it be the pages i am going to? I am only on google and gmail mostly.

I am unsure how to debug programs in windows without installing crap like visual studio so im not sure if its the same segmentation fault or anything - but it sure is a similar way of randomly crashing.

If this is happening on multiple linux distros and in windows xp could it be a hardware issue or something like that? I don't know why it would only be affecting firefox, though.

Any ideas?

-Jamie

---

### Post by jambroo on 2009-02-05
I think this came down to bad ram - i just assumed it was firefox or ubuntu but when it was happening in fedora and windows i knew it was something bigger.

Weird though - i ran memtest86 a while ago and it came up fine then ran it again recently and it was fine - it wasnt until i took one stick out that errors stopped.

For the time being it is fixed so im not 100% sure it was ram. Anyway thought id share just in case anyone else is seeing similar random software crashes.

---

