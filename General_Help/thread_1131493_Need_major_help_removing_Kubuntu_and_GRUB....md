---
title: "Need major help removing Kubuntu and GRUB..."
date: 2009-04-20
forum: General Help
---

### Post by teamsupreme on 2009-04-20
Alright...I dual booted Kubuntu with Vista today, and I wanted to get rid of Kubuntu, so I followed some tutorial, and came up with an Error 13...so I reinstalled it. Then I decided to format Vista, and that gave me an Error 22...so I reinstalled Kubuntu...for no reason...and now I'm stuck with and Error 22. I have no boot/recovery disc for Vista, and I need a good way to get rid of GRUB once and for all...Help please!

---

### Post by KhurramM on 2009-04-20
You seem to have no data to save, ... SO simply format the whole disk and re-install win.

On the other way around try out the super grub disk. It will recover windows from grub.

Have a look here:
[http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows#Windows_Vista_.28with_easybcd_help.29](http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows#Windows_Vista_.28with_easybcd_help.29)

and
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Hope I clear my self.

Good Luck!

---

### Post by teamsupreme on 2009-04-21
Ok I may sound stupid but...how to I format the whole disk? Also, if I format the disk, how will I reinstall Vista? The Laptop never came with a recovery cd...

---

### Post by James_Lochhead on 2009-04-21
Without a recovery disk it is impossible to restore the Windows boot loader. If you do not have one you can borrow one from a friend (this is allowed as long as you don't re-install) or contact the computer manufacturer to obtain one. You are entitled to ask the manufacturer for a disk (usually) if your computer did not come with one. 

There is no need to get rid of Vista in this situation.

To remove Kubuntu just use a live cd and the program called GParted to remove the Kubuntu partition.

---

### Post by teamsupreme on 2009-04-21
Hmmm...well...I will contact the company then, but for the time being, I want to install Ubuntu on it for now. How can I install it while reformatting it?

---

### Post by hyperdude111 on 2009-04-21
To install ubuntu on your whole hard disk, just download the .iso, burn it and during install select "use entire disk"

A whole disk format just remove all current partitions and replace the al with 1 partition the size of your entire disk. If you had any data on your vista partition it is GONE because you formated the vista partition it is the same for your kubuntu.

Once you get your vista cd you will need to re-format again just use the tools provided on the cd. Remember when you format you will delete all your data.

---

### Post by teamsupreme on 2009-04-21
Yeah. Thankfully I backed up my files a while back. I may dual boot Vista and Ubuntu someday...Time to download Ubuntu!

---

