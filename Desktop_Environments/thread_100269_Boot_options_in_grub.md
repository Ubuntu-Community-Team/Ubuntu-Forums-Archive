---
title: "Boot options in grub"
date: 2005-12-07
forum: Desktop Environments
---

### Post by Nolite on 2005-12-07
Hi all,
my first post in the ubuntu forums *yay* :)

Anyaways, I'd wan't to start with saying I'm a very new Linux/ubuntu user, just recently created a partition on my Windows disc to try it out and learn stuff as I go.
The past days I've searched the forums in every obstacles I've encountered this far, but at this problem I'm clueless!

I'm using grub (I think that it's name) to choose which OS to boot. Linux is the default in grub but I want it to be WinXP atm. This is because I feel I still have to learn a whole lot before Linux get more advantages than Windows for me, plus I'm a hardcore gamer and Linux dosen't (or isn't) yet fully supported on this part of PC usage afaik.

Question: how do I change the boot order in grub, making WindowsXP the default booting OS?

Thanks in advance, 
Nolite.

---

### Post by canadianwriterman on 2005-12-07
Welcome to the Ubuntu forums Nolite. Changing the default boot OS is fairly simple. Open a Terminal window and type:

**sudo gedit /boot/grub/menu.list**

This will open the menu.list file in a text editor. The file may look confusing and there will be many lines with ## in front of them. You need to look for all of the boot options. They'll look like this:

[B]title Ubuntu, kernel 2.6.12-10-386 
root (hd0,2)
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd /boot/initrd.img-2.6.12-10-386
savedefault
boot[/B]

One of the options will be for Windows. Start at the top of these boot options and count them. There should be about five options, including Ubuntu kernel boot options, memtest and Windows. It's important to note that you need to start counting at "0," not "1." So, the first boot option in the file is "0," the next is "1," etc. You'll find that Windows will be at the bottom of the list, so it should be maybe option "4" or "5."

Now, find a line near the top of the file that says "default." The standard default is usually option "0." Change the "0" to the number that represents your Windows OS.

Save the file and close it. Now, you should see Windows highlighted as the default when you boot next time. If not, just note what did get set as the default and go back in and re-edit menu-list to get the correct one.

Hope that helps!

---

### Post by schdefan on 2005-12-07
if you also want to change the order in the grub menu and winXP should be your first entry change /boot/grub/menu.lst

For example:
> ## ## End Default Options ##
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386


then default for Windows is 0


schdefan

---

### Post by canadianwriterman on 2005-12-07
[QUOTE=schdefan]if you also want to change the order in the grub menu and winXP should be your first entry change /boot/grub/menu.lst

For example:



then default for Windows is 0


schdefan[/QUOTE]

That is always an option. However, the Windows OS boot option may get removed if there is an update to the Linux kernel. The Windows OS is automatically placed in menu.list below the line:

### END DEBIAN AUTOMAGIC KERNELS LIST

If you copy and paste it above that line, I think you'll find that you'll lose it each time the kernel is upgraded. At least, I found that was a problem in the prerelease development of Breezy and I had to keep adding it back manually.

---

### Post by Ted D. on 2005-12-07
I am a noob as well. I am trying to make the same change. Trouble is I can't find the "save in the terminal window. Advice please.
Ted D.

---

### Post by canadianwriterman on 2005-12-07
[QUOTE=Ted D.]I am a noob as well. I am trying to make the same change. Trouble is I can't find the "save in the terminal window. Advice please.
Ted D.[/QUOTE]

The save is not done in the Terminal window. When you type **sudo gedit**, a text editor will open and show you the file contents. The save is done in the text editor. There should be a save button or, at least, a **file > save **option.

---

### Post by canadianwriterman on 2005-12-07
While you guys are editing menu.list, there are a couple of other nifty things you can change. Where it says "**timeout**," the default is "10." That's how many seconds the system waits before automatically booting the OS that has been set as a default. You can change the "10" to something longer of you want. I have mine set to "30" seconds.

Also, you can remove the ## from in front of the line **color cyan/blue white/blue**. That will give you a nicer looking boot option screen.

**EDIT: A final word of caution. Don't fool around with other lines in menu.list. If you make changes to any other boot option, you might make your system unbootable.**

---

### Post by PtS on 2005-12-07
If there's somebody having nothing to modify in /boot/grub/menu.list it propably doesn't excist (it happened to me). Try open /boot/grub/menu.lst instead.

---

### Post by Nolite on 2005-12-07
Wow! Thanks a bunch canadianwriterman! I'm kinda overwhelmed about the fact how helpfull the Linux/Ubuntu community really seems to be! As PtS noted, I had to open menu.lst, but I did solve that part on my own though! ;)

---

### Post by thunderchase on 2005-12-07
Heh, that's very useful info. I have always wanted to set the windows line as default, but I've never tought of it to ask on any forum :) ..

---

### Post by Ted D. on 2005-12-07
Thanks! It worked. I will get the hang of this yet. Ted D

---

### Post by schdefan on 2005-12-08
canadianwriterman: Your are right with the kernel upgrade. So it is not a good idea to put windows in the first line.

And it is ALWAYS a good idea to make a backup of menu.lst before editing.

schdefan

---

