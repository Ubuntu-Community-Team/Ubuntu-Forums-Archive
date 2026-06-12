---
title: "Ubuntu 10.04 boot problem"
date: 2010-12-22
forum: Desktop Environments
---

### Post by NorlanBustillo on 2010-12-22
Hi, i was downloading a torrent file when i noticed it was at 99.40% and ten minutes later it was 99.24%... so i started doubting... then it increased and decreased again. I clicked the shutdown botton and it show that a restarting was required, so i restarted it.

When i restarted it and selected ubuntu (for i have installed it via wubi) it appeared that ¨loadfont¨ wasn´t found...
i restarted the pc and when i selected ubuntu, the options of booting (or something like that) should have appeared, but no, it just restarted my pc... now i can´t access ubuntu! and the torrent took my 2 weeks!!

Any Help??!!??!!

---

### Post by bcbc on 2010-12-23
There are problems with wubi installs due to a recent grub update. Nothing to do with torrent. See the wubi megathread [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) Problem #2, Solution #1.

Let me know if you need more help.

---

### Post by theasprint on 2010-12-23
Hi,

Just like *bcbc *said, problems are caused because there is a bug for a grub update in Wubi.

But if you are downloading a torrent file, nothing should happen.
For the increasing and decreasing part, I may guess that it is downloading in small parts or redownloading something. That would most unlikely cause a problem. (But you can take disk corruption into consideration or suspicion)

To give an overview of what's going on in your PC now, go to boot from a LiveCD.
Try Ubuntu without installing and go to the bootinfoscript link in my signature.
Follow the instructions and post the results (results.txt) here.

Help will arrive soon as long as you do that.

---

### Post by NorlanBustillo on 2010-12-23
> **bcbc said:**
> There are problems with wubi installs due to a recent grub update. Nothing to do with torrent. See the wubi megathread [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) Problem #2, Solution #1.

Let me know if you need more help.

> **theasprint said:**
> Hi,

Just like *bcbc *said, problems are caused because there is a bug for a grub update in Wubi.

But if you are downloading a torrent file, nothing should happen.
For the increasing and decreasing part, I may guess that it is downloading in small parts or redownloading something. That would most unlikely cause a problem. (But you can take disk corruption into consideration or suspicion)

To give an overview of what's going on in your PC now, go to boot from a LiveCD.
Try Ubuntu without installing and go to the bootinfoscript link in my signature.
Follow the instructions and post the results (results.txt) here.

Help will arrive soon as long as you do that.

