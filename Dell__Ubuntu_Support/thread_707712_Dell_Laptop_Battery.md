---
title: "Dell Laptop Battery"
date: 2008-02-25
forum: Dell  Ubuntu Support
---

### Post by p3_Arme on 2008-02-25
Out of interest, does anyone here know about; have; own or use a Dell laptop.

Since they are now selling laptops with Linux on :) I'd like  to know a few more tech. things before I buy one, but no matter much I look for the information I want, I can't find anything. 

Question I want answered is: How long does the battery last for (roughly, if used for Open Office and Music.)

The info. on the site gives the battery size 4/6/9 Cell with various WHr, but no info. on power drain, nor how long battery would last for.

 (I like the 9 Cell with 85 WHr)

Any suggestions or help, would be grateful.

---

### Post by edm1 on 2008-02-25
Well i have a Dell Inspiron 8600 which is almost 4 years old now. It's a 9 cell but now only charges to 67% of what it used to (48.4Wh/72Wh). Anyway it last a little less than two and a half hours if i turn the screen brightness down and wireless off.

---

### Post by pbcartwright on 2008-02-25
I have a 2-year old XPS, and the battery lasts about 2 hours.. listening to music.

---

### Post by dicecca112 on 2008-02-25
1520 here, I can get about 3hrs out of my 9cell.

---

### Post by p3_Arme on 2008-02-25
Thanks everyone for replying, 

If anyone here works for Dell, just let them know, there are some sad people, sorry geeks like moi, who would like to know the power drain,and or power usage, so we can roughly work out if it's worth getting two batterys, a bigger battery or stick with the one they recommend.

Thanks again.

---

### Post by Gringexican on 2008-02-25
I have a relativly new (Oct 2007) Dell Inspiron 1420n with Fiesty Fawn on it.  It has the 9 cell 85 Wh battery (and a 2nd as spare).  Running music and several programs such as OO.o and Firefox I average between 3-4 hours.  If I'm not playing music or running intense apps while on battery I can get a tad over 5 hrs before it warns me to hibernate and switch batteries.

The only noticable difference between battery v. plugged-in is that the screen is dimmer, otherwise everything runs just as quickly.  I have also noticed that the Li-ion batteries take bloody forever to recharge.

Dell is now shipping with Gutsy.  Both my Dells have been excellent machines.  My tower (Inspiron 530n) has a 500 GB HD for Gutsy and I just added a 250 GB for WinXP (blaspehmy, I know... but I need to run some proprietary Win apps for work) so keeping it on a separate drive is a sanity saver :)  that way I can use a virtual machine rather than dual boot so Windows stays in its "sandbox" and I can enjoy all the power and stability of Linux.

The only prob with the default install from Dell is that their partition scheme is not to *my* preference, but gParted is a wonderful tool :twisted:

Hope that helps

---

### Post by p3_Arme on 2008-02-25
Thanks, that was exactly what I needed to know. :)

---

### Post by dasunst3r on 2008-02-25
My Inspiron E1505/6400 with 9-cell battery is good for anywhere from 4-5 hours.

---

### Post by b0b4n on 2008-02-25
I got a Dell Inspiron 1720 i can get up to 3hours and 40 min depending on CPU frequency no sure what my battery is i think its 9 cell

---

### Post by fragos on 2008-02-25
1420n base model with 9 cell battery and I get 5+ hours with WiFi on.

---

### Post by SmallFish on 2008-02-25
I have E1505 with 9 cell. The battery died in less than a year. I am running on plugging to the power like a desktop. It does not even hold 1 min. 
In general, the 9 cell is pretty amazing when it was new. It last 7-8 hours for both windows and ubuntu in any kind of usage (2-3 programs at a time) other than watching movie.

---

### Post by notwen on 2008-02-25
Inspiron 1420n browsing the web and streaming music over a NFS mounted drive using my wifi.  I average 3-4hrs of life w/ a 9 cell battery.  =]

---

### Post by niteshifter on 2008-02-26
Hi,
1420n factory install 7.10, Nvidia and Hi-res screen, 85Whr batteries: From 3 to 4.5 hour run times. 3 hr is full screen brightness while viewing DVDs, 4.5 hr no DVD activity, wireless on, screen full brightness.

That's an 8 week old machine, btw. The one I had before that (an 8600 running 6.10) was giving 3.5 hours (screen at minimum, no DVD drive action, wireless on), 2.5 hours at full loading. Four year old batteries (72Whr).

---

