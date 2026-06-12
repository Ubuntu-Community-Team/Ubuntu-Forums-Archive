---
title: "time slows down"
date: 2005-12-29
forum: Desktop Environments
---

### Post by Bruce Adams on 2005-12-29
I'm have a strange problem. After several hours of use, my machine gets flaky. It freezes for short periods of time (sometimes with the system alert sound playing (I need a smiley covering it's ears :) )). I have the System Monitor running in the top panel, with CPU, memory, network and disk all showing. Nothing looks like heavy use there. I do not see anything interesting running 'top' either.

The one interesting thing I've seen is that time appears to slow down. I have seconds showing on the clock (also on the top panel--always visible). When the system gets weird, I look at the clock and it's a minute or two behind real time. (I have an radio synched clock on my desk and my Ubuntu machine is normally doing NTP with good reference machines. When things are normal, the clocks are dead on each other.) Watching the Ubuntu clock, the seconds tick off very slowly--no skips--it is not that the clock process is not getting system resources, the system clock is running very slowly. If I give the 'date' command in a terminal window, it agrees with the on-screen clock (that is, a couple of minutes behind real-time).

Once I get into this strange place, the only path out appears to be a reboot. If I don't reboot fairly quickly (five minutes or so) I'll completely lose control of the system and have to hard boot it.

I've seen the problem with NTP turned on and turned off. I don't think I'm running anything weird on this system. I don't even know what to look for. I scanned the wiki and the forums, but have not found anything that sounds similar.

Any suggestions?

---

### Post by stuporglue on 2005-12-29
What kind of machine are you running? I've heard of time problems on AMD 64s. 

Could it be overheating?

---

### Post by Bruce Adams on 2005-12-29
It's a Pentium 4 (an IBM NetVista desktop machine).

It has recently run CentOS 3.6 with no problems and Windows 2000 before that.

I don't think it's a hardware failure. I guess I don't have an easy way to prove that. (It's not dual boot.) I guess I could run a live CD (Knoppix or whatever) for a couple of days to see if anything goes weird there.

---

### Post by mesocool on 2005-12-30
[QUOTE=Bruce Adams]I'm have a strange problem. After several hours of use, my machine gets flaky. It freezes for short periods of time (sometimes with the system alert sound playing (I need a smiley covering it's ears :) )). I have the System Monitor running in the top panel, with CPU, memory, network and disk all showing. Nothing looks like heavy use there. I do not see anything interesting running 'top' either.

The one interesting thing I've seen is that time appears to slow down. I have seconds showing on the clock (also on the top panel--always visible). When the system gets weird, I look at the clock and it's a minute or two behind real time. (I have an radio synched clock on my desk and my Ubuntu machine is normally doing NTP with good reference machines. When things are normal, the clocks are dead on each other.) Watching the Ubuntu clock, the seconds tick off very slowly--no skips--it is not that the clock process is not getting system resources, the system clock is running very slowly. If I give the 'date' command in a terminal window, it agrees with the on-screen clock (that is, a couple of minutes behind real-time).

Once I get into this strange place, the only path out appears to be a reboot. If I don't reboot fairly quickly (five minutes or so) I'll completely lose control of the system and have to hard boot it.

I've seen the problem with NTP turned on and turned off. I don't think I'm running anything weird on this system. I don't even know what to look for. I scanned the wiki and the forums, but have not found anything that sounds similar.

Any suggestions?[/QUOTE]

I got the same problem.. My machine is sony vaio with P4 2.80C. :confused:

---

### Post by antidrugue on 2005-12-30
Which kernel are you using?
```

uname -a

``` 
What exact model of CPU?
```

cat /proc/cpuinfo

``` 
Post those two please.

Even if other distros are doing find, still verify that you have the latest bios for your motherboard.

---

### Post by mesocool on 2005-12-30
[QUOTE=antidrugue]Which kernel are you using?
```

uname -a

``` 
What exact model of CPU?
```

cat /proc/cpuinfo

``` 
Post those two please.

Even if other distros are doing find, still verify that you have the latest bios for your motherboard.[/QUOTE]

