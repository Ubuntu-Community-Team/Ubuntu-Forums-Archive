---
title: "Gnubiff"
date: 2005-11-13
forum: Desktop Environments
---

### Post by microo on 2005-11-13
I'm trying to configure Gnubiff with a Gmail account ...is there someone who can help me with that.

Thanks

---

### Post by aysiu on 2005-11-13
I can't help you with Gnubiff, but maybe gmail-notify might help you. To install it, make sure you have the universe repositories enabled (see first link in my sig). Then type this in the terminal ```
sudo apt-get update
sudo apt-get install gmail-notify
``` You can also install it through Synaptic (see screenshot).

---

### Post by microo on 2005-11-16
Thanks for the advice Aysiu but after the installation ..how do i make it start when i reboot...can it be by typing gmail-notify in the start-up part in session ?

---

### Post by mustang on 2005-11-16
[QUOTE=microo]Thanks for the advice Aysiu but after the installation ..how do i make it start when i reboot...can it be by typing gmail-notify in the start-up part in session ?[/QUOTE]

System->Preferences->Sessions

Startup Programs tab: add the perl script

---

### Post by microo on 2005-11-16
Now you have me ...What's in the world a perl script....


I'm not that good in Linux to know everything, at 53 i'm learning but not as fast as i was learning at 20 so please be nice and explain it to me.

Thank you mustang

---

### Post by mustang on 2005-11-16
I'm sorry. Looking over my post, I couldn't even tell what I was saying. My apologies.

Goto System->Preferences->Sessions

Go to the startup programs tab. Click on add and then find the path of where you extracted check-gmail. For example, mine is here:

```
/home/manish/Applications/checkgmail-1.3/
```

What I meant by adding the perl script is selecting the "checkgmail" executable script. Keep the order value its default.

So then my startup command is 

```
/home/manish/Applications/checkgmail-1.3/checkgmail
```

---

### Post by microo on 2005-11-16
Thanks a lot mustang now i understand it

---

### Post by microo on 2005-11-16
One more question mustang, i've install it from synaptic so what can be my start up command. I have to set it up each time i reboot.

Excuse me for my ignorance.

---

### Post by RAOF on 2005-11-16
If you've installed gmail-notify, you can just add "gmail-notify" to your session startup.  (as in Mustang's post, but instead of adding "/home/whatever/...", you just add "gmail-notify")

---

### Post by microo on 2005-11-16
Gee ! That i love Ubuntu ! With a community like that i'm asking myself why there is so many people on Windows.

I was afraid to install Breezy ...( i was in love with Hoary) but the more i read and work with Breezy the more i found it superb.

Thank you for helping me RAOF

---

### Post by phewner on 2007-07-31
Ok, I figured out how to get gnubiff working with gmail.  It retrospect it was completely obvious but nonetheless I wasted an hour not getting it right.  Here's how it should look:

---

