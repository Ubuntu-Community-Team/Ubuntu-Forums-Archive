---
title: "Laptop Battery Indicator Faulty"
date: 2006-06-01
forum: Desktop Environments
---

### Post by DarthGroznii on 2006-06-01
Hello -

I've installed Dapper Drake and had very little trouble; however I've discovered a bug: the status of the battery is just incorrect - after fully charging the battery, I pulled out the power cord and it told me I have 3 minutes left, even though it's 100%.  I've received other such erroneous messages saying that the battery was at low power level etc.  

This was not a problem on Breezy Badger.

The laptop I am using is a HP Compaq nx7000 business laptop.

Thanks in advance for any assistance.

Yours sincerely,

Darth Groznii

---

### Post by slavik on 2006-06-01
never use the timer ... but it should still read the proper charge percentage on the battery

---

### Post by sherlock-holmes on 2006-06-01
[QUOTE=DarthGroznii]Hello -

I've installed Dapper Drake and had very little trouble; however I've discovered a bug: the status of the battery is just incorrect - after fully charging the battery, I pulled out the power cord and it told me I have 3 minutes left, even though it's 100%.  I've received other such erroneous messages saying that the battery was at low power level etc.  

This was not a problem on Breezy Badger.

The laptop I am using is a HP Compaq nx7000 business laptop.

Thanks in advance for any assistance.

Yours sincerely,

Darth Groznii[/QUOTE]

i dont even have the indicator at all... i was wondering what it was i am missing at that panel...how to add them?
edit: i had to uncheck the 'lock to panel' before i could place the icon from add to panel and move around...thanks

---

### Post by christhemonkey on 2006-06-04
I have this problem, except, on my laptop i am still running the liveCD and trying to install.
But a balloon tells me that i have 3 minutes remaining and that it is going to shutdown.

Quite unnerving really.



I seem to be unable to install as well, even when plugged in. 
But thats another story and another thread.

(but if you do want to help, it hangs after selecting the keyboard layout)

---

### Post by art on 2006-06-04
I have the same thing, which is very annoying... I unplug the power cord, and it warns of power beeing critical, and hibernates... What the...

---

### Post by spier on 2006-06-04
Same here: power management works great excepts for the battery life!

With a fully charged battery, dapper hibernates (selected option in PM)  right after unplugged!!

Any clues on how to tell pm an expected battery life?

Thanks

---

### Post by 40%TUX on 2006-06-04
aaaa hell...story goes on.....
same here
...
i guess we need a fix (in power management application that is..you dopeheads.... ;) just kidding)

---

### Post by spier on 2006-06-04
Hei, i think i found a way to go 
[here]("http://www.ubuntuforums.org/showpost.php?p=387628&postcount=18")

I`ll give it a try, but not this night... you know, Sunday... too much wine... I`ll let you know about any good news.

---

### Post by jorgealfonso on 2007-04-08
Hello all,

The low-battery LED on my laptop is always blinking. I mean ALWAYS, even if the laptop is plugged/unplugged/charged/empty, running on Linux or Windows... It's blinking even when the computer is OFF!!

This is happening since I installed Ubuntu. I left the installation running from the live CD, but it seems like my roommate unplugged the laptop by mistake; when I came back from work the LED was blinking an it has been blinking ever since...

Guess the BIOS was informed by Ubuntu that the battery was running out, then the battery actually ran out... and at the end nobody notified the BIOS that the battery was OK once again. I thought the problem could be repaired by letting the battery intentionally discharge and then recharge it, but I already tried many combinations of this and none worked (having the battery partially/completely finished, from windows/linux, etc...)

Do any of you have a guess about what could I do to fix this, or where to look for related documentation?

Thank you! ;)

---

### Post by Peter Andersson on 2007-04-09
I had a similar problem on my hp nx7400. I found this by asking google:
[http://emisca.altervista.org/nx7400/](http://emisca.altervista.org/nx7400/)
Look at "ACPI problems and fixes, bad state problem"
maybe those scripts could help.

---

