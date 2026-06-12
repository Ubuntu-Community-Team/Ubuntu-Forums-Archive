---
title: "USB Racing Wheels - Any working in Linux?"
date: 2006-03-02
forum: Gaming &amp; Leisure
---

### Post by sham69 on 2006-03-02
Has anyone got a USB racing wheel of any description to run in Linux?

I have an ACT-Labs Formula Force which has no hope of ever working I'm sure.
Hence, a Windows partition for Racing Sims....

---

### Post by jamyskis on 2006-03-03
I have a cheapy one that works because the inputs are like a standard joypad, although I can't remember the model offhand - I don't use it much because of the space it takes.

I'll get back to you on this.

---

### Post by handy on 2006-03-04
Yes, I'd be interested to know if anyone has got any of the ***Logitech* - Wingman Formula Force** wheels & pedals working?

---

### Post by leech on 2006-03-04
[http://www.wingmanteam.com/linux.htm](http://www.wingmanteam.com/linux.htm)

Google is your friend.  You'll want to modprobe iforce.  

Leech

---

### Post by handy on 2006-03-05
[QUOTE=leech][http://www.wingmanteam.com/linux.htm](http://www.wingmanteam.com/linux.htm)

Google is your friend.  You'll want to modprobe iforce.  

Leech[/QUOTE]

Thanks Leech,

It looks like now my problem is to find a game that I can test the wheel under in Ubuntu!? :KS

I input **modprobe iforce** in the cli, & got the response below?   

handy@BirdFish:~$ modprobe iforce
FATAL: Error inserting iforce (/lib/modules/2.6.12-10-386/kernel/drivers/input/joystick/iforce/iforce.ko): Operation not permitted

Obviously I don't know what I'm doing! :confused: :KS  

But I enjoy it as much as I can anyway! :mrgreen:

---

### Post by Gray. on 2006-03-05
sudo modprobe iforce

---

### Post by sham69 on 2006-03-05
Hmm.. I'll try that, my wheel uses IForce as well.
As for games Grand Prix Legends (openGL) will apparently run under Wine.
It is truly great.....

---

### Post by handy on 2006-03-05
Thanks & Thanks! :KS

---

### Post by leech on 2006-03-07
There's always Torcs.  Not sure if Tuxracer will use the wheel.  I can't recall if I ever tried to use my Microsoft Sidewinder wheel or not in linux...

Leech

---

