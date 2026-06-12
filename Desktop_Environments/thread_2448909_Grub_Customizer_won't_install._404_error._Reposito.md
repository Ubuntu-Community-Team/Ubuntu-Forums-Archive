---
title: "Grub Customizer won't install. 404 error. Repository not added."
date: 2020-08-16
forum: Desktop Environments
---

### Post by Mugsy323 on 2020-08-16
Help. I need to edit my Grub Menu but every help article online tells me to install "Grub Customizer". But when I try to add it to my computer, I get the following error:

[IMG]https://i.postimg.cc/pT9zd1wk/Repository-not-found.png[/IMG]

"Error 404" is "not found". Resulting in "Repository not added", preventing me from installing the program.

I copied/pasted the text directly from the instructions (multiple sites. always the same) into the Terminal window.

Did someone move/remove the repository for "Grub Customizer"? Is there any way to install it (or another utility?)

TIA

---

### Post by CelticWarrior on 2020-08-16
That PPA supports Ubuntu up to 19.04 only.

---

### Post by Dennis N on 2020-08-16
Grub Customizer is in the Ubuntu Repository:

```
dmn@Sydney-vm:~$ apt show grub-customizer
Package: grub-customizer
Version: 5.1.0-2
Priority: optional
Section: universe/utils
Origin: Ubuntu
```

---

### Post by ActionParsnip on 2020-08-16
Are you wanting to make Windows the first option in GRUB rather than Ubuntu? If so then you just need the below:

```
 
sudo mv /etc/grub.d/30_os-prober /etc/grub.d/05_os-prober

sudo update-grub

``` 

Should put Windows at the top. The number tells GRUB the order to place the entries

---