guanyu@home:~$ uname -a
Linux home 2.6.12-10-386 #1 Thu Dec 22 11:37:10 UTC 2005 i686 GNU/Linux


guanyu@home:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 8
cpu MHz         : 2788.418
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss
bogomips        : 5488.64

Thanks..

---

### Post by antidrugue on 2005-12-30
Ok... I was trying to know if you had a Prescott Pentium 4 (with hyper threading), which you don't.

So, I suggess you do this:
```

dpkg -l | grep 386

```

To know exactly what you have installed right now. It will probably be something like this:

linux-image-2.6.12-10-386
linux-restricted-modules-2.6.12-10-386

So just install the corresponding 686 kernel and kernel-modules:
```

sudo apt-get install linux-image-2.6.12-10-686 linux-restricted-modules-2.6.12-10-686

```

And reboot in your new 686 kernel, see if it makes a difference...

---

### Post by Cordate on 2005-12-30
I've heard that time can slow down when you're not having fun- maybe you just need to try some new games ;)

---

### Post by robertobaggio2k on 2005-12-30
i've had the same problem my computer starts to lag badly i cant even move the mouse smoothly at times, i've got an amd  xp 1800+, its been doing these the last couple of days not before, i only have installed the gdesklet for hd space n usually have running gaim and firefox and music, dont know y it does this :S but the red light on the pc goes nuts

---

### Post by mesocool on 2006-01-02
[QUOTE=antidrugue]Ok... I was trying to know if you had a Prescott Pentium 4 (with hyper threading), which you don't.

So, I suggess you do this:
```

dpkg -l | grep 386

```

To know exactly what you have installed right now. It will probably be something like this:

linux-image-2.6.12-10-386
linux-restricted-modules-2.6.12-10-386

So just install the corresponding 686 kernel and kernel-modules:
```

sudo apt-get install linux-image-2.6.12-10-686 linux-restricted-modules-2.6.12-10-686

```

And reboot in your new 686 kernel, see if it makes a difference...[/QUOTE]

I install them, but it doesn't fix the problem and I think my CPU is with hyper threading.. :(

---

### Post by briancurtin on 2006-01-02
bring up the system monitor and look at the resources tab. near the top will show your CPU status: does it show CPU1 and CPU2? if so, you have hyperthreading (or two separate processors, but you would know that)

---

### Post by mesocool on 2006-01-02
[QUOTE=briancurtin]bring up the system monitor and look at the resources tab. near the top will show your CPU status: does it show CPU1 and CPU2? if so, you have hyperthreading (or two separate processors, but you would know that)[/QUOTE]

Just one CPU tab.. Then what's the problem with the slowing clock.. Thanks.. :confused:

---

### Post by mcduck on 2006-01-02
You should run 'sudo apt-get install linux-686-smp' to get a kernel that supports hyperthreading/multiple CPU's :)

(It's better to install metapackage pointing to newest kernel instead of installing the kernel image itself. This way you'll get everything needed, and also automatic updates)

---

### Post by antidrugue on 2006-01-03
[QUOTE=mcduck]You should run 'sudo apt-get install linux-686-smp' to get a kernel that supports hyperthreading/multiple CPU's :)

(It's better to install metapackage pointing to newest kernel instead of installing the kernel image itself. This way you'll get everything needed, and also automatic updates)[/QUOTE]

Yes we know that, but his CPU doesn't have hyper threading. ;) 

Try too boot computer in "Recovery Mode", so no X (no graphics, only a console). Leave it that way for as much as it normaly need to go crazy.

Could it be a problem only with X? That's what it will tell you.

From there use the command
```

date

```

To check if clock is slowing down as well, when no X server loaded.

---

### Post by Bruce Adams on 2006-01-03
```

$ uname -a
Linux ba 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux
$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.40GHz
stepping        : 7
cpu MHz         : 2392.707
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid
bogomips        : 4734.97

```
after installing 686 kernel and rebooting
```

$ uname -a
Linux ba 2.6.12-9-686 #1 Mon Oct 10 13:25:32 BST 2005 i686 GNU/Linux

```

I have not yet run the 686 kernel long enough to know if the problem will recur.

