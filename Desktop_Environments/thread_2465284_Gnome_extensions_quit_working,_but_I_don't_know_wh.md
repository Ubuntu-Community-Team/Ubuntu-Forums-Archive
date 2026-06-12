---
title: "Gnome extensions quit working, but I don't know when."
date: 2021-07-28
forum: Desktop Environments
---

### Post by irv on 2021-07-28
First, I have read through other threads to see if there was a fix for this but didn't find one.
It has been a while since I added Gnome extensions so I am not sure what is going on. Maybe I should mention that I have upgraded from 20.04 to 20.10 to 21.04, and that is where I am right now. I have Gnome Tweek-Tools installed and it shows the extensions I have already installed. I have made sure that 
```
chrome-gnome-shel
```
and 
```
gnome-shell-extensions
```
are installed and that I have the Extensions added to Chrome and Firefox, but when I go to
[https://extensions.gnome.org/#sort=popularity]("https://extensions.gnome.org/#sort=popularity") I don't have the buttons to install or configure the gnome extensions.
I have tried installing and reinstalling the above mention, plus restarting the shell, and even rebooting after trying everything, but nothing works.
Any idea what to try next?

---

### Post by tea for one on 2021-07-28
There is an on/off toggle for all extensions within gnome-tweaks.

Open gnome-tweaks > Extensions > Slider (towards top right)

---

### Post by Dennis N on 2021-07-28
> I don't have the buttons to install or configure the gnome extensions.
Things have changed. You don't configure extensions through tweaks any longer. Instead, search for "Extensions" (see screen shot). That's where the activation and configuration is done now.

---

### Post by irv on 2021-07-28
In answer to both questions, yes and yes. I see both and use both, but I still can not install extensions. 
[http://wabasha-server.net/photos/Gnome%20Estensions%20screen.png](http://wabasha-server.net/photos/Gnome%20Estensions%20screen.png)

---

### Post by deadflowr on 2021-07-28
Does the chrome-gnome-some-dome-whatever-shell work in Ubuntu's chromium?
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1741074]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1741074")

---

### Post by tea for one on 2021-07-28
Your image implies that your gnome-shell integration is not recognising the extensions.gnome.org site.

In your first post, there was a small typo - shel instead of shell

Perhaps check if it is still installed:-

```
sudo apt install chrome-gnome-shell
```

---

### Post by Dennis N on 2021-07-28
> **irv said:**
> In answer to both questions, yes and yes. I see both and use both, but I still can not install extensions. 
[http://wabasha-server.net/photos/Gnome%20Estensions%20screen.png](http://wabasha-server.net/photos/Gnome%20Estensions%20screen.png)
You're right - I see it in tweaks too - at least for now. I have read that option in tweaks is going to be removed. To answer the failure to install, the Extensions tool won't do that yet. It will remove an extension however if you click the arrow to the right of the extension name, that option is exposed. To install, a lot of extensions are in the Ubuntu repository - just install as any other package. If it's not there, you have to install with Firefox from the extensions web site. You need the "gnome-shell integration" Firefox extension and the package chrome-gnome-shell as instructed at the top of the page in your image. If these are already installed, the instructions wouldn't be shown. If you use Chromiun snap or Firefox snap or flatpak, then this won't work. You have to download the extension package and manually install it.

---

### Post by irv on 2021-07-29
I am going to mark this solved and what I ended up doing was redoing two computers this morning by wiping them and doing a fresh install on both with POP OS. System 76 OS.
It is basically Ubuntu with a custom Gnome desktop. I made it easy to do this with a script I wrote to reinstall all my software with one command. I do both computers in about an hour and a half. 
These were my two desktops so now all I have to do is my laptops, I have two of them as well. Tomorrow is another day.

---

