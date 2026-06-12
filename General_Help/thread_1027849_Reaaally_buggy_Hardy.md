---
title: "Reaaally buggy Hardy"
date: 2009-01-01
forum: General Help
---

### Post by Ionamay on 2009-01-01
Okay so I had been using Intrepid Ibex but recently I reinstalled Hardy because I thought it would give me less problems. Nooo. It just keeps freezing and I have to keep doing hard reboots (ctrl alt backspace doesn't work) and whenever I try to do anything, for example with firefox and pidgin, one or the other will crash at some point. I've done about 6 hard reboots today and I hate doing that. I just need some help getting ubuntu to be a little less buggy. Please help? Must be a simple enough problem.

---

### Post by Ionamay on 2009-01-01
Someone pleeeease help me, this is really frustrating me, now it keeps beeping and i had a page of flashing green text that didn't even say anything, come on, I've been using ubuntu for over a year now, please help me out, I don't want to have to leave ubuntu now.

---

### Post by stderr on 2009-01-01
Rather hard to say without specifics. One place to start looking is in the system logs. They reside in /var/log/ but can also be accessed in a GUI by System->Administration->System Log. 

Messages, syslog, kern.log and maybe Xorg.0.log may contain useful info - if they do appear to contain abnormal occurances, post it here and we'll all pour over it.

---

### Post by Ionamay on 2009-01-01
I don't really know what counts as an abnormal occurance.

---

### Post by Ionamay on 2009-01-01
Should I just post what it says in the log?

---

### Post by stderr on 2009-01-01
Maybe if you just post the contents of /var/log/syslog and /var/log/messages and we'll try to see if anything looks amiss. 

With regard to having to hard reboot, you could try using magic keys to safely reboot your system. They may not work either, but it's definitely worth a go. Basically you hold down Alt and PrintScreen, and WHILST HOLDING THOSE KEYS DOWN press R, E, I, S, U, B (without the commas, and with a 1-2 sec gap in between each). That should safely reboot your PC. I wrote a little article on it [here]("http://www.acepcs.co.uk/index.php?a=knowbase&kbs=linux&kba=magickeys") if you need more info.

Also, if next time you start Firefox or anything else), you start it from a terminal, then you may get some useful error messages in the terminal when it crashes.

```
firefox
```

would start firefox, but keep that terminal open, and if it crashes, check back and post any error messages that are in the terminal. Similarly, 

```
pidgin
```

would start pidgin etc.

---

### Post by linuxisevolution on 2009-01-01
> **Ionamay said:**
> I don't really know what counts as an abnormal occurance.

I had the same problem. If you've done the updates and installed the new kernel, then you can load the old kernel via grub to see if that fixes it. Restart your pc ( lol, you've done that enough ) and hit escape on the 3 second thing and then select the third down from the top kernel on the list and hit enter. The kernel has hardware incompatiblilities with some hard drive interfaces or some bug like that. Look at the hdd activity light on the front of your tower the next time it freezes, is it solid or flickering?

Let us know if this helps.

---

### Post by dcstar on 2009-01-02
> **Ionamay said:**
> Okay so I had been using Intrepid Ibex but recently I reinstalled Hardy because I thought it would give me less problems. Nooo. It just keeps freezing and I have to keep doing hard reboots (ctrl alt backspace doesn't work) and whenever I try to do anything, for example with firefox and pidgin, one or the other will crash at some point. I've done about 6 hard reboots today and I hate doing that. I just need some help getting ubuntu to be a little less buggy. Please help? Must be a simple enough problem.

if you had problems with one release and still have problems with a different release, then perhaps it is time to stop blaming the software and look at the component common to both: your hardware?

---

### Post by hyper_ch on 2009-01-02
You should detain from bumping a thread within 24h after last reply or after it's been opened!

---

### Post by Ionamay on 2009-01-03
There's so much to paste, I don't know what to give you, it's too much... and to dcstar, well I had no problems with Hardy first, then I updated and I had problems with Intrepid Ibex, so I went back to Hardy, expecting not to have too many problems.

---

