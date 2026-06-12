---
title: "kernel 2.6.22"
date: 2007-10-08
forum: Debian
---

### Post by Junichiromayo on 2007-10-08
I upgrade my installation from kernel 2.6.18 to 2.6.22 and I can't boot without adding acpi=off in the /Boot/Grub/menu.lst.
Somebody knows another solution?
I boot now with the 2.6.18 kernel waiting for solution. I'm on a Dell Inspiron 1501. May be I'll go to Ubuntu.

---

### Post by kerry_s on 2007-10-08
is there something specific you want in the 2.6.22 image?

i was just about to try it and see how it was coming along, last month when i tried it, it had the acpi problems but booted fine, it's switching to console(tty) and shutdown, that was broke for me, it would hang.

the 2.6.18 is a good image never gave me problem's, even the cpu throttling works right. nothing wrong with using it if it works.

forgot to mention, there is no fix for a kernel bug, unless you want to rebuild it, compile your own kernel.

---

### Post by Junichiromayo on 2007-10-09
Nothing specific. If the sound, brightness, etc buttons would work, it'll be fine. I'm am on 2.8.18-k7 and it works with AMD64 Turion x2.
My wifi works; I can manage my Airport Extrem station with Airport-utils (I'm an ex-Mac addict who don't like Apple gadgets and today philosophy, so I switch to Linux for my laptop and since a month I try to find the distribution I'll definitively adopt on it; I can test because I have an Intel iMac with Mac OS 10.4 operationnal).
Thank's

PS: Do you know how to make suspend (sleep?) workable? Sorry, I'm French speaking.

---

### Post by kerry_s on 2007-10-09
> **Junichiromayo said:**
> Nothing specific. If the sound, brightness, etc buttons would work, it'll be fine. I'm am on 2.8.18-k7 and it works with AMD64 Turion x2.
My wifi works; I can manage my Airport Extrem station with Airport-utils (I'm an ex-Mac addict who don't like Apple gadgets and today philosophy, so I switch to Linux for my laptop and since a month I try to find the distribution I'll definitively adopt on it; I can test because I have an Intel iMac with Mac OS 10.4 operationnal).
Thank's

PS: Do you know how to make suspend (sleep?) workable? Sorry, I'm French speaking.

sorry, no i don't. i leave my computer on all the time so i just put the screen to sleep and move the mouse to wake it up.

i just tried that 2.6.22, it's still screwed up. i recommend just staying with what you got, i use the 2.6.18-5-686 for mine.

---

