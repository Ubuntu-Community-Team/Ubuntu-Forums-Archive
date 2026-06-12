---
title: "dpkg was interrupted, you must manually run 'dpkg --configure -a'..."
date: 2009-04-22
forum: General Help
---

### Post by alimahmoudy on 2009-04-22
hello, i've recently run an update. But when i wanted to run synaptic package manager, i got the following error:

[B]dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

And when i ran ```
sudo dpkg --configure -a

```
i got the following message:

[B]Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.29.1-ultimate
Cannot find /lib/modules/2.6.29.1-ultimate
update-initramfs: failed for /boot/initrd.img-2.6.29.1-ultimate
dpkg: subprocess post-installation script returned error exit status 1[/B]

I've recently installed and compiled the 2.6.29.1 kernel, but i removed it later via synaptic.

The problem only appeared after i did the update. any help ? thanks alot.

---

### Post by amauk on 2009-04-22
well, it's failing to process 2.6.29
which you say you've removed?

Are there any mentions of .29 in /boot/grub/menu.lst?

---

### Post by alimahmoudy on 2009-04-22
Thanks for your reply. no there isn't any mention.

---

### Post by orlox on 2009-04-22
Try this:

```

cd /var/lib/dpkg/info
sudo mv initramfs-tools.postinst initramfs-tools.postinst.back
sudo dpkg --configure -a
sudo mv initramfs-tools.postinst.back initramfs-tools.postinst

```

I just mentioned this on another post, reccommend you to see the discussion there:

[http://ubuntuforums.org/showthread.php?p=7122573#post7122573](http://ubuntuforums.org/showthread.php?p=7122573#post7122573)

---

### Post by alimahmoudy on 2009-04-22
Thanks alot man. Sorry i didn't see that in the other post, i thought my problem was different than the one in there.
Anyways, i've been trying to solve this for 4 hours, finally i fixed it, using the following commands:

[B]sudo ln -s /boot/initrd.img-2.6.24-23-generic /boot/initrd.img
sudo update-initramfs -u[/B]

And finally

**sudo dpkg --configure -a**

**My kernel version is 2.6.24-23**

---

### Post by sdunnrocket9 on 2009-05-01
Thanks Orlox - that did it for me.

---

