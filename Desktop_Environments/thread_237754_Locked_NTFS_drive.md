---
title: "Locked NTFS drive"
date: 2006-08-16
forum: Desktop Environments
---

### Post by biaz on 2006-08-16
Hi all,

Two days ago my laptop crashed while I was using Windows XP Professional (SP2). I wasn't doing anything special in particular (installing Spyware Doctor). After I pushed the reboot button the system halted right after the specification screen, stating that some files in the /WINDOWS/SYSTEM32/... folder couldn't be loaded nor found. Another guideline in that errormessage said I should insert my Windows XP Pro cd and run the repair tool. So that's what I did, although when the 'repair' tool was loading I received a blue error screen saying that something was wrong with 'bad_pool_caller.'

After some googling I found out that this problem might have occured because of a failed ram memory stick. I ran two memory tests but there were no errors detected at the end of both tests. I decided to run a Live CD from Ubuntu to, at least, recover some files which are important to me. 

The following problem occurs: I can boot into the Ubuntu environment and I can browse through the folders of the Windows system using the root account. However, I cannot recover any files since the NTFS formatted HD is locked. How can I unlock this NTFS drive in order to recover my files? I receive a 'Permission denied' message when I try to access the NTFS drive with an account other than root.

I hope someone can help me. If you need more information please ask for it.

*edit: An attempt to install Ubuntu using the remaining free space failed too.

Thanks in advance,
B

---

### Post by PriceChild on 2006-08-16
I don't see how you're using a root account on the live cd?

I take it you're mounting the drive inside system>admin>disks to a random folder?

Pricey

---

### Post by biaz on 2006-08-16
I used the following procedure to mount the hd:
- Appointed a pw to the root account and logged in
- I made a folder in the /mnt dir, called 'test'
- Further I used this command 'mount /dev/hda1 /mnt/test'

I have only one hd.

---

### Post by PriceChild on 2006-08-16
On running the live cd... you automatically have root permissions on the fake drive it creates itself, you also get full permissions on any drives you mount.

I advise you reboot the pc to the cd, then start again, not bothering to log in as root etc.

(You haven't installed from the live cd and are running there now have you?)

---

### Post by biaz on 2006-08-16
I have tried it the way you suggested, but I receive the same message: 'The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "test".'

Regarding the install, no I haven't.

---

### Post by biaz on 2006-08-17
can someone please help me?

---

