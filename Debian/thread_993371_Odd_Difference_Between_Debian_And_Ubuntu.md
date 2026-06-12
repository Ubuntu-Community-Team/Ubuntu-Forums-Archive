---
title: "Odd Difference Between Debian And Ubuntu"
date: 2008-11-25
forum: Debian
---

### Post by tcoffeep on 2008-11-25
Hello.

I found myself wondering something odd.

When I install Debian's base, and nothing else, and install Fluxbox and a handful of items I find necessary, my laptop's internal heat hits about 70 degrees. When I do the same with Ubuntu, it rarely hits about 60.
Is this as odd as it seems to me? Is there something different in the way Ubuntu and Debian detect hardware? Or is it kernel differences? (The latest kernel I could get with Debian was 2.6.26.6 using the lenny repositories, I think, whereas Ubuntu is 2.6.27.7. Please correct me if I'm mistaken.).
My laptop is an Inspiron 5150, which is horrid for overheating, but, it seems that it overheats depending on the OS?

---

### Post by oOarthurOo on 2008-11-25
Something like that could be explained by frequency scaling. A debian minimal install might not include packages to control frequency scaling while ubuntu base might.

---

### Post by kerry_s on 2008-11-25
when doing the base up build with debian, it's up to you to make sure you have the programs needed. debian doesn't bundle everything together like ubuntu does make sure you have the acpi stuff needed for your system and i recommend hal as well. check your dmesg log for any errors.

you should just go debian lenny, recommends is on by default, so you usually get whats needed.
[http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso)

if your unsure check the laptop package, when your unchecking the other 2. :)

---

### Post by p_quarles on 2008-11-26
> **oOarthurOo said:**
> Something like that could be explained by frequency scaling. A debian minimal install might not include packages to control frequency scaling while ubuntu base might.
Not "might", definitely. For a laptop, it is necessary to install the relevant package (called something like cpufrequtils) and then configure it. Otherwise, you will have your CPU(s) running at full speed all the time, which is counter to how most modern laptops were designed.

---

### Post by tcoffeep on 2008-11-26
Learn something new every day. Thanks, guys. I was about to give up on Debian. I guess I have a bit to learn, eh? Any idea where one can go to figure out what one needs to learn in order to build a bottoms-up system?

---

### Post by kerry_s on 2008-11-26
> **tcoffeep said:**
> Learn something new every day. Thanks, guys. I was about to give up on Debian. I guess I have a bit to learn, eh? Any idea where one can go to figure out what one needs to learn in order to build a bottoms-up system?

trial & error is the best teacher, the more you do it the better you'll get. you'll eventually get to know your favorite programs, what i usually do is open synaptic, then do a search, for example: 
editor
or
file manager
then i'll just try some, see what i like.

i always start mine with just X, a window manager and synaptic:
apt-get install xorg jwm synaptic

that's all i need to get into X, once i have that i log out of root(type> exit), log in as my user and startx, i then open the terminal and start synaptic. from there i decide what i want to try on that build, i usually try something a little different each time.
jwm is my favorite window manager, i don't even waste my time on anything else.

---

### Post by basenvironment on 2008-11-26
cpufrequtils should be automatically configured to use processor speed stepping if your cpu supports it. You will need to reboot after installing it. Then the command cpufreq-info will retrieve kernel information about cpu frequency scaling.

As stated, the best way to learn to build bottom-up is to fumble thru it a number of times. Keep notes each time in regards to what you need to install to do something. Soon you should be able to know exctly what you need/want.

Off the top of my head I would suggest:

aptitude install -R xorg alsa-base alsa-oss alsa-utils bash-completion cdrdao coreutils ddccontrol discover dmidecode dmz-cursor-theme dvd+rw-tools genisoimage libglu1-xorg libgl1-mesa-dri libgl1-mesa-glx linux-sound-base mdetect mesa-utils pmount read-edid ttf-liberation ttf-dejavu vbetool wireless-tools wodim xdebconfigurator xresprobe hwinfo hwdata cpufrequtils grandr

then

aptitude install -R your_favorites

---

### Post by kerry_s on 2008-11-26
i've never needed to add anything for cpu throttling, i just let the kernel take care of it.

---

### Post by stream303 on 2008-11-26
When building up a system in a DIY fashion, I found the following to be extremely useful.  Don't use sudo in the following, since you'll be doing it as root the Debian way.   (and some things are just not applicable like xubuntu-desktop of course..)

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

It isn't just for low-memory systems, but for anyone wanting to build from the ground up so to speak, even PowerPC users.

After each step I liked to doublecheck processes with top, or my favorite, htop, to make sure nothing was eating up cpu time at 100% or so.  

Hint: if you have dual-cpu's, just hit the "1" key while in top to see each cpu, or just download htop.  These can be critical before you even get to a gui version of a system-resource monitor...

I followed these instructions about a year or so ago with Debian and had no problems - can't say I've tried with Lenny.

If the default frequency-scaler powernowd doesn't seem to be working, or if you need lower-latency say for audio / video editing, you can try **cpudyn** which only has two states.  Downloading it will automatically remove powernowd and set itself up.  The reverse is true if you don't like it.  I watch it by adding the cpu-frequency scaling applet to the top panel in Gnome.

---