thanks for the help, but both mention a LiveCD... which i don´t have... what can i do if i don´t have it?? :(

---

### Post by theasprint on 2010-12-23
Hi,

For a LiveCD, you can download the .iso file from the Ubuntu website:
[http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download")

After downloading the .iso file, burn it into a DVD. (Preferable DVD-RW)
And there you have a LiveCD.

*Note do not download the Alternate version, get the normal version.

---

### Post by NorlanBustillo on 2010-12-23
> **theasprint said:**
> Hi,

For a LiveCD, you can download the .iso file from the Ubuntu website:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

After downloading the .iso file, burn it into a DVD. (Preferable DVD-RW)
And there you have a LiveCD.

*Note do not download the Alternate version, get the normal version.
The iso is too large?

---

### Post by amsterdamharu on 2010-12-23
You could try to download tiny core Linux, that is only 10MB and then try the bootinfo script. Tinycore has a desktop but it's not so easy to work with. 

Either burn it on a cd or use a program called unetbootin in Windows to put it on a usb (should be non destructive to the data on it but if the data is important don't take any risks).

Install sea monkey on tiny core after you boot and go to this thread, then run the bootscript and post it here.

I am sure one of us can alter the syslinux to boot your Ubuntu and then re install grub.

---

### Post by theasprint on 2010-12-23
Hi,

You mean that the file is very big?
Average Ubuntu .iso file should be about 600Mb - 700Mb.

I understand it may take a long time for you to download. Perhaps doing it overnight?

But seriously, you will need to download the .iso file.
If you've used the Wubi install, you would also have to wait about the same amount of time for the .iso file to be downloaded while installing.

---

### Post by NorlanBustillo on 2010-12-23
> **theasprint said:**
> Hi,

You mean that the file is very big?
Average Ubuntu .iso file should be about 600Mb - 700Mb.

I understand it may take a long time for you to download. Perhaps doing it overnight?

But seriously, you will need to download the .iso file.
If you've used the Wubi install, you would also have to wait about the same amount of time for the .iso file to be downloaded while installing.
693 Mb
It´s 10:00 am! when i installed wubi it was at 9-10 pm!
this file says it will take me 12 hours... i really hate my slow internet connection...
thanks for the help :D:D

---

### Post by NorlanBustillo on 2010-12-23
> **amsterdamharu said:**
> You could try to download tiny core Linux, that is only 10MB and then try the bootinfo script. Tinycore has a desktop but it's not so easy to work with. 

Either burn it on a cd or use a program called unetbootin in Windows to put it on a usb (should be non destructive to the data on it but if the data is important don't take any risks).

Install sea monkey on tiny core after you boot and go to this thread, then run the bootscript and post it here.

I am sure one of us can alter the syslinux to boot your Ubuntu and then re install grub.
i don´t really care about the OS, but for the information... i have used ubuntu for about 2 months as my everyday OS so all my stuff is there!

---

### Post by amsterdamharu on 2010-12-23
So if you want to get it going again booting in Windows won't help you out on fixing your Ubuntu problem, you need to boot a Linux kernel. You say that the Ubuntu ISO is too big (and it is a bit) so in your case you can just download tinycore, not to use as your new OS but to fix your current problem.

PS your current problem now is that we can't really help you without the output of bootinfo script or at least some commands that need to be executed in Lunux.

---

### Post by amsterdamharu on 2010-12-23
Tinycore can be found here:
[http://distro.ibiblio.org/pub/linux/distributions/tinycorelinux/3.x/release/tinycore-current.iso](http://distro.ibiblio.org/pub/linux/distributions/tinycorelinux/3.x/release/tinycore-current.iso)
Help and info:
[http://tinycorelinux.com/welcome.html](http://tinycorelinux.com/welcome.html)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Download on Windows to stick the tinycore on USB and start your computer with it. Then you can try to run the bootinfoscript in tinycore. If that doesn't work you can execute some commands that will give us some info on what your harddisk looks like.

---

### Post by NorlanBustillo on 2010-12-23
> **theasprint said:**
> Hi,

You mean that the file is very big?
Average Ubuntu .iso file should be about 600Mb - 700Mb.

I understand it may take a long time for you to download. Perhaps doing it overnight?

But seriously, you will need to download the .iso file.
If you've used the Wubi install, you would also have to wait about the same amount of time for the .iso file to be downloaded while installing.
Question...i have the 10.04 but i´m downloading the 10.10...will that also work? will i lose my files for doing so?

---

### Post by bcbc on 2010-12-23
> **NorlanBustillo said:**
> Question...i have the 10.04 but i´m downloading the 10.10...will that also work? will i lose my files for doing so?

10.10 will be fine. you're only going to be using it as a "Live CD". Just don't uninstall/reinstall wubi or you will lose everything.

On that wubi megathread there's a link to a tool ext2read that can run in windows pull off important data from your root.disk. You might consider this if you're concerned.

---

### Post by NorlanBustillo on 2010-12-23
> **amsterdamharu said:**
> Tinycore can be found here:
[http://distro.ibiblio.org/pub/linux/distributions/tinycorelinux/3.x/release/tinycore-current.iso](http://distro.ibiblio.org/pub/linux/distributions/tinycorelinux/3.x/release/tinycore-current.iso)
Help and info:
[http://tinycorelinux.com/welcome.html](http://tinycorelinux.com/welcome.html)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Download on Windows to stick the tinycore on USB and start your computer with it. Then you can try to run the bootinfoscript in tinycore. If that doesn't work you can execute some commands that will give us some info on what your harddisk looks like.
thanks... i finished downloading the file and im going to try the dvd

---

### Post by bcbc on 2010-12-23
You can use a CD as well. I sometimes use RW but they tend to be less reliable. Burn it on the slowest speed.
You can also use a USB

Ubuntu.com has step by step instructions for each: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) (Step 2, click on CD or USB stick, then click on Show me how)

---

### Post by NorlanBustillo on 2010-12-23
> **theasprint said:**
> Hi,

Just like *bcbc *said, problems are caused because there is a bug for a grub update in Wubi.

But if you are downloading a torrent file, nothing should happen.
For the increasing and decreasing part, I may guess that it is downloading in small parts or redownloading something. That would most unlikely cause a problem. (But you can take disk corruption into consideration or suspicion)

To give an overview of what's going on in your PC now, go to boot from a LiveCD.
Try Ubuntu without installing and go to the bootinfoscript link in my signature.
Follow the instructions and post the results (results.txt) here.

Help will arrive soon as long as you do that.
Here is the result.txt
[http://www.mediafire.com/file/r3xfnxdj6m18ssy/RESULTS.txt](http://www.mediafire.com/file/r3xfnxdj6m18ssy/RESULTS.txt)

---

### Post by NorlanBustillo on 2010-12-23
> **bcbc said:**
> You can use a CD as well. I sometimes use RW but they tend to be less reliable. Burn it on the slowest speed.
You can also use a USB

Ubuntu.com has step by step instructions for each: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) (Step 2, click on CD or USB stick, then click on Show me how)
now? im writing this via ubuntu, but had not install anything... how can i make the 10.04 work for then upgrading using this cd?

---

### Post by bcbc on 2010-12-23
So your root.disk is on /dev/sda1 - therefore you can use the instructions on the wubi megathread exactly: Problem #2, Solution #1

> Boot a LiveCD, identify your Windows partition that contains the root.disk (make sure you mount the correct partition; this example assumes /dev/sda1), and edit grub.cfg as follows:


```
sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg
```
Remove all lines prior to the first menuentry of /boot/grub/grub.cfg. 

In other words, from the start of the file up to, but not including, the following menuentry
```
 ### BEGIN /etc/grub.d/10_lupin ###
```
Save, reboot.

---

### Post by NorlanBustillo on 2010-12-23
> **bcbc said:**
> So your root.disk is on /dev/sda1 - therefore you can use the instructions on the wubi megathread exactly: Problem #2, Solution #1
how do i edit grub.cfg

---

### Post by bcbc on 2010-12-23
> **NorlanBustillo said:**
> now? im writing this via ubuntu, but had not install anything... how can i make the 10.04 work for then upgrading using this cd?

You cannot upgrade from a desktop CD, only an 'alternate' CD. But I don't recommending upgrading anyway. I don't think there's a great advantage.

PS you don't need to mount /dev/sda1 as /mnt/windows in /etc/fstab as it's already mounted as /host by default for wubi installs.

---

### Post by NorlanBustillo on 2010-12-23
> **bcbc said:**
> You cannot upgrade from a desktop CD, only an 'alternate' CD. But I don't recommending upgrading anyway. I don't think there's a great advantage.

PS you don't need to mount /dev/sda1 as /mnt/windows in /etc/fstab as it's already mounted as /host by default for wubi installs.
but how do i edit grub.cfg???

---

### Post by bcbc on 2010-12-23
> **NorlanBustillo said:**
> how do i edit grub.cfg

1. Boot the Ubuntu CD, select "try without installing".
2. Go to a Terminal: CTRL+ALT+t
2. enter the following, hit enter after each line
```
sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg
```
The last command opens up grub.cfg in a text editor (gedit). Delete everything from the start of the file up to the line that looks like this:
```
### BEGIN /etc/grub.d/10_lupin ###
```
Save and exit.
Unmount and reboot:
```
sudo umount /mnt
sudo umount /media/win
```
Reboot, removing CD, and select Ubuntu - it should show the grub menu, and let you boot in as normal

---

### Post by theasprint on 2010-12-23
Hi,

Just stay calm and keep on following the instructions of *bcbc*

I did not answer for the past few replies because it was midnight/late in my time zone.
But I'm sure bcbc can help you a lot.

---

### Post by NorlanBustillo on 2010-12-23
> **bcbc said:**
> 1. Boot the Ubuntu CD, select "try without installing".
2. Go to a Terminal: CTRL+ALT+t
2. enter the following, hit enter after each line
```
sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg
```The last command opens up grub.cfg in a text editor (gedit). Delete everything from the start of the file up to the line that looks like this:
```
### BEGIN /etc/grub.d/10_lupin ###
```Save and exit.
Unmount and reboot:
```
sudo umount /mnt
sudo umount /media/win
```Reboot, removing CD, and select Ubuntu - it should show the grub menu, and let you boot in as normal

> **theasprint said:**
> Hi,

Just stay calm and keep on following the instructions of *bcbc*

I did not answer for the past few replies because it was midnight/late in my time zone.
But I'm sure bcbc can help you a lot.



Thanks!! now i got into ubuntu! thank you very much for both of you! :D

but, i have a question... the LiveCD is from 10.10, if i install it, would i lose all my actual (from ubuntu) information??

---

### Post by bcbc on 2010-12-23
> **NorlanBustillo said:**
> Thanks!! now i got into ubuntu! thank you very much for both of you! :D

but, i have a question... the LiveCD is from 10.10, if i install it, would i lose all my actual (from ubuntu) information??

Great - that's good news!

You're not finished though... if you look at that wubi megathread there's another part called "Permanent fix" that you have to do. Basically it just cleans up the /boot/grub directory. If you don't do this it will break again when you update your kernel. Have a look at the thread and let me know if you have any questions.

In answer to your question, if you try and install 10.10 with Wubi it will require that you first uninstall the existing 10.04.1 install - you will lose everything on your current Wubi install if you do this.

---

### Post by NorlanBustillo on 2010-12-24
> **bcbc said:**
> Great - that's good news!

You're not finished though... if you look at that wubi megathread there's another part called "Permanent fix" that you have to do. Basically it just cleans up the /boot/grub directory. If you don't do this it will break again when you update your kernel. Have a look at the thread and let me know if you have any questions.

In answer to your question, if you try and install 10.10 with Wubi it will require that you first uninstall the existing 10.04.1 install - you will lose everything on your current Wubi install if you do this.
thanks... in the synaptic thing (sorry to not write all, but its almost midnight here) the two things are supposed to be marked on a vertical line red?

---

### Post by bcbc on 2010-12-24
> **NorlanBustillo said:**
> thanks... in the synaptic thing (sorry to not write all, but its almost midnight here) the two things are supposed to be marked on a vertical line red?

Yeah a horizontal line ;) and there's a padlock on the left.

---

### Post by NorlanBustillo on 2010-12-24
> **bcbc said:**
> Yeah a horizontal line ;) and there's a padlock on the left.
Thanks!!! A lot, you were very kind for helping me...
don 't think im a girl or some ga... for telling that, but just the fact that my ubuntu is back makes me feel...:D:D:D
well, i think that is it
thanks again...
bye :P

---

### Post by bcbc on 2010-12-24
Hey, you're welcome. :) Glad you got it sorted out.

---

