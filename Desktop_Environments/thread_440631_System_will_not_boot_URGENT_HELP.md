---
title: "System will not boot *URGENT HELP*"
date: 2007-05-11
forum: Desktop Environments
---

### Post by davulf on 2007-05-11
Hi there,

I had a dual boot Ubuntu / XP, and hadn't been using Ubuntu in a while. So I just decided to use My Computer > Manager and delete the partition and reformat it. 

So I had windows running fine and whatnot, but when I went to restart, I get an Error 22 message from GRUB.

After some research, it seems like my MBR needs to be fixed. How can I do this? I have a Live CD. I need to get this working properly as I have valuable work files on the Windows. I think I just need to get the MBR installed properly to work. 

I tried to use the recovery console through the Windows CD, but it says it cannot find a hard drive. However, it shows the HDD in the BIOS, so I don't think there is something wrong with it (god I hope not).


Any help would be greatly appreciated. This is extremely important to me.

Thanks,
DaVuLf

---

### Post by honeydew on 2007-05-11
do you have a windows restore cd? when windows messes with the disks it tends to bork the mbr.  It has a windows or nothing type attitude.  Also you mint as well back stuff up if you have the abillity incase windows does something unexpected(like usual)

---

### Post by davulf on 2007-05-12
Hi there, thanks for the reply. Unfortunately, I cannot get into Windows to back things up (which sucks since I was in the middle of working when it restarted). I had done windows updates, and gone away from the machine, and it thought to restart itself on its own. 

If I put in the recovery CD (sincei its a laptop and I have no disk drive) it says that there is a problem with the hard drive. I should hope that there isn't, since this is EXTREMELY important information on there.

I think I just need to know how to restore the original MBR from the Live CD. 

Thanks,
DaVuLf

---

### Post by benanzo on 2007-05-12
If you put in any Windows install cd and "Press any key to boot from cd.." it will boot to the windows installer.

Then press R when it asks if you want to Install or Repair.  you want to repair.

This will take you to a DOS menu.  Select the number of the windows installation that it lists.

It looks something like this:

```

1: C:\

```

Press 1

It will then take you to a DOS prompt:

```

C:\ :

```

Press TAB to see a list of available commands.

Type FIXMBR at the prompt.  This will fix your MBR and allow Windows to boot normally.

---

### Post by TheTux on 2007-05-12
> **davulf said:**
> Hi there, thanks for the reply. Unfortunately, I cannot get into Windows to back things up (which sucks since I was in the middle of working when it restarted). I had done windows updates, and gone away from the machine, and it thought to restart itself on its own. 

If I put in the recovery CD (sincei its a laptop and I have no disk drive) it says that there is a problem with the hard drive. I should hope that there isn't, since this is EXTREMELY important information on there.

I think I just need to know how to restore the original MBR from the Live CD. 

Thanks,
DaVuLf

You can try to use [supergrub disk]("http://freshmeat.net/projects/supergrub/"). I used it once and it saved the day!

---

### Post by tabs on 2007-05-12
> **benanzo said:**
> If you put in any Windows install cd and "Press any key to boot from cd.." it will boot to the windows installer.

Then press R when it asks if you want to Install or Repair.  you want to repair.

This will take you to a DOS menu.  Select the number of the windows installation that it lists.

It looks something like this:

```

1: C:\

```

Press 1

It will then take you to a DOS prompt:

```

C:\ :

```

Press TAB to see a list of available commands.

Type FIXMBR at the prompt.  This will fix your MBR and allow Windows to boot normally.

I had the same problem and can confirm this worked (For me anyway)

---

### Post by davulf on 2007-05-12
As I had mentioned, the recovery console will not come up.

I tried the SuperGrub Disk, and that gives an error as well. 

Can I not just fix the MBR from Ubuntu?

---

### Post by Kevinator on 2007-05-12
Are they all giving the same error? If so, you are probably still trying to boot from your hard disk. You probably need to go into the BIOS setup and change the boot order.

---

