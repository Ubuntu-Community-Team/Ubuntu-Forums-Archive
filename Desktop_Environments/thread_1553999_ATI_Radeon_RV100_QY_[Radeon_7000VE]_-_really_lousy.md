---
title: "ATI Radeon RV100 QY [Radeon 7000/VE] - really lousy display (Lucid)"
date: 2010-08-16
forum: Desktop Environments
---

### Post by wayover13 on 2010-08-16
I recently stuck an old ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] in my machine. The machine runs my own personalized ubuntu installation, built up from scratch: no gnome or any of the fluff that comes with the standard ubuntu.

I've got a display, so it's not as if I have no gui. And it displays at the selected resolution (1280x1024). But it looks like absolute crap and makes me sick staring into it for any length of time. It's got thousands of horizontal lines going across the screen and seem to shift back and forth rapidly. It's really annoying and becoming intolerable.

I've tried looking up tips on how to get the display to look better, but have so far come up empty. Most of what I'm finding seems centered on getting 3D or some special effects working. Hey, I don't give a hoot about any 3D. I have no interest in compiz and all those bells and whistles and I don't do any gaming. I just want a regular old display I can look at for an extended period without getting a headache.

It could be that, since I built this system up from scratch, that I'm missing some xorg element. But I'm not sure what it could be. It was displaying fine using the old card, though I was using the vesa driver with that one.

So, what can I do to fix this display? It actually looks a bit like a refresh rate issue. But I've checked several times and the refresh rate values for my monitor are listed correctly in xorg.conf. I'm using the radeon driver, by the way.

Input will be appreciated.

Thanks,
James

---

### Post by clhsharky on 2010-08-16
wayover13

R100 & r200 are having problems with KMS(kernel module),
Turning KMS off and going back to the old UMS(user space) works for many.
Use nomodeset in grub boot line or radeon.modeset=0.
```
sudo gedit /etc/default/grub
```
add (radeon.modeset=0) between "" to (GRUB_CMDLINE_LINUX_DEFAULT="quiet splash")
like so
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0"
```
sudo update-grub
sudo update-initramfs -u
```
restart 

update-initramfs was to make sure modules are registered.

You can also remove(quiet splash)to see startup.

Sharky

---

### Post by wayover13 on 2010-08-16
Thanks for your reply, clhsharky. I didn't get to test how your suggested fix works because I wanted first to try out something simpler: starting the gui xorg.conf-less. Though my current xorg.conf looks fine to my eye I was not fully certain that there might not be some error in it. And it seemed that letting the system start the gui using settings it would detect might just resolve the issue. So I moved xorg.conf to xorg.conf-old and restarted the gui. And, voila, a sane display. So the problem seems to have been solved by letting the system detect the hardware and by not trying to get it to use my modified xorg.conf.

James

---

### Post by ActionParsnip on 2011-02-08
Remember to run:

gksudo gedit /etc/default/grub
and NOT
sudo gedit /etc/default/grub

sudo is NOT to be used with GUI apps as sudo does not setup the X environment and can cause ~/.ICEAuthority to be owned by root which will cause issues. It is easier to avoid this rather than have to re-chown a borked file due to bad system use.

---

### Post by 3Wize on 2011-11-13
> 
sudo vim /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0"
```sudo update-grub
sudo update-initramfs -u

restart 
This solution works well on my Debian stable (Squeeze), kernel 2.6.32-5-amd64
for the ATI Radeon RV100 QY [Radeon 7000/VE] (PCI slot) used as secondary graphic card.

---

