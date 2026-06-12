---
title: "Unity on 18.04"
date: 2018-12-10
forum: Desktop Environments
---

### Post by speartip on 2018-12-10
Can anyone tell me if they're using Unity on top of the Ubuntu Gnome desktop?
How stable is it? And are there any specifics that need addressing?
The reason I ask is that Compiz has always been the best window manager for my Desktop (Intel i3 550 Processor with integrated Intel Ironlake Graphics) 
All other WMs seem glitchy, & not as smooth, KDE being the exception. At present I use Mate for that reason, but am thinking of going back to Unity.
Any observations would be appreciated.

---

### Post by CatKiller on 2018-12-10
If it worked, or if it had problems, for anyone else, that wouldn't say much about how it would work on your system.

Since it worked well for you before and you seem to prefer it, give it a try. It's just logging out and logging in again if you don't like it. There's a widget on the login screen next to your username to say which Desktop Environment you want to log in to.

---

### Post by oldrocker99 on 2018-12-10
Bear in mind that MATE Tweak, in the Panel tab, in the Panels section on top, there are several panel layouts to select. The one you want is called Mutiny, which is very close to Unity:cool:, with its unique features. No need to reinstall or install another desktop.:D

Good luck!

---

### Post by ajgreeny on 2018-12-10
If you do go ahead and install the unity desktop, make a list of all the dependency packages that are brought in with it.

Doing so means that if you can not get it working as you want, and thus want to remove it, you can do so with a single command ```
sudo apt purge packagenames
```

---

### Post by Ars_Ivci on 2018-12-10
I tried Unity on both 18.04 and 19.10 without any problems. Because I have a very old computer, 16.04 performed better than those (running 16.04 now). You have an i3 processor so you will not have little performance issues like me (2xCeleron b830 @1.80Ghz).

Still, 18.04's layout/flow is hardly any different than Unity but you should know better.

---

### Post by speartip on 2018-12-10
Thanks for your comments.
I forgot to mention the "Mate" I'm using is Linux Mint, which I dual boot with KDE Neon. However I might install Ubuntu Gnome over it, & add Unity. I always have Neon as a Backup. I just wanted to see how others had found Unity, now it's not an official Ubuntu flavour.

---

### Post by mc4man on 2018-12-10
Works fine here. You should install via the meta package
```
sudo apt install ubuntu-unity-desktop
```
(- if any packages are added you don't want then remove after..

If on a laptop also install 
```
sudo apt install xserver-xorg-input-synaptics
```

During initial install there should be a prompt to switch to lightdm, do so.  (when installing on default Ubuntu 18.04.x

This ppa has a few updated packages - 
[https://launchpad.net/~unity7maintainers/+archive/ubuntu/unity7-desktop?field.series_filter=bionic](https://launchpad.net/~unity7maintainers/+archive/ubuntu/unity7-desktop?field.series_filter=bionic)

Comments,info,  ect. here - 
[https://discourse.ubuntu.com/t/testing-unity-session-in-18-04/987](https://discourse.ubuntu.com/t/testing-unity-session-in-18-04/987)

If keeping you can then remove gdm3, gnome-shell, ect.

Pretty much everything works fine, alt+print probably not, workarounds available.

If using a 4x1 workspace setup (cube/rotate preferred ) then I've a modded unity here
[https://launchpad.net/~mc3man/+archive/ubuntu/unityplus](https://launchpad.net/~mc3man/+archive/ubuntu/unityplus)

---

### Post by speartip on 2018-12-11
Thanks mc4man, that was the type of info I was looking for.
When I get a spare hour or 2 I will give it a go & report back.

---

### Post by Randymanme on 2018-12-13
> **mc4man said:**
> Works fine here. You should install via the meta package
```
sudo apt install ubuntu-unity-desktop
```
(- if any packages are added you don't want then remove after..

If on a laptop also install 
```
sudo apt install xserver-xorg-input-synaptics
```

During initial install there should be a prompt to switch to lightdm, do so.  (when installing on default Ubuntu 18.04.x

This ppa has a few updated packages - 
[https://launchpad.net/~unity7maintainers/+archive/ubuntu/unity7-desktop?field.series_filter=bionic](https://launchpad.net/~unity7maintainers/+archive/ubuntu/unity7-desktop?field.series_filter=bionic)

Comments,info,  ect. here - 
[https://discourse.ubuntu.com/t/testing-unity-session-in-18-04/987](https://discourse.ubuntu.com/t/testing-unity-session-in-18-04/987)

If keeping you can then remove gdm3, gnome-shell, ect.

Pretty much everything works fine, alt+print probably not, workarounds available.

If using a 4x1 workspace setup (cube/rotate preferred ) then I've a modded unity here
[https://launchpad.net/~mc3man/+archive/ubuntu/unityplus](https://launchpad.net/~mc3man/+archive/ubuntu/unityplus)

I just installed Unity with synaptic package manager about 30 minutes ago and I couldn't believe how sorry it looked and ran.  I promptly uninstalled it.  Something told me to try it out on Ubuntu before putting it on Mint.  Nonetheless, I'll try it again with your directions.  And it that doesn't do it for me, I'll just replace 18.04 with 16.04.

---

### Post by Randymanme on 2018-12-13
> **mc4man said:**
> Works fine here. You should install via the meta package
```
sudo apt install ubuntu-unity-desktop
```

If using a 4x1 workspace setup (cube/rotate preferred ) then I've a modded unity here
[https://launchpad.net/~mc3man/+archive/ubuntu/unityplus](https://launchpad.net/~mc3man/+archive/ubuntu/unityplus)

Thank you veery much; installing " . . . via the meta package . . ." did the trick for me.

So what do I do after adding your modded Unity ppa to get the mods running?

---

### Post by mc4man on 2018-12-13
> **Randymanme said:**
> Thank you veery much; installing " . . . via the meta package . . ." did the trick for me.

So what do I do after adding your modded Unity ppa to get the mods running?
Not sure what you mean. Only some minor changes - 
> * Adjust expo icon for 4x1 ws, pattern is
    12
    34

So if you have a 4x1 workspace setup then when switching ws the expo in unity launcher will reflect. In the default unity the expo icon only works with with a 2x2 setup. 
(- this is hardcoded so witth ppa unity it'll only work with 4x1 ws setup..

> * Re-enable systray
There are still a few apps that only have systray support vs app indicator.  So change is only relevant if you  happen use one of them..

> * Set window group spread to ctrl+alt+z for single hand use.
By default the key binding for window group spread from all workspaces requires using both hands or fairly awkward single hand  (ctrl+super+shift+w), this changes to ctrl+alt+z which is easily done with left hand 

> Additionally in 18.04
  * Set launcher side/top White line to Black (no apparent border with many background images..
I use a medium toned background so the white border on unity launcher is useless/out of place, so changed to black which here is pretty much invisible

So really just a few minor changes meant mainly for cube/rotate users

---

