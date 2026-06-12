---
title: "System Going VERY Slow"
date: 2009-01-17
forum: General Help
---

### Post by jhoffman1986 on 2009-01-17
I attempted a dual-boot installatoin and had problems with Windows (who doesn't), so I deleted the partition, reinstalled GRUB, and just went back to my ubuntu partition.

Now, all of a sudden, my computer is going very slowly, and my web browsing is freezing up (going black) in Firefox.  In Windows, I would know how to go about troubleshooting this, but I'm completely lost in Ubuntu.  Can somebody help me troubleshoot this?

---

### Post by DeMus on 2009-01-17
> **jhoffman1986 said:**
> I attempted a dual-boot installatoin and had problems with Windows (who doesn't), so I deleted the partition, reinstalled GRUB, and just went back to my ubuntu partition.

Now, all of a sudden, my computer is going very slowly, and my web browsing is freezing up (going black) in Firefox.  In Windows, I would know how to go about troubleshooting this, but I'm completely lost in Ubuntu.  Can somebody help me troubleshoot this?

Can you give some information about the discs and partitions you have, what is in Grub (which OS's can you boot), what does System monitor tell you about cpu-usage, memory-usage, which processes ask for much power?
It looks obvious that the deleting of the Windows partition has caused this since your problems started after you did that, but do the two have anything in common or did something else happen?

DeMus

---

### Post by jhoffman1986 on 2009-01-17
I have a 79gig partition on which Ubuntu is installed, ext3 format. I have the unallocated space 9.77gig from the formatted partition i had installed windows on (i reformatted it when it didn't work into an ext3 format, but it has not been assigned).  Lastly, there is a 3.59gig extended/linux-swap partition (no idea what this is, but I assume it's system of some sort?).

I don't know how to find out what's in GRUB?

System Monitor shows my memory usage steady at around 30% (I have 1256mb RAM) and cpu usage of around 30%.  

As far as high memory processes, the highest is firefox, and the rest are 8mb or below.  Processor-percentage wise, system monitor is currently the highest (as I'm looking at it, followed by firefox, and compiz.real is taking around 1% on and off).

Basically, nothing I can see that's conclusive, but since I just switched to ubuntu a week ago, I'm no expert...

---

### Post by DeMus on 2009-01-17
> **jhoffman1986 said:**
> I have a 79gig partition on which Ubuntu is installed, ext3 format. I have the unallocated space 9.77gig from the formatted partition i had installed windows on (i reformatted it when it didn't work into an ext3 format, but it has not been assigned).  Lastly, there is a 3.59gig extended/linux-swap partition (no idea what this is, but I assume it's system of some sort?).

I don't know how to find out what's in GRUB?

System Monitor shows my memory usage steady at around 30% (I have 1256mb RAM) and cpu usage of around 30%.  

As far as high memory processes, the highest is firefox, and the rest are 8mb or below.  Processor-percentage wise, system monitor is currently the highest (as I'm looking at it, followed by firefox, and compiz.real is taking around 1% on and off).

Basically, nothing I can see that's conclusive, but since I just switched to ubuntu a week ago, I'm no expert...


CPU usage of 30%? Which programs or processes are running that take so much cpu power? You say system monitor is the nr.1 in the list, but this process normally only uses a little. How much does it use and what kind of processor do you have? I ask this since 30% usage on an old celeron processor is something different from 30% on a new quad core.

DeMus

---

### Post by jhoffman1986 on 2009-01-17
This computer is around 3 years old.  1.6gig pentium m.  My computer was also downloading with downthemall at the time.  However, it runs slow period.  Is this just something I should reformat my computer again for?

---

### Post by cariboo on 2009-01-17
Remember Linux is not Windows, just because it is common to reinstall windows to fix a problem, it doesn't mean you need to do the same thing with Linux.

Open System-->Preferences-->Sessions and under Startup Programs disable anything you don't need.

AT SPI Registry Wrapper is used with Orca, so if you don't use Orca, you don't need it. THe rest of the applets are self evident.

Jim

---

### Post by DavidFourer on 2009-02-04
> **cariboo907 said:**
> Open System-->Preferences-->Sessions and under Startup Programs disable anything you don't need.

Jim
I also have slow graphical user interface, and not just Firefox.  I want to try your suggestion.  Is there anything in that list of start-up programs that would put me in a dire situation if I un-checked it?  For example, the last one is "Window Manager".

Slow graphical user interface.  Video struggles-really bad, all windows open and close slowly, Firefox not implicated.  I upgraded from 8.04 to 8.10 last week, and all was fine for a few days.  While fixing my internet connection, this problem started.  Re-boot is no help.

Dell inspiron 6000 with 1 gig ram
Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) Intel Celleron 1.4 GHz, 2.6.27-11-Generic
System monitor reports excessive CPU activity, Normal was 3% at ilde.  Now starts at 15% and increases to 50-100%
Only process using resources is system monitor.

---

