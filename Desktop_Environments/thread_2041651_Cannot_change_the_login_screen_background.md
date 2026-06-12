---
title: "Cannot change the login screen background"
date: 2012-08-13
forum: Desktop Environments
---

### Post by luvshines on 2012-08-13
I recently upgraded to 12.04 and am not observing some issue with the login screen background
I was using 'ubuntu tweak' to keep the login screen background different from my desktop background
But something seems to have changed recently. The setting is no longer working
The screen which I chose as login is displayed only for a flash second and is immediately overriden by my desktop background

So effectively, both my desktop and login background are same. I have tried to change it repeatedly using the same tweak but invain.

Any help would be much appreciated

---

### Post by cmcanulty on 2012-08-13
Ubuntu tweak is an easy way to do that

---

### Post by satish_j on 2012-08-13
The login screen background is stored in /usr/share/backgounds.
Navigate to the directory and chmod the selected background image to 755.
Logout and Login/

---

### Post by luvshines on 2012-08-14
> **cmcanulty said:**
> Ubuntu tweak is an easy way to do that

I am already trying to use Ubuntu tweak.

From my initial post> 
I was using 'ubuntu tweak' to keep the login screen background different from my desktop background
But something seems to have changed recently. The setting is no longer working

---

### Post by luvshines on 2012-08-14
> **satish_j said:**
> The login screen background is stored in /usr/share/backgounds.
Navigate to the directory and chmod the selected background image to 755.
Logout and Login/

Nope !! Not working from me. The permission were 644 already, I changed it to 755 but again the same effect.
The screen which I selected as login is displayed for a split second but is immediately overriden by the desktop image right at the login screen

---

### Post by Bucky Ball on 2012-08-14
Grub Customizer is my tool of choice.

[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)

---

### Post by deadflowr on 2012-08-14
The login background now runs the desktop background of whomever is set for logging in. If you have a system with multiple users, scrolling between them will change to whatever each user has set as a backgound. It does at first feel annoying, but eventually you can get used to it. I too, liked(cool feature) the 11.10 version, but now I have grown to like(tolerate) the new way. So far, I have not found an easy way to replicate the 11.10 experience.

---

### Post by luvshines on 2012-08-14
> **Bucky Ball said:**
> Grub Customizer is my tool of choice.

[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)

But I never said anything about grub screen background. I want to customize just the login screen background

---

### Post by luvshines on 2012-08-14
> **deadflowr said:**
> The login background now runs the desktop background of whomever is set for logging in

But isn't it configurable ?
It was working 2-4 days ago and stopped working suddenly.
Infact the login screen I selected shows for a second and is then replaced by my desktop screen

---

### Post by satish_j on 2012-08-14
> **luvshines said:**
> Nope !! Not working from me. The permission were 644 already, I changed it to 755 but again the same effect.
The screen which I selected as login is displayed for a split second but is immediately overriden by the desktop image right at the login screen

This is strange.I had similar problem and was able to get it resolved by changing the rights on the file.
Maybe you can try with 740 and check

---

### Post by luvshines on 2012-08-14
> **satish_j said:**
> This is strange.I had similar problem and was able to get it resolved by changing the rights on the file.
Maybe you can try with 740 and check

That is not working either.

Infact changing it to 740 has changed the behavior of the login screen a bit.

I see the default purple(dotted) background which is immediately replaced by the desktop screen

Earlier it was default purple(dotted) background --changes-to--> the login background which I chose --changes-to--> my desktop screen

So removing the read permission from the file has reduced the image flash from 3 to 2
default purple(dotted) background --changes-to--> my desktop screen

---

### Post by luvshines on 2012-08-14
An update to this.

Since the behavior seemed to change by changing the read permissions from image files, **for now I have deployed a dirty hack to get it working** :tongue:

I have removed the 'others' read permission from the file which is my current desktop background.
So at login the screen behavior is
default purple(dotted) background --changes-to--> the login background which I chose

And it sticks there since it can't read the next file

BUT I don't like this hack. I change my wallpaper very frequently and adjusting the permission for each and every file is not gonna work for me :(

---

### Post by luvshines on 2012-08-14
Finally, this seems to have fixed it\\:D/

I was trying to remove 'draw-user-backgrounds' using dconf-editor but it was not working.

Then got the steps from googling```
sudo -i
xhost +SI:localuser:lightdm
su lightdm -s /bin/bash
gsettings set com.canonical.unity-greeter draw-user-backgrounds 'false'
```

And voila, it works now. Got back the original behavior:guitar:

---

### Post by cmcanulty on 2012-08-14
another aid for this is the app Splash Screen Manager

---

