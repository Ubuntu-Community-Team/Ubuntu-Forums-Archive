---
title: "after installing Vista on another  partition, the boot menu is gone"
date: 2009-05-01
forum: General Help
---

### Post by liketofindoutwhy on 2009-05-01
I have Vista and installed Ubuntu 9.04 both as a separate partition and then also inside of Vista.

After that I reinstalled Vista on another partition and then the Ubuntu boot menu is gone.  Is there a way to get it back?  thanks.

---

### Post by ebanlague on 2009-05-01
Are you completely sure you didn't write over the Ubuntu partition?
Boot into Windows and make sure that the Ubuntu partition is there and has data stored on it.
In Windows, type into the search bar diskmgmt.msc and that will bring up all the partitions and have.

If during the Vista installation you didn't specify the partition you want, I do believe that it by default may have written over your Ubuntu one.

---

### Post by egalvan on 2009-05-01
Installing MS Windows overwrites the MBR,
which is where the boot-loader lives...

So GRUB is now gone from the MBR....

but not from the rest of the install,
unless  you accidently used the Ubuntu partition(s).

PartedMagic LiveCD is a good "rescue"-type distro to have...
it will let you check any partition types...

[http://partedmagic.com/](http://partedmagic.com/)

As for re-loading GRUB,
meifera and caljohnsmith are the masters...

do a search for their posts...

I am too newbie on this to really help more than this...

ErnestG

---

### Post by caljohnsmith on 2009-05-01
I think it would help to first get a clearer picture of your setup related to booting, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup, and most likely it will be a simple matter to make Ubuntu a boot option again.

John

---

### Post by liketofindoutwhy on 2009-05-02
thanks,  is there a way to install Vista on a new partition without destroying the MBR ?

---

### Post by caljohnsmith on 2009-05-02
> **liketofindoutwhy said:**
> thanks,  is there a way to install Vista on a new partition without destroying the MBR ?
Unfortunately no, Vista will always overwrite the MBR with Windows boot code, but it is usually a really easy matter to reinstall Grub to the MBR afterwards. If you would like help doing that, please post the results of the Boot Info Script, and I can give you specific instructions. 

John

---

