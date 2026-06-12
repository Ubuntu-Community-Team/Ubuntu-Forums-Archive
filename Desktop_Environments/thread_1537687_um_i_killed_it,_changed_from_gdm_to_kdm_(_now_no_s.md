---
title: "um i killed it, changed from gdm to kdm :( now no screen"
date: 2010-07-23
forum: Desktop Environments
---

### Post by Tristan85 on 2010-07-23
hey i installed kde to try it out
and as i read in one of the post to try and get a shutdown button {instead of logout > shutdown}
i changed to kdm {from gdm}
problem is now my screen is stuiffing up and i cant use my linux.
is there some way i can restore it using my livecd so it runds the gdm instead

when i load my linux the screen stays up the top and is all blurred and unreadable. i tried booting into recovery mode but screen is still the same.and therfore i dont know what the options are in the recovery mode

im usuing ubuntu 10.04

thanks in advance if anyone can help

---

### Post by linux18 on 2010-07-23
this is the fourth time today I'm posting this quote from myself:

 > 
these steps will boot any non-bricked ubuntu:

-choose recovery mode at grub
-drop to a root prompt
-type telinit 3 and login
-then type xinit 
-when xinit starts type: metacity &  - for ubuntu OR compiz &  -  if you have it OR flux/openbox &  - if you have it OR fvwm & -  for xubuntu
-then type gnome panel & -for ubuntu OR xfce4-panel & -for xubuntu
-lastly type nm-applet & -for networking


then remove kdm and gdm then reinstall gdm: 
```
 sudo apt-get purge gdm kdm && sudo apt-get install gdm 
```
enjoy!

---

### Post by Tristan85 on 2010-07-24
sorry man i seen that but when i go recovory it is the same and i cant read what to select
:(

---

### Post by WinRiddance on 2010-07-24
You don't "boot" into recovery mode.
Recovery mode is selected from a text menu which may not even appear on your screen if you have Ubuntu 10.04 as the only installed operating system (no dual-boot).

What you're describing has it least partially to do with your graphic chip. The grub menu which is also where the recovery mode is, shouldn't have any problem at all displaying your grub text based menu ... white text on black background. That's why I don't think that you've ever actually entered your recovery mode as of yet.

Shut down the computer. Not a restart but a complete shut off. Wait a minute or two and then power it back up, but this time start tapping the left shift key once every second or two, to make the text based menu appear on the screen. Depending on your computer you may have to do this 3 or 4 times and you may have to try the right shift key too ....
**Then follow the suggestions of linux18**.

---

### Post by Tristan85 on 2010-07-25
i have a dual boot with vista, my linux runs off an external hdd,
when i boot at the start i hit esc select external it boots to grub, then goes black as it loads then when the gui comes up {normal not recovery option} it starts loading then you know the screen where kde shows what its loading it hits there perfectly fine then the whole screen shrinks to the top of the screen and is all scrambled.

and when i select recovry mode {in grub}
it starts loading then also shrinks to the top of the screen and i cant read the options there cause its also scrambled in the top inch of the screen

for that shift thing do i do that at the grub prompt ?

sorry im really new to linux aswell.


EDIT: um i tried that shift to get into grub recovery, couldnt get it to work,  at the grub menu i can press c to get to the command line. is that any help??

---

### Post by Tristan85 on 2010-07-25
ok well im back in linux again instead of windows...

thanks for all your help guys. i took my hdd and used it on a friends comp. it had something to do with my nvidia graphics card. her laptop doesnt run one so it loaded i reinstalled gdm anyways.

but on mine as it loads {i think its the splash screen that is still all blurred and messed up {and confined to the top inch of the screen} {will try and get a photo on my phone and upload it, incase anyone knows of a way to fix it ?

also how do i mark this thread as solved ?

ok here are some photos {sorry about the bad quality they are off my phone.

[http://i764.photobucket.com/albums/xx284/Tristan85_photos/Pic_0726_076.jpg](http://i764.photobucket.com/albums/xx284/Tristan85_photos/Pic_0726_076.jpg)

[http://i764.photobucket.com/albums/xx284/Tristan85_photos/Pic_0726_077.jpg](http://i764.photobucket.com/albums/xx284/Tristan85_photos/Pic_0726_077.jpg)

 also none of that is readable they arent words

---

