---
title: "HP Deskjet 952C driver won't install, worked in Breezy"
date: 2006-06-28
forum: Desktop Environments
---

### Post by Brighid on 2006-06-28
Hi everyone,

I tried installing the driver for my HP Deskjet 952C printer, just as I did back in Kubuntu Breezy.  In Breezy it worked without any trouble, and the test page printed out fine.

Now, following the same procedure in Dapper, I can't get it to install.

I looked over the forums a bit and found people suffering similar problems, but I'm unsure of what the solution is ..

I'm using the wizard in System Settings.  This is the error output I get:

```
Unable to load the requested driver

Unable to create the Foomatic driver [HP-DeskJet_952C,hpijs]. Either 
that driver does not exist, or you don't have the required 
permissions to perform that operation.
```

I thought that perhaps I didn't have the Foomatic drivers, but I went into Adept and filtered "foomatic" and it seems to be installed.  I also thought that I perhaps needed to do it in administrator mode (due to the mention of permissions), but I got the same result.

What can I do?

---

### Post by arjay1 on 2006-07-07
sorry I can't help but you should know you are not alone.  I can't get the hp 840c to install either.  It was fine under breezy.

Hope we can get some help on this otherwise i am going to have to dump dapper

---

### Post by bohboh on 2006-07-07
Have you tried the trial version of [turboprint]("http://www.turboprint.de/english.html") to see if it is the drivers themselves or the absence of the drivers.

Also, i had problems with CUPS, i had to manually upgrade to CUPS 1.2.1 to fix my problem.

---

### Post by Brighid on 2006-07-21
> **bohboh said:**
> Have you tried the trial version of [turboprint]("http://www.turboprint.de/english.html") to see if it is the drivers themselves or the absence of the drivers.

Also, i had problems with CUPS, i had to manually upgrade to CUPS 1.2.1 to fix my problem.

I'm a little wary of installing things without Adept (I've done it, but I never like it), so I must ask first; what exactly would I be doing in turboprint that would help me with this?  I don't think I quite understand, after looking at their site, what it is that it does.  Does it make the printer run without a driver, or what?

I'd honestly forgotten about my printing problem, because I haven't had to print lately, but the inability to do so still lingers.  It's rather bothersome, and it's almost taunting that it worked before I upgraded to 6.06.

---

### Post by 11hjpphty76lkjj on 2006-07-21
You may want to try installing the latest HP linux driver.

[http://hplip.sourceforge.net](http://hplip.sourceforge.net)

there is a step by step for dapper.  let me know if you have any problems with it!

---