You also suggested checking that I have the latest BIOS. It took me a little while to figure out how to check that.
```

$ sudo biosdecode
#### many lines omitted ####
        BIOS Build ID: 24KT36AUS
        Box Serial Number: KLLTP1G
        Motherboard Serial Number: IBM
        Machine Type/Model: 830542U

```
Checking IBM/Lenovo's web site, I find "... Critical BIOS update ..." here: [http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=TCTR-ERRN91&sitestyle=ibm](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=TCTR-ERRN91&sitestyle=ibm)

Checking for my specific machine, I find this page: [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-42952](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-42952) which says the new BIOS version is 24KT55A. *biosdecode* shows me running an older version, 24KT36A (with a "US" on the end just to make it harder for me to Google the version number, groan).

Now I have to figure out how to write a bootable floppy from Ubuntu :-)

---

### Post by Bruce Adams on 2006-01-03
I did apply the BIOS upgrade (which is distributed as a Windows executable :( ). The readme for the BIOS fixes contained enough scary stuff that I figured an upgrade was appropriate. I get to hope that it fixes my "time slows down" problem as well.

There was a bump after updating the BIOS. X windows would not startup. Going into BIOS setup and changing the BIOS Display from PCI to AGP got me going again.

---

### Post by Bruce Adams on 2006-01-04
It's pretty clear to me that the BIOS update solved my problem. It's been up and stable for nearly a day now. Yeah! :D

---

### Post by antidrugue on 2006-01-05
Glad it helped! Happy new year!

---

### Post by Bruce Adams on 2006-01-05
Oops. I had the problem again... while running the updated BIOS and an up-to-date 686 kernel.
```
$ uname -a
Linux ba 2.6.12-10-686 #1 Thu Dec 22 11:55:07 UTC 2005 i686 GNU/Linux
```

After I'd lost control of my X windows setup, I did manage to switch to virtual console #1 (via Ctrl-Alt-F1) and ran the 'date' command several times. I was amazed to see time move both forwards and backwards, several times, by as much as a few seconds. It seemed like something was actively setting the time back. I did not have NTP running (although I have seen the problem when I did have NTP running). I'm baffled. What might mess with the system clock?

---

### Post by AmboyGuy on 2006-01-05
Never Mind -------

---

### Post by nxn on 2006-01-05
I'm having the same problem as you, here's my thread: [http://www.ubuntuforums.org/showthread.php?t=112250](http://www.ubuntuforums.org/showthread.php?t=112250)

I don't think it's X related since even when I kill x and get into a terminal it still lags and has time issues.

On a side note I also have an IBM NetVista, but that might just be random luck, figured I should mention it though.

---

### Post by antidrugue on 2006-01-05
CMOS battery ? (though I don't think so, both because your machine is so new and because your other OS don't seem to have the same problem -- maybe they have NTP enable)

BIOS settings ? (some motherboards apparently disable the clock as a power saving feature)

ACPI ?

Check out [ this thread](http://ubuntuforums.org/showthread.php?t=53094).

---

### Post by nxn on 2006-01-05
In my experience the CPU usage remains really low during the slowdown, as if it's idling (0-3%), also I can move windows as smooth as always, so I'm assuming it's not ACPI.

The problem is when I try to start a new program or close one, if I click on the terminal icon in my launcher it will take at least 5 minutes for the window to show up, getting out of X and killing everything related to X doesn't help.

As for the clock nearly halting or even going back in time a second or two is an effect rather than the cause of the slowdown. I don't know if it's like that for Bruce, but reading his posts the symptoms seem identical. I even get the system beep if it goes on too long and I try to run a bunch of programs like dmesg/top trying to figure out the cause.

Looking at my logs I'm seeing some slight correlation with cron.hourly executing (although I have nothing in /etc/cron.hourly) except the placeholder file. And it doesn't screw up every time cron.hourly executes, in fact it seems random, but it does happen within a few minutes difference of it. (I know this because the clock is halted and when I come back I see when it happened ;). I also see some correlation with random asshats trying to ssh into here as root and not doing a good job at it. I disabled sshd for the time being to see if that might be the cause.

EDIT: 
Other threads on this: [http://www.ubuntuforums.org/showthread.php?t=47330&highlight=slow+clock](http://www.ubuntuforums.org/showthread.php?t=47330&highlight=slow+clock) 
[http://www.ubuntuforums.org/showthread.php?t=80704&highlight=slow+clock](http://www.ubuntuforums.org/showthread.php?t=80704&highlight=slow+clock)

The metacity theme idea in the last link seems promising, it's so ridiculous it just might work, and thinking about it, I did not have this problem when I was using the Human theme.

---

### Post by Bruce Adams on 2006-01-06
Some reasons that I think the system clock is at the center of the problem. When the problem hits:
[LIST=1]
[*]Launching an application does an animation (of an expanding box). The animation involves short sleeps between frames. I assume the sleep durations are based on the system clock.
[*]A system beep can go on for a very long time when this problem occurs. Again, I suspect the beep is setup to go for a period of time (say 0.2 seconds) and depends on the system clock for that timing. Complex sounds do not have this problem, only the system beep. (This makes "sudo shutdown now" painfully noisy, as well as slow.)
[*]Auto repeat on the keyboard does not work. Auto repeat is based on a real-time clock--I assume it's the system clock again.
[*]The System Monitor (which I have running in the top panel) stops updating. I have it set to update every tenth of a second (this lets me see the time problem quickly).
[/LIST]

If I stay away from things that depend on time, the system behaves OK.

You mention having a IBM Netvista. Exactly which model? (I wonder if it is the same as the one I have.) "sudo biosdecode" will tell you near the end of it's long output.
```
$ sudo biosdecode
#### some stuff omitted ####
        BIOS Build ID: 24KT55AUS
        Box Serial Number: KLLTP1G
        Motherboard Serial Number: IBM
        Machine Type/Model: 830542U

```

The last line is the IBM model number (without the dash): 8305-42U

P.S. I forgot to say "Thank you" for the pointers to other threads on this subject. Lots of those threads mention Netvista hardware as well.

---

### Post by nxn on 2006-01-06
I don't have the same exact model, but it does seem like an IBM problem. I also don't use the onboard video or sound, but I'm not sure if they're disabled or not, either way I doubt it would be related to either.
```

        BIOS Build ID: 24KT54AUS
        Box Serial Number: KLHMK9C
        Motherboard Serial Number: IBM
        Machine Type/Model: 831038U

```

I'd update the bios but I don't have windows anymore so their .exe files are worthless.

Moving on, It's not an issue with the theme like I hoped, it happened again after switching back to Human. Now I'm trying with the noapic kernel paramater, so far it's been about 8 hours, which doesn't seem bad, but I'd have to have an uptime of 2 or 3 days before I'd be satisfied that it fixed the problem. And even then I still saw APIC messeges in my logs after I put the parameter in, so I'm not positive that the paramater is even doing anything for me.

I'm too lazy to configure my own kernel right now, unless the kernel config is available for the prebuilt kernels ubuntu uses somewhere. However if this doesn't work, I'll be left without a choice.

Anyway, another link with somethings to try: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=284477](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=284477) The majority of people posting there said disabling apic in one way or another worked around the problem, although someone said he HAD to do it through the kernel to get it to work. I don't know, worth a shot if you haven't tried it before.

---

### Post by tmeier on 2006-01-06
Have you checked your RAM to see if it has any issues?  There is a good memory checker at [http://www.memtest86.com](http://www.memtest86.com).  I had a windows machine acting funny and this was the issue a bad stick of RAM.  Something easy to check anyway.

---

### Post by Bruce Adams on 2006-01-06
Good thought. I'm running memtest86 now.

The Breezy installer put it on my hard disk and added it to my grub boot pick list. It was really easy to kick off. Another example of Ubuntu doing the right thing.

---

### Post by nxn on 2006-01-06
Yeah, I tried memtest, it was fine. I'm pretty sure the noapic kernel boot parameter solved my problems, it's been up for almost 17 hours now, which was almost impossible before.

---

### Post by Bruce Adams on 2006-01-12
The "noapic" kernel parameter solved my problem as well. I have an uptime of over three days now.

Thanks for all the help!

---

