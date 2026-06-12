---
title: "Vista/XP/Ubuntu 8.10 Triple Booting Issue"
date: 2008-12-13
forum: General Help
---

### Post by Phil149 on 2008-12-13
So I have a Triple boot with Vista/XP/Ubuntu 8.10 and I can boot into Ubuntu and XP, but not Vista.  I'm using the GRUB boot loader, but to boot into Vista and XP I have to go to a second menu (Vista's Bootloader, I think).  When Vista tries to boot, it shows the screen that says "Welcome" and has a background, but then my screen flashes and it restarts. :mad:

Thanks

---

### Post by TeXtonyx on 2008-12-13
So you can boot XP and Ubuntu completely, just not Vista?
This is not a grub error or you wouldn't get a Welcome screen.
Vista needs to be repaired. The first step to try is Testdisk
because the second step of using Vista's Startup Repair makes 
some more work of restoring the Ubuntu grub menu to the MBR.

---------------------------------------------------------

I borrowed this advice from meierfra about using
Testdisk. sda is the first drive and sdb is the second drive and so on.

"You might try testdisk to rebuild the Boot sector:

Code:

sudo apt-get install testdisk
sudo testdisk /dev/sda

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"

--------------------------------------

RebuildBS uses a backup of your boot sector. If the backup and
the current boot sector are not identical then you want to use
Testdisk to restore the backup (maybe it says write).

If you have a Vista OEM recovery cd, rather than a Vista install cd
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

bootrec /fixmbr
bootrec /fixboot
bootrec /rebuildbcd

---

### Post by Phil149 on 2008-12-13
Do I need to use both methods, or can I just use the Vista Recovery CD?  Also, if I use the Vista Recovery CD, will it change GRUB?

Thanks again

---

### Post by Tim Sharitt on 2008-12-13
Using the Vista recovery CD should get Vista going. I think you will have to reinstall grub, there is a guide at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Phil149 on 2008-12-13
If I use TestDisk will I need to reinstall GRUB?

---

### Post by Tim Sharitt on 2008-12-13
> **Phil149 said:**
> If I use TestDisk will I need to reinstall GRUB?
If you're only repairing the Vista partition (with test disk), it shouldn't be necesary. Hoeever, if you must use the vista disk to do the repairs, it has a bad habit of overwriting grub in the mbr.

---

### Post by Phil149 on 2008-12-14
Thanks for your help.

---

### Post by TeXtonyx on 2008-12-14
> **Phil149 said:**
> If I use TestDisk will I need to reinstall GRUB?

I wrote in post #2

"Vista needs to be repaired. The first step to try is Testdisk
because the second step of using Vista's Startup Repair makes
some more work of restoring the Ubuntu grub menu to the MBR."

That means Testdisk is less work because you don't have to do
some more work of restoring the Ubuntu grub menu to the MBR.

That is why Testdisk is the first step because if it works 
you don't need a second step. If you needed to use both steps
regardless of whether the first step worked, then you would
have to reinstall grub in any case. And there would be no 
reason to say, 'the first step to try is Testdisk', because it's
less work to be able to skip the works of reinstalling grub,
if it didn't matter what order the steps were taken because it 
was necessary to do both of them regardless; there would be the
same amount of work if you had to run testdisk first and then
Vista Recovery second, or Vista Recovery first and then run 
testdisk second. There is only less work when you have to do
only one step; not both steps because the order wouldn't matter.

Phil149 wrote: "Do I need to use both methods, or can I just 
use the Vista Recovery CD? Also, if I use the Vista Recovery CD, 
will it change GRUB?"

TeX wrote:"Vista needs to be repaired. The first step to try is 
Testdisk because the second step of using Vista's Startup Repair 
makes some more work of restoring the Ubuntu grub menu to the MBR."

The reason one needs to restore the Ubuntu grub menu to the MBR
is because Grub has been changed. If grub were not changed, then
one would not need to restore grub to the MBR. I didn't think
it would confuse you to say, "Ubuntu grub menu to the MBR", rather
than to say 'grub to the MBR', I thought it would make it clearer.

