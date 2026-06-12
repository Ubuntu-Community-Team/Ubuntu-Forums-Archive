---
title: "Gnome Help"
date: 2009-01-20
forum: Desktop Environments
---

### Post by AaronJoseph on 2009-01-20
I installed Ubuntu on my laptop but the screen seems "too" big. When I minimize a window it vanishs, like I have no bottom menu and the top menu goes to far past my screen. Is there a way to zoom in so the screen appears smaller so everything fits in my laptop's screen? 

Also, can I download the KDE desktop and switch between the two without having to install Kubuntu with the default Ubuntu?

---

### Post by taurus on 2009-01-20
If you want to run KDE, just install the kubuntu-desktop package.  Then, you can choose which DE you want to run at the GUI login screen, bottom left corner.

```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by mick222 on 2009-01-20
check in system -> preferences-> screen resolution to change your settings.
You can install the Kde desktop either as above or through synaptic package manager, if you prefer to use the gui. Only problem is Kde apps will showup in the gnome menu and visa versa, which can look a bit clutterd.

---

### Post by AaronJoseph on 2009-01-20
I tried changing the screen resolution but when I did it messed up. The screen became blurry and it made everything appear 4 times...like there were four mouse arrows, etc....

It also says "Unknown" on the sample screen. Every one I pick makes the screen way big or way small and all blurry. I ran the Live CD on my brother's laptop and it did not say "unknown." It said "Laptop 15'". Why doesn't mine pick up my screen size?

---

### Post by Ludachrispeed on 2009-01-21
Are there buttons on your monitor you can use to resize the visible area?  I had to do that when I first hooked up my monitor with linux.

Also, I don't know what graphics card and whatnot you have, but if it's nvidia, you can do some cool stuff with

```
nvidia-settings
```

which will bring up a nice gui... go to "X Server Display Configuration" to check out the resolution there.

---

### Post by AaronJoseph on 2009-01-21
> **Ludachrispeed said:**
> Are there buttons on your monitor you can use to resize the visible area?  I had to do that when I first hooked up my monitor with linux.

Also, I don't know what graphics card and whatnot you have, but if it's nvidia, you can do some cool stuff with

```
nvidia-settings
```

which will bring up a nice gui... go to "X Server Display Configuration" to check out the resolution there.

There are no buttons on my laptop to change screen size..only brightness. I will try that code out. I don't know what else to do. Even the login screen is too far down, so I can only see where you type your username and after you hit enter the password box and thats it. 

The bottom menu on the desktop won't show up and the top menu goes to far to the right...so i cannot see it all.

---

### Post by AaronJoseph on 2009-01-21
Anyone know how I can fix this?

---

### Post by AaronJoseph on 2009-01-21
I am completely new to linux, so can anyone explain a former Windows user how to fix this problem? Please.

---

