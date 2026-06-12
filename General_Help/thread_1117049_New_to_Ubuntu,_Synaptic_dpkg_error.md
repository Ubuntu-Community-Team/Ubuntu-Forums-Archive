---
title: "New to Ubuntu, Synaptic dpkg error"
date: 2009-04-05
forum: General Help
---

### Post by poopfly on 2009-04-05
Hi,  I am a fairly new linux user and I'm having a problem with synaptic.  I have used the search function to no avail, and I have become frustrated that I can't solve this problem.

A few months ago my wife cancelled the installation of some update (I have no idea which) in the middle of the update.  Since then I have gotten 

[COLOR="Red"]"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
[/COLOR]
when trying to run synaptic.  

Typing the command in the terminal yields:

[COLOR="Red"]p@poopfly:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-ubuntu-modules-2.6.24-23-generic (2.6.24-23.36) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-23-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-23-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-23-generic; however:
  Package linux-ubuntu-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.23.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-23-generic
dpkg: subprocess post-installation script returned error exit status 1
p@poopfly:~$ 
[/COLOR]

Please help!

---

### Post by coffeecat on 2009-04-05
This looks to be a problem:

> **poopfly said:**
> [COLOR=Red]gzip: stdout: No space left on device[/COLOR]

Go to System -> Administration -> System Monitor. Click on the File Systems tab. What do the Total, Free, Available and Used columns in the line Directory = / say?

---

### Post by poopfly on 2009-04-05
I tried to attach a screenshot.  Thanks for helping.

---

### Post by coffeecat on 2009-04-05
Yes, there's your problem. It wasn't the root (/) partition that was the problem, it was the /boot partition. And thanks for posting a screenshot rather than just the line I asked for. I didn't stop to think you might have a separate /boot partition. Out of interest, why do you have a separate /boot partition?

Anyway, the /boot partition is completely full and when the package manager attempts to install the initrd files into /boot, it can't. Hence the error.

This is recoverable by moving all the contents of the /boot partition into the /boot folder of your root partition, but it will also require an edit of /etc/fstab and /boot/grub/menu.lst to work. **And** a reinstall of grub stage 1 to the mbr to get it to go to sda3 rather than sda1. How much experience of Linux do you have?

---

### Post by poopfly on 2009-04-05
Hmm, this sounds like it might be painful.  I have used linux for about 6 months.  Moving and editing files won't be a problem for me.  Screwing with GRUB might be tricky.

I have a separate /boot partition upon someone's advice.

What do you recommend I do first?

---

### Post by coffeecat on 2009-04-05
Actually, I've got a better idea. 80 odd MB for a /boot partition should be enough. You've got some old kernels in there which can be removed - freeing up room. Have a look in /boot. There will be several versions of vmlinuz-2.6*. How many have you got? While you're looking, I'll check in Synaptic to see which packages you need to uninstall.

---

### Post by poopfly on 2009-04-05
Lets try a screenshot again.  I've got 5 versions of vmlinuz taking a total of 9MB.  Looks like I'm using 71MB for initrd.img, whatever that is.

---

### Post by coffeecat on 2009-04-05
Don't worry, the obsolete initrd files will be removed when we take out the unwanted kernels (along with abi, config and system map files). We'll remove the two older versions, which are *-2.6.24-16-generic, and *-19-generic.

Go to Synaptic and mark three packages for each of those two versions for complete removal - 6 packages altogether. That's -2.6.24-16-generic, and -2.6.4-19-generic, for linux-image-*, linux-headers-* and linux-restricted-modules-*.

That's: linux-image-2.6.24-16-generic, and so on. Don't mark anything else. If you mark linux-image-*, it'll automatically mark the corresponding linux-restricted-modules-*.

**Don't mark any later versions, 21 and above, just yet.**

Apply that, and then you should be able to run that dpkg --configure command and complete the installation of the latest kernel. If that all goes well, you may as well go back and remove the *-21-* kernel. You only need two versions: the latest to boot into and the immediately previous one (so long as it worked OK) as a fallback.

---

### Post by poopfly on 2009-04-05
Actually I can't run synaptic.  Is there another acceptable way to remove these packages?

---

### Post by coffeecat on 2009-04-05
Ah yes, of course. Sorry, I was forgetting the dpkg error. :oops:

Well- this is not ideal, but the only way I can think of is to manually delete the files to make room. That may cause problems with dpkg later, but I hope not insuperable ones. I can't guarantee that this will not cause more problems but this is what I would do in your situation. I would delete all the files belonging to the oldest kernel only. Try this. Open a terminal, and:

```
ls /boot/*2.6.24-16*
```Look at the output. Is it showing only 6 files related to the 2.6.24-16 kernel? If so, then:

```
sudo rm /boot/*2.6.24-16*
```(I'm assuming here that your /boot partition is mounted to the /boot folder in your / partition. I can't see how it could be any other way.)

That should remove the six files. Now try the dpkg command.

---

### Post by poopfly on 2009-04-05
Excellent!  I had just the six files and removed them as you suggested.  Retried 'dpkg --configure -a' and got no errors.  Then I opened synaptic to see if it worked and success!

Do you recommend I still mark some other packages for removal at this time?

---

### Post by coffeecat on 2009-04-05
Yes I think so. Follow my earlier post for both the 16 and 19 kernels. The reason being is that Synaptic/dpkg still thinks the 16 kernel is in situ. That's why I was concerned about problems with dpkg. You're about to find out. :p Hopefully, there will no error messages, or just a bit of grumbling about missing files. By uninstalling the 16 kernel this way, you'll also clean up menu.lst of unnecessary entries. And you need to remove the 19 kernel to make extra room for the future. I would take out the 21 kernel too, but that's up to you.

Good luck, and [here's an interesting pros and cons for separate boot partitions]("http://forums.gentoo.org/viewtopic-t-220302.html"). A bit out of date, but food for thought.

---

### Post by poopfly on 2009-04-05
Just wanted to say for anyone else who may have similar problems that the steps suggested by Coffeecat have solved my problem.  I can run synaptic again, and download/install updates and other programs.

Coffeecat, thank you very much for your help.

---

### Post by coffeecat on 2009-04-05
You're very welcome! And a belated welcome to the forum too.

---

### Post by peterdvlhick on 2009-04-12
I have the same dpkg error but no old kernels.

if you have a look at the screenshot  you shoudl understand where im coming from.

also i dont think i have a partition it says i have 40 gb free.

Please Help.

---

### Post by coffeecat on 2009-04-12
**peterdvlhick**, you are probably getting the same dpkg error which is not uncommon, but probably for a completely different underlying reason. In fact you do have an old kernel. Anyway, go to Applications > Accessories > Terminal. In the terminal, type:

```
sudo dpkg --configure -a
```followed by return. You will be prompted for your password. Type it in followed by return. You will not see it being typed in - that  is a security measure. 

Hopefully, that will fix your problem.

You would have been better starting a new thread so that if yours turns out to be a more complicated issue, then the discussion won't get muddled with the unusual situation of the OP. I will ask a moderator to move this for you.

**Edit: peterdvlhick**, forgot to add - post the whole of the error message you're getting before running 'sudo dpkg --configure -a'.

---

### Post by peterdvlhick on 2009-04-12
Thankyou so very much. Sorry for my new-to-ubuntu incompetance.

It worked a charm.

Dont worry about moving it.

Thanks again.

Pete

---

### Post by coffeecat on 2009-04-12
No problem. Glad it worked.

Welcome to the forum, and...

Enjoy Ubuntu.

:wink:

---

