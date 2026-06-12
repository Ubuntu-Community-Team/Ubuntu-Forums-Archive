---
title: "DELL Precision T1600 Won't Boot:"
date: 2011-07-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nbotticelli on 2011-07-18
I have recently installed Ubuntu 11.04 x64 on a new DELL Precision T1600 using the alternate install disc.

The install went smoothly and I can select which OS to boot into from GRUB but after choosing Ubuntu the screen shows up as partly purple but doesn't showing the loading screen and then after half a minute the screen itself turns off as if it has lost signal. Ubuntu itself seems to be booting up fine in the background but the screen itself doesn't show up.

I am thinking there is something funny going on with how Ubuntu is interacting with the video card.

The video card is an NVIDIA NVS 300 which has a DVI splitter cable coming out the rear which goes to a dual monitor set up. I am thinking maybe there is something funny because of the y-cable? Unfortunately I must use this cable and cannot plug a monitor cable directly into the video card to test to see if that is the issue.

Has anyone else dealt with this before? Is there another way that I could possibly go in and change the driver being used?

I also cannot boot into a LiveCD either.

Thank you!

---

### Post by hlynur on 2012-01-13
I have some of these machines with the same configuration i.e. the NVS 300 card which has given me some headache. My problem is ubuntu gets kernel panic as soon as kdm loads. This can be resolved by installing a new nvidia driver downloaded from nvidia.com.

When you install that driver you need to purge your ubuntu nvidia drivers and you need to blacklist the opensource nouveau driver 

so sth like 

dpkg -P nvidia-current nvidia-glx-185 nvidia-settings 

add 
blacklist nouveau
to /etc/modprobe.d/blacklist.conf 

update your initramfs 
update-initramfs -u

install linux-headers (needed to compile the new nvidia driver)

Then reboot to get rid of the already loaded drivers and install the nvidia driver from nvidia.com 


I still have another issue on these machines that they don't reboot correctly. I.e. when you type reboot in the shell it just starts the reboot process and then hangs !!

---

### Post by kula85 on 2012-01-25
same for me

> **hlynur said:**
> 

I still have another issue on these machines that they don't reboot correctly. I.e. when you type reboot in the shell it just starts the reboot process and then hangs !!

---

### Post by doug901 on 2012-03-10
Same problem here, and it is in both 11.10 and 12.04 beta 1.  I thought NVS 300 was supported by Nouveau, but not so much.

---