It takes about 20 minutes to run Vista Startup Repair and then
next change grub after booting up from another cd. I think probably
(not sure) Vista's Recovery Console (RC) would do the work of Testdisk.
But running Testdisk from Ubuntu takes about 2 minutes. And nobody
knows beforehand whether you need to use both methods. So the right
order of steps is to start with the 2 minute step first. If you have
to use the 20 minute step next, also that's 22 minutes. If the 2
minute method works first, you save 18 minutes over trying the 20
minute method first when it works. Even if Testdisk had only a
1 in 5 chance of fixing the problem, and RC had a 4 in 5 chance of
fixing the problem, considerably better, one would still run Testdisk
first, because 4 wasted tries of 2 minutes = 8 minutes, and on the
fifth try that 2 minutes saves you the 18 minutes that RC and grub take.
That is still quite an advantage to trying Testdisk first.

---

### Post by Phil149 on 2008-12-16
First off, thanks for the input.  But when I used Testdisk it said that the boot sector was OK.  Next, when I say that I can boot to the Welcome Screen, it's Vista's Welcome Screen (the one with the Vista Background and the loading symbol).

---

### Post by TeXtonyx on 2008-12-17
"I'm using the GRUB boot loader, but to boot into Vista and XP 
I have to go to a second menu (Vista's Bootloader, I think)."

Does XP boot from the Vista bootloader? When two versions of Windows
are installed on the same drive the boot files usually all migrate
to just one Windows partition. That will create problems for grub.
So if you can boot XP, can use My Computer to look at the boot files
on C:\ and also the boot files on Vista? Are they all on one Windows
partition? 

Before you get to Vista's Welcome screen, can you repeatedly tap
F8 and get to the safe boot menu? By default, if there is a 
serious error it will reboot. F8 has an option not to automatically
reboot, but to display the error message which causes the reboot,
the next time it happens, instead of just rebooting.

Did Vista ever work? Do you know of anything that happened to
cause Vista problems? If Vista worked did you do anything which
might impact Vista like resize a partition. During the Ubuntu 
install, choosing resize the Windows partition can sometimes
cause a problem.

Microsoft recommends running Startup Repair first. There's a 
screenshot attached at the bottom of this post.

If that does not work then try using the Command Prompt which is
the last choice shown on the attached screenshot of Recovery options,
and typing them in using the following order.

C:\bootrec /fixmbr   <enter>
C:\bootrec /fixboot  <enter>
C:\bootrec /rebuildbcd <enter>

If XP works, I would check out the boot files situation but maybe
not fix it yet. Just see if the boot files are congregated. Then 
I'd try Startup Repair, and if that fails, the bootrec commands. 
This might generate an error message which pertains to why you have 
spontaneous reboots (the F8 idea I mentioned) or boot files problem.

Vista will overwrite the MBR if this works or not. Test it to make sure 
it boots once, before restoring grub to the MBR from the Ubuntu live cd.

---

### Post by caljohnsmith on 2008-12-17
> **TeXtonyx said:**
> 
C:\bootrec /fixmbr   <enter>
C:\bootrec /fixboot  <enter>
C:\bootrec /rebuildbcd <enter>

If you want to keep using Grub as your boot loader Phil149, I would not recommend running "bootrec /fixmbr", because that will replace Grub with a Windows MBR; then you for sure won't be able to boot Ubuntu immediately after that. As TeXtonyx mentioned, most likely your XP and Vista boot files are in one partition together. If you would like to be able to boot XP and Vista separately from the Grub menu, how about downloading the attached "boot_info9.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info9.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what it would take to boot XP and Vista separately. :)

---

### Post by TeXtonyx on 2008-12-17
"When Vista tries to boot, it shows the screen that says "Welcome" 
and has a background, but then my screen flashes and it restarts."

That seems to me to be the main problem, not using grub to boot 
Windows, grub works sufficiently for that already -> "Welcome"

Moving the boot files now will not fix Vista, and fixing the 
boot files now, might have to be done again depending on what it 
takes to fix Vista. That is why the priority is finding out what 
the error is that makes Vista reboot which has nothing to do with
which partition the boot files are in, Windows is designed to work 
that way. Why fix the Windows boot files first, in order to make
grub boot either Windows OS, when grub will certainly not help 
Vista finish booting, which seems to me to be the main problem.

---

### Post by caljohnsmith on 2008-12-17
> **TeXtonyx said:**
> "When Vista tries to boot, it shows the screen that says "Welcome" 
and has a background, but then my screen flashes and it restarts."

That seems to me to be the main problem, not using grub to boot 
Windows, grub works sufficiently for that already -> "Welcome"

Moving the boot files now will not fix Vista, and fixing the 
boot files now, might have to be done again depending on what it 
takes to fix Vista. That is why the priority is finding out what 
the error is that makes Vista reboot which has nothing to do with
which partition the boot files are in, Windows is designed to work 
that way. Why fix the Windows boot files first, in order to make
grub boot either Windows OS, when grub will certainly not help 
Vista finish booting, which seems to me to be the main problem.
I agree that the he first needs to fix Vista, and that is why I encouraged him to download that boot_info script so we can get a better idea of his setup and maybe what the problem is. I just wanted to warn him that running the fixmbr command that you gave will remove Grub as his boot loader, which I don't think is what he wants at this point (but I could be mistaken). I think at least one thing we need to consider is if his menu.lst uses the "mapping" lines for Vista when it shouldn't, or if it doesn't have the mapping lines when it should; that could cause Vista to not boot from Grub, even though Vista is not broken. So I think it would be a good idea to get a better picture of his setup, including his menu.lst, so we can more accurately determine whether he has a Vista problem or maybe a Grub problem. But I agree with you, the chances are his Vista might need fixing. :)

---

### Post by TeXtonyx on 2008-12-17
> **caljohnsmith said:**
>   I think at least one thing we need to consider is if his menu.lst uses the "mapping" lines for Vista when it shouldn't, or if it doesn't have the mapping lines when it should; that could cause Vista to not boot from Grub, even though Vista is not broken.  :)

