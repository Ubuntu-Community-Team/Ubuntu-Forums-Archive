---
title: "dell inspiron 6400 running hotter"
date: 2007-10-23
forum: Dell  Ubuntu Support
---

### Post by jack handy on 2007-10-23
my laptop seems to be running hotter under gutsy than it was under vista.  the temperature of the keyboard is noticeably higher and i see that the fan is on much more often now than it ever was previously.

is this normal?

---

### Post by djRob on 2007-10-23
No it isn't normal. I have Inspiron 6400, Core 2 Duo, ATI x1400, and don't see any difference between Ubuntu Gutsy and Vista.  You can slow your CPU with
```

sudo cpufreq-selector -g *governor*

```

---

### Post by jack handy on 2007-10-23
> **djRob said:**
> No it isn't normal. I have Inspiron 6400, Core 2 Duo, ATI x1400, and don't see any difference between Ubuntu Gutsy and Vista.  You can slow your CPU with
```

sudo cpufreq-selector -g *governor*

```

thanks for the reply.  your post inspired me to look up some apps in the repository before messing with command-line stuff that i will most likely mess up.  

i found the KDPowersave app, which is supposed to let me run my CPU's at "powersave" frequency policy.   

i'll see by tomorrow if there's any change.  if not, then i'll look into the cpufreq-selector thing.  :KS

---

### Post by djRob on 2007-10-24
> **jack handy said:**
> thanks for the reply.  your post inspired me to look up some apps in the repository before messing with command-line stuff that i will most likely mess up.  

I think that KDE programs can mess up Gnome. The mentioned command simply switches mode of the processor, you can replace *governor* in the command with power modes that you see in Vista, e.g. powersave.

---

### Post by jack handy on 2007-10-24
really?  damn, i had no idea.  you'd think they would take them out of the repo if they had any chance of messing gnome up. :(

---

### Post by jack handy on 2007-10-24
does the setting of cpufreq-selector reset every time i reboot?

---

### Post by johnw2007 on 2007-10-24
I have one of the new Inspiron 6400's in the UK with Ubuntu pre-installed by Dell. The keyboard is only slightly warm (not normally noticeable) and the fan only runs occasionally, nowhere near as often as on my previous HP nx6110.

If anyone can suggest something for me to check to compare with yours I am willing to do so.

---

### Post by djRob on 2007-10-24
> **jack handy said:**
> really?  damn, i had no idea.  you'd think they would take them out of the repo if they had any chance of messing gnome up. :(
"Ubuntu comes with ABSOLUTELY NO WARRANTY."
Although I think that simple KDE applets can't do much damage, but  I know for a fact that installing KDE desktop in Ubuntu can completely mess up programs which use Gnome widgets, e.g. Firefox. 

As I said use this command
```

sudo cpufreq-selector -f 1000

```I learned that after using "sudo cpufreq-selector -g powersave" processor starts to behave strangely.
You can install CPU Frequency Scaling Monitor applet so you will see what is the speed of your CPU.

---

### Post by mcasaroli on 2008-01-23
What tempeature are you running?
I have an Inspiron 6400 w/ C2D 2.0GHz at 66 C at maximum with the cooler at maximum, it that too much? What temperature do you get at max and min?

---

### Post by peteguhl on 2008-06-17
I have an e1505, which is the same as the 6400 - you *need* to run either dellfand or i8k, your fan isn't running as it should be and either one of those helps. I suggest dellfand as it works much better than i8k on my laptop.

---

