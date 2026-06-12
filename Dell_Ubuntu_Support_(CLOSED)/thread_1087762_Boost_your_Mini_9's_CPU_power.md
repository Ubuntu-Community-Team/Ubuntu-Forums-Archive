---
title: "Boost your Mini 9's CPU power"
date: 2009-03-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sirebral on 2009-03-05
I had a problem that my CPU Frequency Scaling Applet was broken in my DELL Mini 9 revision.  If you have elected to stick with the DELL version then this trick is for you.

Scale you CPU Frequency to 1.6 GHz, instead of On Demand which idles at .8 GHz.

```
sudo cpufreq-selector -f 1600000
```

I am no sure how the battery will be effected, but the OS hangs less and transitions are much smoother.

Bonus Tip:  If you want a Compiz like interface, install emerald and fusion-icon.  The windows themes are nice, and you get he enhanced graphics.  You gotta search for the How To on this, but it will help you learn. ;)

Enjoy everyones jealousy. :popcorn:

EDIT: I just remembered - Thanks **leftcase** for posting the CPU trick here: [http://www.howtoforge.com/cpu_frequency_scaling_ubuntu](http://www.howtoforge.com/cpu_frequency_scaling_ubuntu)

---

### Post by superm1 on 2009-03-05
> **sirebral said:**
> I had a problem that my CPU Frequency Scaling Applet was broken in my DELL Mini 9 revision.  If you have elected to stick with the DELL version then this trick is for you.

Scale you CPU Frequency to 1.6 GHz, instead of On Demand which idles at .8 GHz.

```
sudo cpufreq-selector -f 1600000
```I am no sure how the battery will be effected, but the OS hangs less and transitions are much smoother.

Bonus Tip:  If you want a Compiz like interface, install emerald and fusion-icon.  The windows themes are nice, and you get he enhanced graphics.  You gotta search for the How To on this, but it will help you learn. ;)

Enjoy everyones jealousy. :popcorn:

EDIT: I just remembered - Thanks **leftcase** for posting the CPU trick here: [http://www.howtoforge.com/cpu_frequency_scaling_ubuntu](http://www.howtoforge.com/cpu_frequency_scaling_ubuntu)
You'll want to make sure if you are using compiz/emerald what not that you are turning off the Dell bar desktop interface.  There is an option in the Ubuntu menu for it.  It's known to not perform well with both running.

---

### Post by sirebral on 2009-03-05
I got that.  What I am looking for is a way to permanently change the frequency in the configuration.  I have found some policies and conf files, but nothing that holds the frequency object.

Maybe I should look to see if I can just fix the applet on the Mini 9.  It would be nice to run full clock at start up though.  My C++ skills are on the level of, I still need to finish this school.  This current book I am reading is super easy, just boring.

---

