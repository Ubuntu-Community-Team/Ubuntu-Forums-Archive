---
title: "no keyboard or mouse on login screen"
date: 2009-04-25
forum: General Help
---

### Post by damimiot on 2009-04-25
Ive being using Ubuntu for jsut over 2 weeks. when i turn on my computer the keyboard works properly when using GRUB but when the kernal/os loads the keyboard stops responding and so does the mouse.

Both the keyboard and mouse work in windows. the keyboard is a microsft wireless keyboard 1000 and mouse is a logitch mx revolution

Any help is much apreciated
Damian

---

### Post by joeyknuccione on 2009-04-25
> **damimiot said:**
> Ive being using Ubuntu for jsut over 2 weeks. when i turn on my computer the keyboard works properly when using GRUB but when the kernal/os loads the keyboard stops responding and so does the mouse.

Both the keyboard and mouse work in windows. the keyboard is a microsft wireless keyboard 1000 and mouse is a logitch mx revolution

Any help is much apreciated
Damian
Try this article:

[http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html)

---

### Post by damimiot on 2009-04-27
Tired it but it didnt work. so i've just upgraded to 9.04, a little bit sooner than i planed to.

but thank you for the quick reply

---

### Post by edvar on 2009-09-30
It just happened to me. Hal wasn't loading so I got no mouse, keyboard, sound or network available after I installed an upgrade to kernel 2.28.15.52 in Jaunty.

I tried several things but nothing worked then I realized the folder /etc/hal was empty!

I went to a Linux Mint Gloria VM I had installed on another computer and checked the contents of the folder. The folder structure is basically:

/etc/hal/fdi
/etc/hal/fdi/preprobe
/etc/hal/fdi/policy
/etc/hal/fdi/information

I recreated the folders on my Ubuntu Jaunty box and rebooted. After that I was back in business!

---

### Post by 13thSlayer on 2009-09-30
> **edvar said:**
> It just happened to me. Hal wasn't loading so I got no mouse, keyboard, sound or network available after I installed an upgrade to kernel 2.28.15.52 in Jaunty.

I tried several things but nothing worked then I realized the folder /etc/hal was empty!

I went to a Linux Mint Gloria VM I had installed on another computer and checked the contents of the folder. The folder structure is basically:

/etc/hal/fdi
/etc/hal/fdi/preprobe
/etc/hal/fdi/policy
/etc/hal/fdi/information

I recreated the folders on my Ubuntu Jaunty box and rebooted. After that I was back in business!
here's a command for that:
"sudo cd /etc/hal ; sudo mkdir fdi ; sudo cd fdi ; sudo mkdir preprobe ; sudo mkdir policy ; sudo mkdir information"
That will make it.

---

