---
title: "Evince will not open eps files"
date: 2009-06-01
forum: General Help
---

### Post by jwilley44 on 2009-06-01
I get this error when I try to open an eps file.

```
evince: /build/buildd/cairo-1.8.0/src/cairo-xlib-surface.c:934: _draw_image_surface: Assertion `ret != 0' failed.
```

I was always able to run evince without a problem, and I do not know what happened. This morning it worked and now it does not. I am running Ubuntu 8.10 64 bit. 

Thanks in advance.

---

### Post by Dougie187 on 2009-06-01
Is it a specific EPS file? Or Any EPS file?

---

### Post by jwilley44 on 2009-06-01
It has happened with all the eps files I have tried to open this afternoon.

---

### Post by Dougie187 on 2009-06-01
Are these eps files available online? Or are they self made? If they are self made, what did you use to make them?

Also, have you read through this?

[https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/296701](https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/296701)

---

### Post by jwilley44 on 2009-06-01
The eps files are outputs from gnuplot. I did read through this link. It seemed it was just tracking down the error and I did not see what the fix was.
I would be willing to track down the error, but I would not know what to do from there. I was hoping someone might have an easy fix.

---

### Post by Dougie187 on 2009-06-01
Do you have the same verison of evince they have?

---

### Post by jwilley44 on 2009-06-01
So, I am not totally helpless when it comes to linux but close. I typed in 

```
apt-cache policy evince
```

this is what I got, it is not the same thing as in the thread.

```
evince:
  Installed: 2.24.1-0ubuntu1
  Candidate: 2.24.1-0ubuntu1
  Version table:
 *** 2.24.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com intrepid/main Packages
        500 http://za.archive.ubuntu.com intrepid/main Packages
        100 /var/lib/dpkg/status

```


I am not sure if this what you are referring to. Thanks for being patient.

---

### Post by jwilley44 on 2009-06-03
Don't know why this started happening but it is not happening any more. Thanks for your help.

---

