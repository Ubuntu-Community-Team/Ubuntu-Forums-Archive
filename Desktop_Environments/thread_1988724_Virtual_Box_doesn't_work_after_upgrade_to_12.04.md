---
title: "Virtual Box doesn't work after upgrade to 12.04"
date: 2012-05-28
forum: Desktop Environments
---

### Post by umor on 2012-05-28
Hello, 
after I have updated to Ubuntu 12.4 my virtual box started, but when I wanted to start windowsXP from there it gave me two error messages. The first one was something like "Kernel driver not installed (rc=-1908 ) ". The second one was an instruction to run '/etc/init.d/vboxdrv setup' as root to update linux headers and to install DKMS.
But running '/etc/init.d/vboxdrv setup' gave me another error telling me that it cannot locate the kernel headers (if I remember correctly). I tired to install the kernel headers, but they were not available in my distribution (as I have lerant from internet forums) as the kernel was from an older distribution.


What helped me to solve this issue: 

By running

```
uname -a
```

I found out that I was running kernel 3.0.0-12

Next, by running

```
dpkg --get-selections | grep linux-headers
```

I saw that I had newer kernal versions installed on my ubuntu 12.4 which, for some reasons, where not used.

In [this forum]("http://askubuntu.com/questions/140266/linux-headers-not-found") ([http://askubuntu.com/questions/140266/linux-headers-not-found](http://askubuntu.com/questions/140266/linux-headers-not-found), reply by Eliah Kagan), I then read to install the packages linux-image-generic-pae and linux-headers-generic-pae in order to have always the latest stable kernel and the latest stable headers for my ubuntu. In my case the first of the two, linux-image-generic-pae, was not installed. So I installed the missing one via synaptic package manager. Alternative it should be possible to install with the commands

```
sudo apt-get install linux-image-generic-pae
```
and
```
sudo apt-get install linux-headers-generic-pae
```

Because I had previously modified the menue list of the GRUB maually, I was asked if I want to stick to my old menue list of GRUB. I decided not to stick to the menue list but to use the package maintainer's default instead (I don't remember the exact wordings of this step, but it should be obvious if you also run into this dialog). I think this was the most important step of all, as I think it told GRUB not to start with kernel 3.0.0-12 but with the most recent one (please correct me if this is not correct, I am just guessing).

After re-booting, virtual box now runs without errors again. Thanks to all ubuntu users who posted in the forums which helped me to figure out how to get the virtuabl box running again.

---

