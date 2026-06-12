---
title: "KDE Login Screen Wallpaper"
date: 2013-02-09
forum: Desktop Environments
---

### Post by zerubbabel on 2013-02-09
I just installed the latest KDE 4.10 upgrade from the backports repository, and now the login screen is a rather bold blue and violet swirl pattern. But I'm a more conservative type and would like something a bit more tame. Problem is, I can't figure out where to get to it. It doesn't seem as if anything in the Workspace Appearance settings affects it. I've tried different themes, and it remains the same...

---

### Post by suraj5989 on 2013-02-09
Are you using lightDM? 
There is an option 'Login Screen(LightDM)' in system settings
Go to the theme tab. Select the prefered theme and background image.

---

### Post by zerubbabel on 2013-02-09
Yes, I tried that too, and it shows only the standard KDE wallpaper (blue-gray rays emanating from the lower right corner), but that is not what is displayed either at login or to unlock the screen. Instead, what is displayed is that garish blue/purple/violet swirl. 

There are no options shown other than "Load from file" or "Clear image". I tried "Clear image" but it made no difference, and I wasn't really intending to make or find my own background image. I'd be content with the blue-gray ray pattern, actually. If I knew where that image was, I guess I could try loading that one.

---

### Post by suraj5989 on 2013-02-09
Is the image something like this?
[http://www.bluemintlinux.com/2012/12/new-wallpaper-coming-for-kde-4-10-and-kubuntu-13-04.html](http://www.bluemintlinux.com/2012/12/new-wallpaper-coming-for-kde-4-10-and-kubuntu-13-04.html)

I had upgraded to 4.10 recently but didnt get this image.

> Yes, I tried that too, and it shows only the standard KDE wallpaper  (blue-gray rays emanating from the lower right corner), but that is not  what is displayed either at login or to unlock the screen. Instead, what  is displayed is that garish blue/purple/violet swirl. 

I am not sure how you are getting different images in settings and the actual login screen though.
You will have to try and set a different wallpaper.

---

### Post by suraj5989 on 2013-02-09
Try running this command in the terminal.
> cat /etc/lightdm/lightdm-kde-greeter.conf

Does this have entry for 'BACKGROUND'?
if its there then you can remove this entry and see if it works.
Make a backup of te file before you do it.

---

### Post by llanitedave on 2013-02-09
Interesting question, because I have a similar issue.  I have a background image selected, but it doesn't display on my login screen.  I suspect because it's in my home folder, which isn't accessible to the system until after my login.

But I'm not sure how or where to copy it in such a way that the login manager can find it.  I  suppose a sudo could do it -- but not sure what's the right directory for it.

---

### Post by zerubbabel on 2013-02-10
> **suraj5989 said:**
> Is the image something like this?
[http://www.bluemintlinux.com/2012/12/new-wallpaper-coming-for-kde-4-10-and-kubuntu-13-04.html](http://www.bluemintlinux.com/2012/12/new-wallpaper-coming-for-kde-4-10-and-kubuntu-13-04.html)



Yes, that's the one!

---

### Post by zerubbabel on 2013-02-10
> **suraj5989 said:**
> Try running this command in the terminal.


Does this have entry for 'BACKGROUND'?
if its there then you can remove this entry and see if it works.
Make a backup of te file before you do it.

It has "Background =" but no setting.

---

### Post by zerubbabel on 2013-02-10
Surely someone must know how to change this login screen wallpaper...

---

### Post by suraj5989 on 2013-02-11
I found the old wallpaper in :
/usr/share/wallpapers/Ariya
You can either set the correct image in this path through the system settings or copy the file to your home directory and then set it.
Make sure you choose the right resolution .

---

### Post by zerubbabel on 2013-02-13
> **suraj5989 said:**
> I found the old wallpaper in :
/usr/share/wallpapers/Ariya
You can either set the correct image in this path through the system settings or copy the file to your home directory and then set it.
Make sure you choose the right resolution .

This worked for the login screen, but not for unlocking the screen after inactivity.

---

### Post by gunghang on 2013-07-05
The log in background on my netbook is /usr/share/backgrounds/warty-final-ubuntu.png

If anybody is bored, this is the odyssey that led me here.

I'm having a delightful time setting up an Asus X202e.  I'd never even heard of EFI.

Anyway, Ubuntu is part of my multi-boot.  I have the Kubuntu desktop on 13.04.  

(I also discovered that KDE is now default with Ubuntu Ultimate 3.5)

(I went with Ringtail because it's 64 and I'd read that it has UEFI support or some such thing - it was my fourth try and what broke the "EFI barrier" and produced a grub menu.)

Oh, yeah, the log in screen background:

It had just used whatever the desktop background was.  Then, I switched to Kubuntu Netbook.  I got the Plymouth theme screen.

The image is warty-final-ubuntu.png which is in /usr/share/backgrounds.

I changed the file name to warty-final-ubuntu-orig.png.  I then changed one of my "terrible Linux wallpaper" pix to warty-final-ubuntu.png and copied it to the /usr/share/backgrounds folder.  My log in background is now Star Tux.

I miss having different wallpaper on the different desktops.

I love the steam powered linux splash screen.

My background screen for a locked computer is  /usr/share/wallpapers/Elarun/contents/images/2560x1600.png

---

