---
title: "When rebooting Ubuntu desktop ed 704"
date: 2007-08-18
forum: Dell  Ubuntu Support
---

### Post by arvadawest on 2007-08-18
Hi,
I have a Dell XPS 410N with Ubuntu desktop ed. 704.  I notice when I do a "shutdown" on this system it will shutdown fine and boot back up when I hit the power button, but, when I do a "restart" of the system, in the Ubuntu screen it stalls and does not boot up.  I have to manually shutdown to start up.

What could be causing this?  Thanks.

---

### Post by arvadawest on 2007-08-18
Let me update this more:

When I restart, it goes to the screen the eliminates the orange bars, then when it is supposed to reboot and add the orange bars, it stalls, no oranges bars.  I know this sound primetive in how I am explaining it.  I tried to resinstall the OS again and it still does this.  I do not having to power down the system by pushing the power button when it gets stuck.  What do I do??  thanks.

---

### Post by FoundmyTux on 2007-08-19
Try sudo gedit /boot/grub/menu.lst

Find the line that begins with kernel and ends with quiet splash and add reboot=b to end of line. Save file. Shut down computer. After restart reboot should work.

---

### Post by arvadawest on 2007-08-19
Hi FoundMyTux,
I want to thank you so much for your help.  It worked!  I am a newbie to Linux (ubuntu).  I resinstalled the OS several times thinking it was my fault.

1)  I am curious.  Why wouldn't it add "reboot=b" after I reinstalled the OS?

2)  Are there any good books to learn about command line commands on Linux?

Thanks so much!  -aw

---

### Post by FoundmyTux on 2007-08-19
My answer to your first question is I don't know. 

A good place to start learning about the command line is:
[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")

Another excellent place is these forums. Study the examples. In the beginning you'll understand very little, but stick with it. If you don't understand a command type in terminal man + command will give you a help file.

---

### Post by arvadawest on 2007-09-24
Hi All,
I made this change last month and it work.  Since then, my system has been running for 30 days.  I went to reboot and had the same problem.  I have to do a complete shutdown in order for my system to come up, but when I do a "restart" it won't boot.  What can I do?  Thanks.

-arvadawest


> **FoundmyTux said:**
> Try sudo gedit /boot/grub/menu.lst

Find the line that begins with kernel and ends with quiet splash and add reboot=b to end of line. Save file. Shut down computer. After restart reboot should work.

---

### Post by FoundmyTux on 2007-09-25
Hi, did you install the new kernel update this morning? If you did check /boot/grub/menu.lst if reboot=b was added to update. I have done more research on this problem and found you should  also add reboot=b to the line
 #defoptions=quiet splash as this will automatically add reboot=b to new kernel updates.

---

### Post by Louis Cypher on 2007-09-25
> **arvadawest said:**
> Hi,
I have a Dell XPS 410N with Ubuntu desktop ed. 704.  I notice when I do a "shutdown" on this system it will shutdown fine and boot back up when I hit the power button, but, when I do a "restart" of the system, in the Ubuntu screen it stalls and does not boot up.  I have to manually shutdown to start up.

What could be causing this?  Thanks.

I had the same problem with my Dell 410n.  The reboot=b solved my problem though. Thx for the info.

---

### Post by arvadawest on 2007-09-25
Hi, thanks.
Should I also add reboot=b to the other two lines with "splash"?

Yes, I updated the kernel yesterday and when I rebooted and it would not reboot.

This certainly is a problem and I am glad I am not the only one.  Will this happen to each update to the kernel?  thanks.

-aw


> **FoundmyTux said:**
> Hi, did you install the new kernel update this morning? If you did check /boot/grub/menu.lst if reboot=b was added to update. I have done more research on this problem and found you should  also add reboot=b to the line
 #defoptions=quiet splash as this will automatically add reboot=b to new kernel updates.

---

### Post by arvadawest on 2007-09-25
This is very strange.  When I add reboot=b to:

# defoptions=quiet splash reboot=b

it will work when i immediately reboot, but when i reboot a 2nd time it will stall again.  clearly, this is a problem for other's who own a dell 410.

does anyone have any ideas?  i had also added reboot=b to:

itle		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=616ae6af-fd8c-4afa-97e8-1dd8bd8b690d ro quiet splash

and

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=616ae6af-fd8c-4afa-97e8-1dd8bd8b690d ro quiet splash

both after "quiet splash" but it did not work, so i removed "reboot=b" from the last two, but kept the reboot=b on the defoptions.  thanks.

-aw

---

### Post by FoundmyTux on 2007-09-26
Sorry for the delay, I was at work.

When you open /boot/grub/menu.lst you should have two kernels listed, kernel 2.6.20-15-generic and kernel 2.6.20-16-generic. Both kernels should have a line that ends with quiet splash. Add reboot=b to these two lines.

Now find the section that begins with  ## additional options to use with the default boot option. The last line of that section should be # defoptions=quiet splash. Add reboot=b to the end of that line.

Now don't reboot. Instead shut down your computer. After you restart your computer everything should work.

The reboot=b after the existing kernels is to fix reboot for the kernels that are already installed.

The reason for reboot=b on defoptions line is to automatically add reboot=b to any future kernel updates.

---

### Post by arvadawest on 2007-09-26
> **FoundmyTux said:**
> Sorry for the delay, I was at work.

When you open /boot/grub/menu.lst you should have two kernels listed, kernel 2.6.20-15-generic and kernel 2.6.20-16-generic. Both kernels should have a line that ends with quiet splash. Add reboot=b to these two lines.

Now find the section that begins with  ## additional options to use with the default boot option. The last line of that section should be # defoptions=quiet splash. Add reboot=b to the end of that line.

Now don't reboot. Instead shut down your computer. After you restart your computer everything should work.

The reboot=b after the existing kernels is to fix reboot for the kernels that are already installed.

The reason for reboot=b on defoptions line is to automatically add reboot=b to any future kernel updates.
Hi Tux,
Thank you so very much.  It worked!  I was doing everything you told me previously, but I was "restarting" instead of "shutting down" my computer after the change to menu.lst.  

I am curious.  Why would that make a difference?  Thanks so much!

-aw

---

