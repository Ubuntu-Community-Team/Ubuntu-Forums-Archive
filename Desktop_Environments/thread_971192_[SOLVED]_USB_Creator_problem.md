---
title: "[SOLVED] USB Creator problem?"
date: 2008-11-04
forum: Desktop Environments
---

### Post by usererror on 2008-11-04
I wanted to update my usb key from ubuntu 8.04 to 8.10.  my desktop is 8.10 so i tried to use the tool in System > Administration. but it does not work I get this error when I select the ISO image I downloaded:

"This is not a desktop install CD and thus cannot be used by this Application."

In the terminal I see this:

```

=======
$ sudo usb-creator 

Xlib:  extension "RANDR" missing on display ":0.0".

-- Starting up at 19:20:40 --
[19:20:40] adding: /dev/sdh
[19:20:48] mounting /home/mark/Desktop/ubuntu-8.10-desktop-i386.iso
[19:20:48] Unable to find /tmp/tmp_apXCX/.disk/info, not using /home/mark/Desktop/ubuntu-8.10-desktop-i386.iso
[19:20:48] [Errno 5] Input/output error

```

Any ideas?

I burned it to a CD and then at the very end the process also failed.

---

### Post by john183 on 2008-11-06
The main thing that comes to mind after looking at your error is that the ISO is corrupt. If you haven't tried already, you might want to re-download it. I am having problems creating a bootable usb drive also, but i don't get any errors until i try to boot off of it. then it tells me that the OS is missing.

---

### Post by snowpine on 2008-11-06
You might look into Unetbootin--I have used it successfully to create many live USB sticks. It seems there are still some bugs in the Intrepid USB Creator. Good luck!

---

### Post by usererror on 2008-11-08
Thanks for the suggestions, I'm away from my PC for a few days so I will try again when I get home!

---

### Post by usererror on 2008-11-14
> **john183 said:**
> The main thing that comes to mind after looking at your error is that the ISO is corrupt. If you haven't tried already, you might want to re-download it. I am having problems creating a bootable usb drive also, but i don't get any errors until i try to boot off of it. then it tells me that the OS is missing.

I have finally had time to work on this.  I downloaded a new ISO from a closer mirror to me and I am now using it to do a fresh install of Ubuntu on another laptop.

So the root of my problem was a bad ISO

---

