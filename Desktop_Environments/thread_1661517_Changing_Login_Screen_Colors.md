---
title: "Changing Login Screen Colors"
date: 2011-01-06
forum: Desktop Environments
---

### Post by jbraum on 2011-01-06
How do I change the colors on the login screen i.e. the button color and color surrounding the username.  I've changed the wallpaper and have just like I want except the others mentioned above.

Thanks

---

### Post by stinkeye on 2011-01-07
Open the terminal and run the following commands

```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```

Then logout, and you’ll see an Appearance window pop up. Change it to how you prefer it, then close it and login as usual.

When you have logged in after finishing the customizing, run this command to prevent the Appearance window from opening at the GDM screen every time.

```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by jbraum on 2011-01-07
I was more in line of thinking of changing the orangeish color on the username.  Like the image with the demo username


[IMG]http://www.techotopia.com/images/9/95/Ubuntu_10.10_login_screen.jpg[/IMG]

---

### Post by stinkeye on 2011-01-07
....and that can be changed by either customizing or changing the theme 
with the method I described.
It will only change the look of the login screen.
Once booted your normal theme will apply.

---

### Post by jbraum on 2011-01-07
Got it...  Thanks but isn't there a file where the normal theme is located that the hex color(s) can be changed.

---

### Post by stinkeye on 2011-01-07
Yep.
Every theme in **/usr/share/themes** or **~/.themes** has it's
own **gtkrc** file.

---

### Post by tora1188 on 2011-05-09
addended question:

Is there any way to use this method to make the login box completely transparent, letting the background show through?

I have this for now, making the box and everything but the text black, on a mainly black background. It works, since nothing overlaps the box, but I would like to be able to have an uninterrupted image behind the text.

Any ideas?

[IMG]http://http://imageshack.us/photo/my-images/197/img0150xm.jpg[/IMG]

---