Phil149 wrote:"I'm using the GRUB boot loader, but to boot into 
Vista and XP I have to go to a second menu (Vista's Bootloader, 
I think). When Vista tries to boot, it shows the screen that says 
"Welcome" and has a background, but then my screen flashes and it 
restarts."

TeX: I thought his description meant that grub has successfully
chained to the Vista bootloader. And that the Vista bootloader
runs for a few seconds before getting to the "Welcome" screen
which a grub error doesn't produce. I think when Vista reboots
at this point it means it must be an internal Vista problem and
grub is out of the picture, because if grub were wrong, the
Vista boot process which leads to the "Welcome" screen never has
a chance to happen, because the "chain" has not worked. I think
Vista *must* be broken, not that there is a good chance of it.

"Vista Won't load past welcome screen" sometimes at login screen,
is a not uncommon serious Windows error problem and its unrelated
to dual booting. By design Windows reboots when it encounters a
serious problem. Sometimes that problem is a recently installed
incompatible driver. That is why I suggested tapping F8 just
after the Windows bootloader kicks in to get to those recovery
options. One of them turns off the automatic rebooting so that
an error message can be displayed. After that, he can also try
last known good configuration from that screen. But he may not
be able to get to that screen. If not he should try Startup Repair
then the bootrec commands and then reinstall Vista. OP is most
likely to have overwrite the MBR with Vista. That means that
one will lose grub. Grub can be reinstalled. When Vista is
reinstalled it will mess up the grouping of the boot files that
you would like to see moved now, so it will have to be done again.

So that is not the most efficient approach. But is it going to
hurt to move the boot files first, No I don't think it will, so
it can be tried before the bootrec commands, but F8 should be
tried first since it has the best chance of fixing Vista besides
the last resort of reinstalling Vista, or recovering Vista from
a manufacturer recovery partition or cd. Mainly I think the
difference in priorities is caused by my being convinced, but
not absolutely certain, that this is only an internal Vista problem,
with a slight chance of fixing with Startup Repair or F8 while 
you think there is a reasonable chance that this is grub error or 
due to all the boot files being on only one Windows partition.

---