### Post by Gringexican on 2008-02-26
One thing I forgot to mention is that the 9 cell battery does protrude a bit from the back of the computer (about 3/4" (2 cm)).  This doesn't present a problem for me; it fits in my computer bag just fine.  It only looks a little weird.

I suspect that the the 6 cell would be more flush, but since I don't have any I can't check that for you.  Nor can I say how long its typical life is under normal conditions.

---

### Post by jpittack on 2008-02-26
A Dell 1501 Turion X2.  I'm having issues with dynticks and C1E states, but the 9 cell lasts 5 hours Ubuntu, 4.5 Vista (no aero).  Getting dynticks and C1E states won't happen for a long time.  Won't affect your purchases because they don't sell the AMD stuff anymore, or atleast that I have seen. 9 cell doesn't stick out.

Soon the Wolfdale Intel processors will be getting sold in laptops.  That should add about 10-20% battery life.

---

### Post by midnightray on 2008-02-27
> **SmallFish said:**
> I have E1505 with 9 cell. The battery died in less than a year. I am running on plugging to the power like a desktop. It does not even hold 1 min. 
In general, the 9 cell is pretty amazing when it was new. It last 7-8 hours for both windows and ubuntu in any kind of usage (2-3 programs at a time) other than watching movie.

same laptop, ubuntu says provides 3 hours 10 minutes battery runtime. Its a year old. Used to be 5-6 hours brand new. I think I can get more battery life in xp rather than ubuntu. But in xp you spend the gained  battery life pressing ctrl+alt+del :)

---

### Post by PsychedelicReaction on 2008-02-28
brand new xps1330 (less than a month lifetime), 9 cell battery, and i get about 4 hours with ubuntu, more than 1 hour less than vista.

---

### Post by jpittack on 2008-02-28
Have any of you tried battery saving tips?  Such as are you running 64-bit (meaning without dynticks), are you underclocking your graphics cards, dimming your backlights, spinning down the hard drive (efficently), etc?

I am getting that 4 and half hours to five hours because of all of these tips I found at lesswatts.  The only thing that I can do is compile my own kernel with patchs to get dynticks to work and creating my own dsdt file to enable c1e states, or sleep states.  Everything else has been taken care of.  Before I was getting 3 3/4 of an hour.

---

### Post by PsychedelicReaction on 2008-02-29
i run dell default dvd so i think it's the 32 bit version. on battery mode it looks like nvidia downclocks itself to performance level 2 or 1 (switching from compiz to metacity), for the hard drive i didn't any particular tweaks, except enabling laptop mode. screen brightness goes down correctly.

how many wakes up from idle per sec  do u reach with powertop? in a normal session (ethernet+epiphany+mp3) it stays between 400 and 500, most of them made by the keyboard-touchpad

---

### Post by midnightray on 2008-02-29
> **jpittack said:**
> Have any of you tried battery saving tips?  Such as are you running 64-bit (meaning without dynticks), are you underclocking your graphics cards, dimming your backlights, spinning down the hard drive (efficently), etc?

I am getting that 4 and half hours to five hours because of all of these tips I found at lesswatts.  The only thing that I can do is compile my own kernel with patchs to get dynticks to work and creating my own dsdt file to enable c1e states, or sleep states.  Everything else has been taken care of.  Before I was getting 3 3/4 of an hour.

underclocks my 2ghz cpu to 1ghz. Dim the backlight. But underclocking your graphics card. Is this possible for ATI x1400 PCI-XPRESS cards. I'm using the restricted drivers. I found envy had problems with freezing during login/logout and startup.

dell inspiron 6400 e1505

---

### Post by mehmet.ali.anil on 2008-03-02
Inspiron 1520 here, Battery that came with the bundle is estimated 1,5 hours. :confused:

---

### Post by Omnios on 2008-03-02
> **Gringexican said:**
> One thing I forgot to mention is that the 9 cell battery does protrude a bit from the back of the computer (about 3/4" (2 cm)). This doesn't present a problem for me; it fits in my computer bag just fine. It only looks a little weird.
 
I suspect that the the 6 cell would be more flush, but since I don't have any I can't check that for you. Nor can I say how long its typical life is under normal conditions.
 
 I have an XPS 1530 with the 9-cell battery. I does stick out down a bit but found it allows space under tha laptop which helps with cooling.

---

### Post by jpittack on 2008-03-02
> **midnightray said:**
> underclocks my 2ghz cpu to 1ghz. Dim the backlight. But underclocking your graphics card. Is this possible for ATI x1400 PCI-XPRESS cards. I'm using the restricted drivers. I found envy had problems with freezing during login/logout and startup.

dell inspiron 6400 e1505

rovclock package.

```
sudo aptitude install rovclock
```

check your freq with

```
sudo rovclock -i
```

and set it with

```
sudo rovclock -c (freq # here)
```

My default is around 200 MHz.  I can get it down to 28 MHz, but as soon as something moves on the screen, watts pulled will skyrocket because the memory will need to fire up, and stay up for a very long time.  I suggest no less then 1/4 speed, 1/2 speed being the best setting for me, as a 2D game on battery power.

Be sure to check memory MHz.  Because I have AMD, it will reach zero at idle (bus mastering control).  Intel may not do this.  Don't take that down below half speed either.  If its not dynamic, to won't go back up like mine does, which may cause battery life lost.

Use

```
sudo rovclock -m (# here)
```

Check your battery life before tweaking and after with the command

```
acpi
```

to set memory MHz.

---

