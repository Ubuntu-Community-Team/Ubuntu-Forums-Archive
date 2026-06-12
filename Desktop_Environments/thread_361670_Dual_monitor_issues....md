---
title: "Dual monitor issues..."
date: 2007-02-14
forum: Desktop Environments
---

### Post by resiak on 2007-02-14
M'kay, well, I have myself a little predicament. My computer has Microsoft Windows XP Pro x64-bit edition, and I also have Ubuntu installed. The only thing that is preventing me from using Ubuntu more is the inability to use my Dual screens. I have the driver downloaded from  nVidia, and it wont let me install the driver. My graphics card is a GeForce 7600 GS. I know how to get to text mode, and how to get to root, so I don't need help in that spot. The error that I receive while trying to install it goes something like: Cannot install driver with the Xserver running. Please shut it down in order to install this driver. However, I do not know how to shut down the Xserver. 

Also, in order to get to the Text mode, I hit ctrl+alt+F1, and this is after it gets to the splash login screen on Ubuntu.  If anyone else has had trouble installing this driver, please let me know how you managed to install it. The directions on the website are no help, all it says is "type sh (insert driver name here).run"

i renamed the driver "driver.run" in order to make it easier to type, and remember.

Thanks in advance for the help,

Oh, and my email is [email]darkresiak@gmail.com[/email], so if you dont feel like posting, just send me a message on what to do. 

Thanks,

~Resiak

---

### Post by hendo on 2007-02-15
I'm no expert on this, having only installed Ubuntu myself a few days ago. I have two monitors running on an older GeForce 5200 card.

To get it working with nVidia TwinView, i followed, step by step, the instructions in:

[this thread]("http://www.ubuntuforums.org/showthread.php?t=221174")

then

[this page](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

then

[this thread](http://www.ubuntuforums.org/showthread.php?p=1773584).

I never went to the nVidia site for drivers at all, just downloaded what i needed through Synaptic using the instructions on the second page linked above. 

I can't give any more advice than that, i'm afraid. Good luck.

---

### Post by hfw on 2007-02-15
I had similar issues when I switched from XP to Ubuntu, and fought with the driver issue until someone pointed me to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Which is a little program called Envy.  It did the driver install for me, which for some reason I couldn't get right.  Even with the help of the above mentioned threads.  You will still have to go edit your xorg.conf.  The instructions for that are in one of the threads mentioned by a previous poster in this thread.  

Together everything is working great.  Who needs XP?

-hal

---

### Post by CrazyGenie on 2007-02-15
I have sent you a quick solution.. hope it works!!!

---

