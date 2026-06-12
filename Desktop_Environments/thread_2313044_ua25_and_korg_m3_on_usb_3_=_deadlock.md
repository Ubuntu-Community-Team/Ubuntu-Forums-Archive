---
title: "ua25 and korg m3 on usb 3 = deadlock"
date: 2016-02-09
forum: Desktop Environments
---

### Post by alfton on 2016-02-09
hi, I just want to share something i detected, I installed 3 different linux system (linux mint 17.3, xubuntu 14.04, and xubuntu 15.10), same result on all 3..

system is installed with nvidia-current, and a linux-image-lowlatency kernel.

I have 1 Roland UA25 (usb 2 based), and on Korg m3 synth, I guess the midi communicator there is also based on usb 2.

I just bought my self a new computer with usb 3 ports. I plugged inn my devices, and fired up the qjackctl, and configured it to use UA25 as sound card. And at last rosegarden to start compose music.. But experienced random deadlock on my system, (I had to force turn of and power on again to make it work).. Ill tryed everything. without the nvidia driver, it seems at first that helped a bit. So I thought that nvidia driver was not compatible the lowlatency kernel image, so I relaxed with that, and created some more music. But suddenly out of the blue, the computer again deadlocked. 

Ill tried everything, memory check, stress test on the graphic card, you name, all bug search/report I could think of, I even did do a lot of tail -f (diffrent log files) just for a hope of some clue what did happen just before it deadlocked..

But then, ill thought back to my old computer, that one also had a nvidia driver, and lowlatency kernel without deadlock. But there was a different.. it only had USB 2..

my luck in this was that the new one also did have 3 usb 2 ports.. and i switzed the UA25, and korg M3 to it, and voilà.. No more deadlock..

Have anyone else experience this problem?

---

### Post by alfton on 2016-03-21
update on this.
finaly did find the cure for this behavior, the problem was that the USB port did aktivate powersave, and the ua25 does not like that. 

deactivations of the usb powersave in kernel boot parameter in grub did solve the problem.

best regards

---