### Post by ajgreeny on 2020-08-16
It is actually much safer, I believe, to make changes to grub manually rather than use grub-customiser; I have seen several threads here and in other forums where users have done more harm than good using it so I have always edited the appropriate files manually using all the information in the thread at [https://ubuntuforums.org/showthread.php?t=1195275](https://ubuntuforums.org/showthread.php?t=1195275) and [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If you do use GC make sure you fully understand what you're doing and how to reverse the outcome if things go wrong.

---

### Post by oldfred on 2020-08-16
Grub Customizer uses its own versions of grub with proxy in the name.
Not then sure if it has the latest updates as grub issued new versions related to the BootHole issue.

Better just to make whatever changes you want in /etc/default/grub or in 40_custom.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by Mugsy323 on 2020-08-16
Hmm. Whenever I try to "update-grub", I get the same error:

**error: failed to get canonical path of `/cow'.**

All attempts to run "efibootmanager" respond: "EFI variables are not supported on this system." (I am unable to boot from USB in UEFI Mode.)

I don't need to just make Windows the first entry, but my Grub menu is now full of redundant entries that need to be removed. (I never had all this trouble before UEFI Bios'. Nothing but headaches since.)

---

### Post by oldfred on 2020-08-16
/cow is copy on write or your live installer which cannot be updated.

You have to mount your install and then run the update to grub.

If you run Boot-Repair it may add 25_custom with lots more grub entries. Most are not required.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Mugsy323 on 2020-08-16
Unfortunately, "Boot-Repair" refuses to install either (giving me similar reasons/errors.)

I **can** however boot into my original Ubu 20.04 LTS install (I'm in it right now), where I already have both "Grub Customizer" AND "Boot Repair" installed (from before I upgraded to 20.) Unfortunately, they were installed when I was still using an old pre-UEFI machine. So while they run, they can no longer make any changes to the menu. :rolleyes:

In an attempt to regain access to those programs, I put the drive BACK in my old (pre-UEFI) computer and tried to run the apps there. But the UEFI Bios did "something" to the drive and now the programs won't even run on the old machine. :eek:

So I put the drive BACK in my new PC and now it no longer detects it as an eligible Boot drive (I must use "Boot Override" from Bios every time now. Extremely annoying.)

In summary, the programs will RUN on the new PC, but all changes are ignored. And the programs now refuse to even run on the old PC.

So I tried installing Ubu to a drive/partition that DOES boot (my M2) in order to get the Ubuntu Installer to recreate the Grub boot menu, and it did, but the new menu is full of redundant entries that can't be removed or sorted.

[[img]https://i.postimg.cc/tZLdq8bv/Screenshot-from-2020-08-16-13-15-26.png[/img]](https://postimg.cc/tZLdq8bv)

---

### Post by oldfred on 2020-08-16
Customizer is finding a lot of old kernels.
Ubuntu now only keeps two, but before it was up to you to remove the old ones.
And it seems to show older installs also.

Do not know Customizer, so cannot help on that. It uses its own modified version of grub.

---

### Post by ajgreeny on 2020-08-17
As I said previously, grub-customiser can cause more problems than it solves and that is perhaps what's occurred here.

As long as I had everything backed up and the ability to restore everything, (which of course, you do too, don't you?) I might try removing grub-customiser, reinstalling the normal grub packages for the system, taking into account BIOS vs UEFI, and then cleaning up everything, ie kernels etc, manually.

However, I am not an expert like oldfred, so don't do that just yet; wait to see fi that is a good idea or if my suggestion might lead you further into problems with grub.

---

### Post by ActionParsnip on 2020-08-17
Try:
```

sudo mv /etc/grub.d/05_os-prober /etc/grub.d/06_os-probersudo update-grub

```

---

### Post by oldfred on 2020-08-17
I agree with removing grub customizer.
You then need to do a full re-install of your version of grub.
If booting with BIOS, it is grub-pc and with UEFI, it is grub-efi-amd64.
If in your working install and not in live installer:
sudo apt install grub-efi-amd64
That will overwrite any grub settings you have changed in /etc/default/grub or in 40_custom.

If in live installer easier to use Boot-Repair and its advanced options for full re-install of grub. And then post link to summary report it also gives.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Then we will be back to standard grub and can see the details of your installs.

---

### Post by Mugsy323 on 2020-08-17
Is there a way to delete the old Grub menu and reinstall **via the LiveCD** w/o reinstalling Ubu itself? (Reminder, "Boot Repair" won't install or run on my UEFI machine.)

TIA

---

### Post by ajgreeny on 2020-08-17
Yes.
Oldfred told you how in post #13 for both BIOS and UEFI.

Another way to help clean up your grub menu is to remove old kernels, some of which I suspect have come from OS version upgrades.
Try running command ```
sudo apt -s autoremove
``` first to see what packages that will remove, and if there is nothing in the list that you know you want to keep, run it again but remove the ***-s*** (simulate) option.

That may remove the two unneeded kernels 4.13.0-37 and 5.0.0-32, assuming that the package menegement system is aware of them, but if not you may find it easiest to first install synaptic and using that search by name alone for those kernel versions; just type the numbers in the search box from top right hand search button.  It will list all packages with that version number including kernels, headers and maybe others, that you can ask synaptic to remove which will also remove them from the grub menu.

I would still recommend you remove grub-customiser from your system for all the reasons that have already been mentioned; it will allow your OS to revert to the standard grub menu without all the extraneous entries that GC has added.

---

### Post by ActionParsnip on 2020-08-17
What is the output of
```

uname -a; echo; dpkg -l | grep linux-image | grep -v extra

```
Thanks

We can then remove the old kernels and clean up

---

### Post by Mugsy323 on 2020-08-17
> **ActionParsnip said:**
> What is the output of
```

uname -a; echo; dpkg -l | grep linux-image | grep -v extra

```
Thanks

We can then remove the old kernels and clean up

ATM, I can only run the LiveCD (from a Flash drive). Fixing the MBR of my Windows' drives appears to have wiped out Grub, forcing me to reinstall it.

I just now performed the command shown in Post #13. I will reboot now to see if it created a new Grub Boot Menu.

*(FOLLOW-UP: Didn't work. A new Grub boot menu was not added. "sudo apt install grub-efi-amd64" does not specify a destination drive, so I expected it would not.)*

---

### Post by oldfred on 2020-08-17
The [I]"sudo apt install grub-efi-amd64" works from inside your install as it uses the mount of the ESP from fstab.

If using live installer you have to chroot, or use Boot-Repair.
[/I]

---

### Post by Mugsy323 on 2020-08-17
Hmm. the grub efi command refused to work. I didn't have "permission" to chroot either. :-x

SO, I tried installing/running "Boot-Repair" again. This time it worked. And despite telling me to enter some commands manually from the terminal and eventually landing on a "can't continue" message, it still worked and I have a Grub menu once again.

I can only assume whatever Windows did to fix the mbr so I could boot it once again w/o having to go thru bios (removing Grub in the process), somehow allowed Grub to be reinstalled. #-o

Thx.

---

