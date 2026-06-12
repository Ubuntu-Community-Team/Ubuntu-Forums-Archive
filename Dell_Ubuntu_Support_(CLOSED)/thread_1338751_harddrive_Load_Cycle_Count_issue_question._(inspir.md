---
title: "harddrive Load_Cycle_Count issue question. (inspiron 11z)"
date: 2009-11-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by benma on 2009-11-26
Hello.
I recently purchased Dell Inspiron 11z (dual core version).
I wanted to install Ubuntu (or Xubuntu) on it,
but was scared by reports about the harddrive Load_Cycle_Count issue, on laptops and ubuntu, and wanted to know if that bug was fixed on ubuntu 9.10?

Thanks in advance for any help.

---

### Post by Dennis N on 2009-11-27
I have checked the load cycles in 8.10 and after, and I find it is no longer an issue as it once was (in Feisty, for example). The only time my load cycles increase now is when I start up or shut down if on AC power, as you would expect, and also not excessive if on battery power.

Specific machines: Dell E1505 and 6000.

---

### Post by benma on 2009-11-28
What's the most updated way to check if this bug happens and to fix it if needed?

---

### Post by Dennis N on 2009-11-28
> **benma said:**
> What's the most updated way to check if this bug happens and to fix it if needed?

You need to install the package 'smartmontools' from the Ubuntu reopsitory. Then, search these forums for 'smartmontools' to read up on how to use the tools. You may need to search in the 'Forum Archives' section below the 'Main Support Sections', since many of these threads are inactive (read-only) from 2007 or 2008 and won't show up searching the active threads.

You can also use the tools to monitor other stuff besides the load cycles, like temperature.

As I said, you should not be worried about too many load cycles. I'm sure the problem was fixed.

---

### Post by mikewhatever on 2009-11-30
Install smartmontools:

```
sudo aptitude install smartmontools
```

then check the cycle count

```
sudo smartctl -a /dev/sda | grep Load_Cycle_Count
```

It's also important to understand, that no hard drive is going to last forever.

---

### Post by benma on 2009-11-30
I tried that and saw that the problem wasn't fixed. Tried some solutions, without any success. The number still goes up. (About 2-4 points in 15 minutes).

---

### Post by Menthu_Rae on 2009-11-30
> **benma said:**
> I tried that and saw that the problem wasn't fixed. Tried some solutions, without any success. The number still goes up. (About 2-4 points in 15 minutes).

You can disable power management on the drive which will stop it spinning down...

```
sudo hdparm -B 255 /dev/sd**X**
```

Where X is the letter corresponding to your disk drive in question.

There is a way to insert that code into the startup and resume (from standby, hibernate, etc) - but I'm not sure exactly.

I just manually disable it on my laptop. The clicking of the heads unloading and loading is really annoying **and this is seriously one bug that should be fixed.**

EDIT: See here for bug report --> [https://wiki.ubuntu.com/DanielHahler/Bug59695](https://wiki.ubuntu.com/DanielHahler/Bug59695)

---

### Post by mikewhatever on 2009-11-30
> **benma said:**
> I tried that and saw that the problem wasn't fixed. Tried some solutions, without any success. The number still goes up. (About 2-4 points in 15 minutes).

I don't think you realize that this is a useful feature and not a problem. If you have Windows installed, it does exactly the same. Karmic has a checkbox to enable/disable that feature in Gnome Power Management, so that I wouldn't worry too much.

---

### Post by LMP900 on 2009-11-30
No need to install smartmontools in Karmic. Go to System > Administration > Disk Utility, then click on the "More Information" link.

I have a notebook with a 5400RPM 500GB hard drive. Should I enable "Spin down hard disks when possible" under power management? Which would extend the life of my hard disk?

In one scenario, constant spinning up and down would increas load cycle count, but in another scenario, a never-idle disk may degrade quickly. Anyone have an expert opinion? I can't seem to find on on the web (perhaps I'll look harder...)

Thanks

---

### Post by Dennis N on 2009-12-01
> **benma said:**
> I tried that and saw that the problem wasn't fixed. Tried some solutions, without any success. The number still goes up. (About 2-4 points in 15 minutes).

Did you test this on AC or battery power?

At the rate you are describing, that's about 15 per hour which I think would be considered normal on battery power. As mentioned in the posts above, Windows does this too, and it is by design.

On AC power it should produce no increases or very few while in use - only on start and shutdown.

A laptop hard drive is rated to last for hundreds of thousands of load cycles over its lifetime, and by simple arithmetic, it would take years to amass that many at the rate you give.

---

### Post by mikewhatever on 2009-12-01
I think the reason the number increased was probably because the testing was done from a live media, in which case the disk is not used at all. Once Ubuntu is installed, data gets written to and read from the disk every few seconds, so that Load_Cycle_Count increase is reduced to a minimum.

---

### Post by benma on 2009-12-03
I tested it when using a battery.
I understand that windows and mac-os override this hardware behavior.
From what i read that load cycle count should not go more than a few points a day.
I did the check after installing xubuntu 9.10, since i thought the power management is done by ubuntu itself and not the desktop environment.
But from your posts it seems that gnome has an option to put power management in a state to reduce load cycle count?  
Still, i think ubuntu SHOULD do what windows an mac-os do, to override this hardware's default behavior of aggressive power management.

---

### Post by mikewhatever on 2009-12-03
> **benma said:**
> I tested it when using a battery.
I understand that windows and mac-os override this hardware behavior.
From what i read that load cycle count should not go more than a few points a day.
I did the check after installing xubuntu 9.10, since i thought the power management is done by ubuntu itself and not the desktop environment.
But from your posts it seems that gnome has an option to put power management in a state to reduce load cycle count?  
Still, i think ubuntu SHOULD do what windows an mac-os do, to override this hardware's default behavior of aggressive power management.

I can't speak on behalf of OSX, but Windows XP does exactly the same trick when you are on battery. In other words, heads are parked after a period of inactivity, which is usually longer when on AC and shorter when on battery. In XP, When on AC, the number may go up a few, or a few hundred points a day, depending on usage and on power settings, and more so when on battery, which is normal and expected. It's really easy to get wrong impressions from dramatic thread titles like 'ubuntu is killing my hard drive', but most of it is FUD and came from ignorance. If in doubt, it's a good idea to keep watching the load cycle number, but keep in mind, that it's expected to rise when on battery, and that, no matter what you do, that hard drive isn't going to last forever.

---

### Post by benma on 2009-12-04
Ok, but in threads that say something like "ubuntu is killing your harddrive" ,it says that under ubuntu the HD will live for less than 2 years, under the current state, when Load_Cycle_Count goes up that quickly.
These threads also say that under ubuntu this number goes up much quicker than under osx or windows. Is there a way to check the Load_Cycle_Count under win7?

p.s. Are you sure that under Ubuntu 9.10 no fixes/ugly fixes needed to be done?
BTW here's one post i'm talking about: [http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/](http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/)

---

### Post by mikewhatever on 2009-12-04
As said before, some people were severely affected, and others were not. Regardless, the problem was dealt with, and the load cycle bug reports are all labeled as fixed. As you may have noticed, the blog post you quoted is just over 3 years old. You shouldn't need the ugly fix with either Karmic or Jaunty, and all the way back to Hardy, moreover, having been been tailored for much older releases, I'd be surprised if it still worked.
I don't know anything about checking Load_Cycle_Count in W7, you probably can. The way I did it on a dual boot notebook, was checking the Load_Cycle_Count in Ubutnu, then rebooting to Windows, using it regularly for a few hours or days (whatever suited my needs), then checking again in Ubuntu right after startup.

---

### Post by benma on 2009-12-05
I founs smartmontools for windows.
The Load_Cycle_Count in windows 7 doesn't go up.
While under ubuntu it went about 5 points in 15 minutes.
So there're 2 options: the bug wasn't really fixed in ubuntu, or windows manages the power MUCH better than ubuntu.

---

### Post by mikewhatever on 2009-12-05
It would be interesting to know how exactly did you tested in both cases? Was Ubuntu installed to the HDD or running from a live media? Was it on battery or on AC? Was the computer idle or under load? Regardless, 15 minutes is not enough to tell anything definitively. Perhaps you should file a bug report against your particular hardware, I don't know.
Lastly, I don't see any merit in discussing W7's advantages here. If you think it's better, well, use it, and if you still want help with Ubuntu, let us stick to Ubuntu and leave W7 for the Recurring Discussions section.

---

### Post by benma on 2009-12-05
It was xubuntu, installed on hdd. Was tested on ac and on battery. both idle and load tested.
I do like Ubuntu. My point was that if W7 does it, i expect Ubuntu to do that.
BTW, i decided to give Ubuntu a try on my laptop, after using Xubuntu on my desktop for several years, since Ubuntu might be a more complete system (Desktop Environment more sofisticated). Also it has an option in power manager "spin down hard disks when possible" which can be off when on laptop.
It seems so far that the load_cycle_count is stable.
Also multimedia keyboard works much better.

---

### Post by pveurshout on 2009-12-30
I can confirm this is still an issue, using an HP EliteBook 8530w. Plugged in it is fine, but when on battery the Load Cycle Count starts increasing like crazy (several times per **minute**). When I unmark 'Spin down hard disks when possible' (and reboot) the frequency seems to go down somewhat, but I still got multiple spin cycles in just a couple of minutes.

My advice to everyone would be to check this out for your own situation and, if necessary, be careful. My Load Cycle Count currently approaches 2000, which is nowhere near critical but still worries me as I practically *never* use my laptop on battery (plugged in it does not spin down at all, except at shut down of course).

---

### Post by pveurshout on 2010-01-07
It's at about a 100 per hour on battery, regardless of the 'Spin down hard disks when possible'-setting. This is bad.

---

### Post by mikewhatever on 2010-01-07
> **pveurshout said:**
> It's at about a 100 per hour on battery, regardless of the 'Spin down hard disks when possible'-setting. This is bad.

File a bug report at launchpad.net.
Meanwhile, you can issue the following command every time you are on battery as a temporary workaround:

```
sudo hdparm -B 255 /dev/sda
```

Edit:

After some testing, it seems the Load_Cycle_Count increase is unreasonably high in my case too, 36 in about 25 min of idleness. I'll file a bug report, but for the time being, there seems to be an easy workaround that works in my case. Basically, it sets the <hdparm -B> value higher then 128 when on battery, thus preventing aggressive power management. I haven't tested it much, so apply at your own risk.

gksudo gedit /usr/lib/pm-utils/hdparm-functions

find the following section (close to the end):
```
if hdparm_is_on_battery; then
                OPTION="128"
```

change it to:
```
if hdparm_is_on_battery; then
                OPTION="192"
```
save and exit.

To test, unplug the power cord and run 
<sudo hdparm -I /dev/sda | grep "Advanced power management level">
It worked if the output is <Advanced power management level: 192>.

Bug report: [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/504573](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/504573)

---

### Post by pveurshout on 2010-01-16
This seems to work. Have you experienced any problems with the fix since you started using it? Anyway, thanks!

---

### Post by mikewhatever on 2010-01-18
> **pveurshout said:**
> This seems to work. Have you experienced any problems with the fix since you started using it? Anyway, thanks!

No, but I haven't tested it with suspend to disk or RAM yet.

---

