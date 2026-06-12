---
title: "Nvidia Driver Removed the Splash screen"
date: 2014-10-26
forum: Desktop Environments
---

### Post by Ubu1son on 2014-10-26
I installed the nvidia driver 331 ( tested), after rebooting, the splash screen changed.

It was the default blue xubuntu 14.04, with the spinning circle, after nvidia installed, it is now like the default Ubuntu splash screen, with the horizontal orange dots, but it says xubuntu 14.04..........


How can I get back my default xubuntu splash screen?



thanks.

gpu is gt240

---

### Post by Ubu1son on 2014-10-27
This hasnt happened to anyone else?

  I tried it 3 times now, and each time after activating the nvidia driver, the default splash screen is replaced!  :mad:

---

### Post by EmpireITtech on 2014-10-27
[http://askubuntu.com/questions/362722/how-to-fix-splash-screen-in-all-ubuntu-releases](http://askubuntu.com/questions/362722/how-to-fix-splash-screen-in-all-ubuntu-releases)
or
[http://www.binarytides.com/ubuntu-fix-nvidia-graphics/](http://www.binarytides.com/ubuntu-fix-nvidia-graphics/)

---

### Post by grahammechanical on 2014-10-27
As far as I know, the proprietary driver does not do that kind of thing. But something like that will happen if we install an alternative desktop. If we install the Xubuntu desktop onto Ubuntu then the Plymouth splash screen for Ubuntu will change to the Xubuntu splash screen. And it will happen the other way around if we install Ubuntu desktop on top of Xubuntu.

Regards

---

### Post by Dennis N on 2014-10-27
> **Ubu1son said:**
> I installed the nvidia driver 331 ( tested), after rebooting, the splash screen changed. It was the default blue xubuntu 14.04, with the spinning circle, after nvidia installed, it is now like the default Ubuntu splash screen, with the horizontal orange dots, but it says xubuntu 14.04..........


It have the same problem with Nvidia 331 and Xubuntu 14.04.  What you see is the xubuntu-text plymouth theme instead of the xubuntu-logo plymouth theme. Prior to the 14.04 release, it was fixable with the method linked to in post #3 for fixing the splash screen (they are essentially the same). That didn't work for me in 14.04. I just ignore it.

Maybe that solution will work for you, you can ignore it, or you can use quiet nosplash in the grub command line and have a blank screen.

There is an error in the second link where it says:

> To fix the splash screen create and edit
$ sudo nano /etc/initramfs-tools/conf.d/splash
And fill it with the following line
echo FRAMEBUFFER=y
  

The line you enter should not include **echo**.

---

### Post by Ubu1son on 2014-10-27
> **EmpireITtech said:**
> [http://askubuntu.com/questions/362722/how-to-fix-splash-screen-in-all-ubuntu-releases](http://askubuntu.com/questions/362722/how-to-fix-splash-screen-in-all-ubuntu-releases)
or
[http://www.binarytides.com/ubuntu-fix-nvidia-graphics/](http://www.binarytides.com/ubuntu-fix-nvidia-graphics/)

> **Dennis N said:**
> It have the same problem with Nvidia 331 and Xubuntu 14.04.  What you see is the xubuntu-text plymouth theme instead of the xubuntu-logo plymouth theme. Prior to the 14.04 release, it was fixable with the method linked to in post #3 for fixing the splash screen (they are essentially the same). That didn't work for me in 14.04. I just ignore it.

Maybe that solution will work for you, you can ignore it, or you can use quiet nosplash in the grub command line and have a blank screen.

There is an error in the second link where it says:

  

The line you enter should not include **echo**.


Even though after reading all of those "fixes" on the net, I assumed they were just in relation to the resolution, and not an actual change in the splash.
But I tried that anyway before I posted, and it didn't work, it did show the framebuffer=y text ( an error as you say), which just made it more annoying.......

I didn't try the other methods which were old and involved installing things. I didn't want to completely trash the install for the splash.

I cant believe that the nvidia driver just removes a users splash screen, and there is no official fix or method for preserving it.... really weird, there must be a way for 14.04!

---

### Post by Dennis N on 2014-10-27
> But I tried that anyway before I posted, and it didn't work, it did show the framebuffer=y text ( an error as you say), which just made it more annoying.......

Did you try it again with entering only **FRAMEBUFFER=y** (Don't forget to run **sudo update-initramfs -u** afterwards)

Did you try switching to the open source driver?

---

### Post by Ubu1son on 2014-10-31
> **Dennis N said:**
> Did you try it again with entering only **FRAMEBUFFER=y** (Don't forget to run **sudo update-initramfs -u** afterwards)

Did you try switching to the open source driver?

But which is the correct most uptodate method for 14.04lts?

there is:

> Open your terminal and type
  ```
sudo apt-get install v86d
```
  Then
  ```
sudo gedit /etc/default/grub
```
  Find this line
  ```
#GRUB_GFXMODE=640x480
```
  and chagne for this one (*of course choose your resolution*)
  ```
GRUB_GFXMODE=1440x900x24
GRUB_GFXPAYLOAD_LINUX=keep
```
  Save file and type in terminal
  ```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
sudo update-grub2
```



And this:

> **1. Fix the grub boot menu screen**

 To fix the grub boot menu screen edit the file /etc/default/grub
 ```
$ sudo nano /etc/default/grub
``` 
In the file look for the section that has a field named GRUB_GFXMODE declared.
 # The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480 Edit it to look something like this
 ```
GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep
``` 
Now run the following command to regenerate the grub configuration file.
 ```
$ sudo update-grub2
``` 
Now reboot your system. The grub boot screen should have the resolution 1024x768.
 **Get a higher resolution**
 At the Grub boot screen press 'c' key to access the grub console. At the grub console run the following command
 ```
grub> vbeinfo
``` 
It will display all the supported resolutions. If you find a  resolution higher than 1024x768 in the list, then you can use it as the  value of GRUB_GFXMODE to get better. Make sure to select a resolution  that matches the aspect ratio of the native resolution of your monitor. 
  **2. Fix the splash screen**

 To fix the splash screen create and edit 
 ```
$ sudo nano /etc/initramfs-tools/conf.d/splash
``` 
And fill it with the following line
 ```
echo FRAMEBUFFER=y
``` 
Now run the following command
 ```
$ sudo update-initramfs -u
``` 
Reboot again and now the startup and shutdown splash screens should  have the resolution specified in GRUB_GFXMODE field of the grub  configuration file.



Why does the first method need to install something???


I will try second method again, without echo, it should work?

---

### Post by Dennis N on 2014-10-31
I don't think you need to install anything. vbeinfo works anyway. If you try that command  there could be too much output and it will disappear off the screen before you can see the first part. You can see one page at a time if you type set pager=1 first.

```
grub > set pager=1
grub > vbeinfo
```

Method 2 is what I used in the past to fix this problem. Definitely leave off the echo. It won't work if you put it in. I used it a few days ago with an Intel graphics machine that was doing the same thing with 14.04. It worked on that machine. It didn't help with another computer with Nvidia using 14.04 where it did in previous releases. But yours might. You won't know until you try.

---

