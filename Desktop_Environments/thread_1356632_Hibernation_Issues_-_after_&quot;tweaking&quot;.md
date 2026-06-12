---
title: "Hibernation Issues - after &quot;tweaking&quot;"
date: 2009-12-16
forum: Desktop Environments
---

### Post by a-web on 2009-12-16
I have been running 9.4 on a Campaq Presario 2100 for a number of months, no problems.  Sleep, Hibernate and the such all worked perfectly!

A little bit ago I ran into wireless problems connecting to a WPA2 network (see this thread if you are interested: [http://ubuntuforums.org/showthread.php?t=1303516](http://ubuntuforums.org/showthread.php?t=1303516)).  During the tweaking that eventually got me online, my computer no longer hibernates or sleeps.  Just goes to a black screen and only responds to holding down the power button long enough to completely turn off.

Currently I am running 9.10; the hibernation issues started prior to the upgrade and persist in 9.10.

And there is my problem.  Thoughts?

---

### Post by a-web on 2009-12-24
Happy Christmas Eve....  Bump!

---

### Post by a-web on 2009-12-30
Even though the problem posted here is similar, I tried the solution and it did not work:
[http://ubuntuforums.org/showthread.php?t=1242156](http://ubuntuforums.org/showthread.php?t=1242156)

---

### Post by a-web on 2010-01-05
Update -

I reinstalled my OS, this time went with Xubuntu.  And upon install Hibernate and Sleep worked fine.  After I set up my wireless card/network, I can no longer Hibernate or Sleep....

---

### Post by SecretCode on 2010-01-05
Wireless, hibernate and suspend all work fine for me, so I can't help you with experience

But hibernate issues often relate to power management. Have you tried adding _acpi=off_ to your boot options?

---

### Post by a-web on 2010-01-11
How do I do that?

---

### Post by SecretCode on 2010-01-11
Do you see a boot menu when you power on? Saying "GRUB" at the top? If not, press Esc while booting and it should appear.

Press e to edit the boot options. You should see a number of lines, one of them start *kernel* and ending something like *ro quiet splash* (not all the line may be visible). 

Press e again to edit this line. Add '* acpi=off*' to the end of the line.

Press enter to accept the edit and b to boot.

---

### Post by a-web on 2010-01-11
I wasn't able to edit it that way... so I searching online and did```
sudo mousepad /etc/default/grub
```and this is what I have now:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX="acpi-off"
```But I am still unable to hibernate.

---

### Post by SecretCode on 2010-01-12
That may not have had any effect - try editing the same file so those lines read:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi-off"
GRUB_CMDLINE_LINUX=""
```
And then run
```
sudo update-grub
```

---

### Post by a-web on 2010-01-14
My grub file now looks like you advise, SecretCode... but still no hibernating.

---

### Post by SecretCode on 2010-01-14
Oh dear.

There must be other things to try, though.

I suggest finding your wireless card make and model - which you should get from *lspci* and/or *lshw -C network* - and searching the web for power / hibernation problems related to it.

---

### Post by a-web on 2010-01-15
hm... no dice.  Other ideas anyone?

---

### Post by balak on 2010-01-23
a-web, I don't go through the other thread entirely, but you changed your wireless card to get wireless working, right ?

It may be that your new card is making hibernate/suspend fail. You can find out the new card by doing 'lshw -C network | grep product'.
then google if there have been problems reported with that card.

Sometimes it is just a matter of programming the suspend/hibernate scripts to unload/load the corresponding modules before the respective action.

> **a-web said:**
> I have been running 9.4 on a Campaq Presario 2100 for a number of months, no problems.  Sleep, Hibernate and the such all worked perfectly!

A little bit ago I ran into wireless problems connecting to a WPA2 network (see this thread if you are interested: [http://ubuntuforums.org/showthread.php?t=1303516](http://ubuntuforums.org/showthread.php?t=1303516)).  During the tweaking that eventually got me online, my computer no longer hibernates or sleeps.  Just goes to a black screen and only responds to holding down the power button long enough to completely turn off.

Currently I am running 9.10; the hibernation issues started prior to the upgrade and persist in 9.10.

And there is my problem.  Thoughts?

---

### Post by a-web on 2010-01-24
Thanks, balak.  But even though I did switch wireless cards, I think I can rule out the card as the source of the problem:

When I first had Ubuntu, hibernation worked fine and I was online (with non-WPA2 networks).  Then I tried to get on a WPA2 and something I did messed up hibernation.  That was before I got a new card.  Hibernation continued to malfunction through me switching cards and getting online the WPA2.  Thinking I could "undo" whatever I did, I reinstalled (Xubuntu this time, it's an older computer) and hibernation worked until I set up the WPA2 connectivity.

I guess I could try to reinstall and use my older card and *try* to get back online... though that is a lot of work just for a chance of pinning down the problem.

---

### Post by a-web on 2010-03-09
FYI - new install of ununtu, not using WPA2 network...  hibernation works fine.

---

