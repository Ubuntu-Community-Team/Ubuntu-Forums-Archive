---
title: "Two desktop screw ups can anyone tell me how to fix them?"
date: 2012-11-02
forum: Desktop Environments
---

### Post by Joentokyo on 2012-11-02
I installed 12.04 Precise Pangolin, but I checked gdm instead of lightdm at installation, and made a typo in the name I chose for my computer. I only noticed the typo when I was using a terminal window.

Because of gdm and compiz Ubuntu Tweak cannot reset my login screen. 

I would dearly like to change my computer name. I am sure this is possible, but do not know how. Help!

---

### Post by ajgreeny on 2012-11-02
To change you computer name you need to edit **/etc/hosts** and **/etc/hostname**, replacing the occurrence of the typo with what it should be.

If you have both gdm and lightdm installed you can choose to use lightdm by running ```
sudo dpkg-reconfigure gdm
```and you should then be given the option for which to use.

---

### Post by Joentokyo on 2012-11-03
:KS Thanks a million! I ran the commands and on reboot the name was changed.

However, no joy with changing the login screen.  When I use advanced settings  and click  themes, the shell will not allow a change in its theme. ](*,)

That may be what is blocking Ubuntu Tweak. If you know a work around, especially one that doesn't involve using UT, I would be grateful. UT causes my system to report a lot of errors.

---

### Post by Joentokyo on 2012-11-03
> **Joentokyo said:**
> :KS Thanks a million! I ran the commands and on reboot the name was changed.

However, no joy with changing the login screen.  When I use advanced settings  and click  themes, the shell will not allow a change in its theme. ](*,)

That may be what is blocking Ubuntu Tweak. If you know a work around, especially one that doesn't involve using UT, I would be grateful. UT causes my system to report a lot of errors.


Update: Finally got the login screen changed\\:D/, but had to use a file from user/share/backgrounds in the past you could set the same image as your desktop.

Thank you for your help!

---

### Post by ajgreeny on 2012-11-03
To change the login screen to be the same as your desktop image you may be able to copy the image you want to use to **/usr/share/backgrounds** and then choose it from there when changing the login screen background.

---

### Post by Joentokyo on 2012-11-04
> **ajgreeny said:**
> To change the login screen to be the same as your desktop image you may be able to copy the image you want to use to **/usr/share/backgrounds** and then choose it from there when changing the login screen background.

I tried moving the images into /usr/share/backgrounds, but permission was refused.

I used a work around that I found in another thread; it is to open a new directory and folder with image files. Selecting files from that folder changes the login screen by using Ubuntu Tweak.

However, if you can tell me how to move them into /usr/share/backgrounds, I would like to do so as it is a better way I think.

---

### Post by ajgreeny on 2012-11-04
As you have found, you need to use **sudo** to put anything into a system folder, but be careful as you can do great damage if you don't know what you're doing.
```
sudo cp /path/to/*image.jpg* /usr/share/backgrounds/
```
will do that. You could also do it with ```
gksudo nautilus
``` which opens the file manager with root permissions, but be sure to close that instance of nautilus as soon as you finish, and don't do anything else you are not sure about.

---

### Post by Joentokyo on 2012-11-05
> **ajgreeny said:**
> As you have found, you need to use **sudo** to put anything into a system folder, but be careful as you can do great damage if you don't know what you're doing.
```
sudo cp /path/to/*image.jpg* /usr/share/backgrounds/
```will do that. You could also do it with ```
gksudo nautilus
``` which opens the file manager with root permissions, but be sure to close that instance of nautilus as soon as you finish, and don't do anything else you are not sure about.

Everything seems to be working now. Thanks again for all your help.

---

