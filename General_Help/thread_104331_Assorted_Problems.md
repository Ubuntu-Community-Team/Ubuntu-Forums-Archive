---
title: "Assorted Problems"
date: 2005-12-15
forum: General Help
---

### Post by Progressive on 2005-12-15
I just downloaded Kubuntu 5.10 for my Sony VAIO FS Laptop. I dual booted it with Windows XP Home.

I am getting some video problems. Everything turns like static (as in television static) among other similar weird problems until I refresh the desktop, but then starts turning to static again.

Is that a driver problem? I am thinking it might be a booting/partitioning problem because I noticed somewhere in the static that the words "Windows Saving System Settings" were clearly visible.

A side problem is that I havent been able to figure out how to set Windows back as the default in the boot loader or change the amount of time before it bypasses the selection process. I didnt have these problems with the Mandriva boot loader, plus it looked prettier. Maybe I should revert to the old boot loader?

A third problem is that when I set it to shutdown or restart, it gets almost all the way to shutting off or restarting, but does not actually do it.

Another thing you should be aware of is that I previously had Mandriva 2005 installed on the partition. It is possible that I did not format the partition correctly. Would all these be symptoms of if I wrote Kubuntu on top of the Mandriva partion without formatting first?

---

### Post by super on 2005-12-16
i can help you with you bootloader problems. try these instructions from a similar thread:

[QUOTE=canadianwriterman]Open a Terminal window and type:

[FONT="Courier New"]sudo gedit /boot/grub/menu.lst[/FONT]
(If the text editor opens an empty file, then try [FONT="Courier New"]sudo gedit /boot/grub/menu.list[/FONT])

This will open the menu.list file in a text editor. The file may look confusing and there will be many lines with ## in front of them. You need to look for all of the boot options. They'll look like this:

[FONT="Courier New"]title Ubuntu, kernel 2.6.12-10-386
root (hd0,2)
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd /boot/initrd.img-2.6.12-10-386
savedefault
boot[/FONT]

One of the options will be for Windows. Start at the top of these boot options and count them. There should be about five options, including Ubuntu kernel boot options, memtest and Windows. It's important to note that you need to start counting at "0," not "1." So, the first boot option in the file is "0," the next is "1," etc. You'll find that Windows will be at the bottom of the list, so it should be maybe option "4" or "5."

Now, find a line near the top of the file that says "default." The standard default is usually option "0." Change the "0" to the number that represents your Windows OS.

Save the file and close it. Now, you should see Windows highlighted as the default when you boot next time. If not, just note what did get set as the default and go back in and re-edit menu-list to get the correct one.

Hope that helps![/QUOTE]

---

### Post by towsonu2003 on 2005-12-16
[QUOTE=Progressive]
A third problem is that when I set it to shutdown or restart, it gets almost all the way to shutting off or restarting, but does not actually do it.
[/QUOTE]
take a look at this: [http://ubuntuforums.org/showthread.php?t=75314&page=2&highlight=vaio](http://ubuntuforums.org/showthread.php?t=75314&page=2&highlight=vaio)
In the meantime, adding reboot=h to grub menu line seems to work for some people.
[quote=Progressive]I am getting some video problems. Everything turns like static (as in television static) among other similar weird problems until I refresh the desktop, but then starts turning to static again[/code]
This looks like a problem with vaio? 
[http://ubuntuforums.org/showthread.php?t=104247&highlight=vaio](http://ubuntuforums.org/showthread.php?t=104247&highlight=vaio) you may want to do a search on the forums...

////edit////
some people will not like double posting...
[http://ubuntuforums.org/showthread.php?t=104337&highlight=vaio](http://ubuntuforums.org/showthread.php?t=104337&highlight=vaio)
[http://ubuntuforums.org/showthread.php?t=104322&highlight=vaio](http://ubuntuforums.org/showthread.php?t=104322&highlight=vaio)

---

