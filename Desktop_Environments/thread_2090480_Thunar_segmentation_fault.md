---
title: "Thunar segmentation fault"
date: 2012-12-02
forum: Desktop Environments
---

### Post by annikos on 2012-12-02
Hi all!
I've installed Voyager 12.10 x64 (Xubuntu) on my laptop (Acer 5920G).
It looks fantastic and fast as well.
But...
Thunar crashes either from the terminal either from menu when I try to navigate through folders and/or open files. (segmentation fault)
I've added thunar/xfce 4.12 ppa (xubuntu-dev) to install the most fresh build of thunar (1.5.3) but it didn't help.  
Do I have to abandon thunar and move to nautilus or similar?
Thanks.

---

### Post by Toz on 2012-12-02
Try running thunar like this:
```
strace -f -F -odebug.txt thunar
```

After the crash, have a look at the debug.txt file in the working directory for a clue as to what caused the segmentation fault. Feel free to post it back here via:
```
pastebinit debug.txt
```
...and post back the link that is generated.

Depending on the results, we may be able to offer some suggestions or at least suggest that you create a bug report over at bugzilla.xfce.org.

---

### Post by annikos on 2012-12-03
Thanks Toz,

Here's the generated link:
[http://paste.ubuntu.com/1407664/]("http://paste.ubuntu.com/1407664/")

I hope it helps.

---

### Post by Toz on 2012-12-03
Nothing jumps out at me in that log file to indicate a cause.

Do you have a crash report file created in /var/crash for thunar? If so, can you post the crash file?

Also, are there any error messages in ~/.xsession-errors when thunar crashes?

---

### Post by annikos on 2012-12-03
> **Toz said:**
> Nothing jumps out at me in that log file to indicate a cause.

Do you have a crash report file created in /var/crash for thunar? If so, can you post the crash file?

Also, are there any error messages in ~/.xsession-errors when thunar crashes?

(Un)fortunately there is neither a crash report file in /var/crash nor any error message in ~/.xsession-errors for thunar. :confused:

---

### Post by Toz on 2012-12-03
Have you tested this crash in another user account (to rule out the possibility of a user configuration issue)?

If you are interested, here is a wiki article about debugging: [https://wiki.ubuntu.com/Backtrace]("https://wiki.ubuntu.com/Backtrace") and getting a backtrace. 

It might be best to create a bug report over at bugzilla.xfce.org.

---

### Post by annikos on 2012-12-03
Guest account also has crashed Thunar.

So, I've got a backtrace it and send it to bugzilla (bug 9581), as you've suggested.

Thanks for all.

---

