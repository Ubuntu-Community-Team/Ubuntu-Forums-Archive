---
title: "XFCE changing background to gnome/unity"
date: 2012-03-14
forum: Desktop Environments
---

### Post by new-to-ubuntoo on 2012-03-14
Hello

I just have a small thing I hope someone can help me with. I have installed Ubuntu 11.10 32 bit "Desktop" version. I have installed the xfce4 desktop environment because i want the flexibility to switch between unity and xfce when i feel like a change.

When I first login to xfce, the default background comes up with the picture of the mouse, however it disappears after about 4 seconds and goes back to the gnome/unity background default, which i dont want when using xfce desktop, and when i go to change the wall paper, it only has the gnome backgrounds and none of the xfce ones. Its almost like unity has crept in to xfce or something and is taking it over.

Im pretty new to linux so a gui fix would be preferable.

James

---

### Post by 3Miro on 2012-03-14
The problem is that you started Nautilus. Nautilus is the Gnome/Unity file manager and it is responsible for drawing the desktop background and it conflicts with XFCE's xfdesktop.

You can either prevent Nautilus form drawing any background, but this would mean that you have to stop having background in Unity either.

You can disable Nautilus and enable the Compiz Wallpaper plugin, I am not 100% sure if this will work.

Or the easiest would be to just not run Nautilus under xfce. You can now disable it by killing Nautilus from Apps -> System -> System Monitor.

---

### Post by new-to-ubuntoo on 2012-03-14
thanks a lot for that. all i do now is when i use xfce just kill the nautilus and back to what i want now.

thanks a lot :) that makes me happy

---

### Post by 3Miro on 2012-03-14
Glad to help and I guess delayed welcome to the forum.

If you have to kill Nautilus every time you login, you have to look at: Apps -> Settings -> Settings Manager -> Session, and then make sure Nautilus doesn't start at login.

Otherwise, keep an eye on which process starts Nautilus after login and see if you can change that. Killing nautilus too often is a hassle.

---

### Post by Bucky Ball on 2012-03-14
In Xfce you might find it in Apps>Settings>Xfce 4 Settings Manager>Sessions and Startup.

---

