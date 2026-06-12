---
title: "why did they remove desktop icons from ubuntu 20.04"
date: 2020-07-09
forum: Desktop Environments
---

### Post by mickee384 on 2020-07-09
I understand they are gone and that you can enable desktop icons with Gnome extensions, but I  can't put sym links etc there, Just wanted to know what people use the desktop for? I use mine currently to have shortcuts to well used folders, and internet shortcuts. A person who shares my pc, is definitely and point and click person.

---

### Post by mickee384 on 2020-07-09
I use the desktop also for housing temporary files I am needed to be reminded of and the extension does that. Just wish I could have "short cuts" to files and folders and internet links. I just don't understand why Gnome would remove the functionality? Maybe I just don't get the issues with the old desktop?

---

### Post by mc4man on 2020-07-10
If you want full control of Desktop back (or close to) then install & use something else to handle the Desktop.
One example - nemo

```
sudo apt install nemo
```
```
sudo apt purge gnome-shell-extension-desktop-icons
```

For local user only
```
gedit .config/autostart/nemo-autostart.desktop
```

For system wide 
```
sudo -H gedit /etc/xdg/autostart/nemo-autostart.desktop
``` 

Insert this as contents of file, save, log out/in, becomes active 2 sec after login
```
[Desktop Entry]
Type=Application
Name=Nemo Desktop
Comment=Start Nemo desktop at log in
Exec=nemo-desktop
AutostartCondition=GSettings org.nemo.desktop show-desktop-icons
X-GNOME-AutoRestart=true
X-GNOME-Autostart-Delay=2
NoDisplay=false
```

To revert is obvious, remove from startup applications, purge nemo, autoremove, install that extension, log out/in

---

### Post by mickee384 on 2020-07-13
cool. I will try this after upgrading to 20.04. Thanks!

---

### Post by monkeybrain20122 on 2020-07-13
I don't use the desktop. I use unity on 20.04 and use the dash in place of the desktop to show frequently used files and applications (it is much better than gnome's) Another computer has Kubuntu20.04 which also has a dash for the same purpose (though not as good as unity's), I just put a link to the file manager on the desktop. I hate littering my desktop with launchers and icons like Windows, I keep mine pristine and clean.

I find it kind of interesting that people who insist on having a classic menu are also the same people who put app launchers all over the desktop, which basically says that the menu is kind of useless and cumbersome.

---

### Post by ajgreeny on 2020-07-13
I used to use desktop icons/launchers for my most used applications when I was using gnome 2, but when unity appeared on the scene, which I did not like, I moved all my systems to Xubuntu.

For a short time using Xubuntu I also used desktop icons, but then realised how incredibly simple and time saving it is to create a second autohidden panel, which I use as a dock, without the need to install any specific "dock" package. In that panel are just launchers for my most used applications and the Action-Buttons applet (Shutdown, Reboot, Logout, Suspend icons).

It makes for a good looking, clean desktop which I now use for two separate conky displays, each with useful system information showing.

---

### Post by mickee384 on 2020-07-14
cool.

---

### Post by mickee384 on 2020-07-17
I wonder if there is a way to request the desktop back in ubuntu 20.04? I am going to be dealing with this until 22.04 unless we can convince them to bring it back in one of the dot versions of 20.04. Like I said before, I don't really use it as I use a dock and super key, but the other user of my pc is really a luddite (He still uses a flip phone!) and he really can only click on icons. I am going to try to teach him to use the bookmarks in Firefox, but that may be a losing battle. Still don't know the real reason they removed it. All other OS's have a working desktop. I am experimenting  with creating a folder in my home dir that has all his old desktop shortcuts in it and put a link to that on the desktop, but I am having difficulties as some of the links only open a config file when accessed from places other than the actual desktop. I am going to use Gnome Extension for "Desktop Icons" but that seems to only work with files, not internet links like the full desktop experience in 18.04... and I really don't want to switch from Gnome to Unity as a DE. I love Gnome!

---

### Post by mickee384 on 2020-07-18
I may have figured out a work around. I created a folder in home and put the old desktop shortcuts in there, then made a link and put that on the desktop. Will see if that works good enough

---

### Post by deadflowr on 2020-07-18
> I wonder if there is a way to request the desktop back in ubuntu 20.04? I am going to be dealing with this until 22.04 unless we can convince them to bring it back in one of the dot versions of 20.04. 

You'd file a bug, but it would more than likely be marked as WON'T FIX.
(if bugs haven't already been filed for it and already marked won't fix)

> Still don't know the real reason they removed it. 

I had a long post on why, but I think this gives a better, more concise reasoning from the developers point of view:
[https://csorianognome.wordpress.com/2017/12/21/nautilus-desktop-plans/]("https://csorianognome.wordpress.com/2017/12/21/nautilus-desktop-plans/")

---

### Post by mickee384 on 2020-07-23
Thanks. I see the issues now.

---

### Post by walts48 on 2020-08-29
> **monkeybrain20122 said:**
> I don't use the desktop. I use unity on 20.04 and use the dash in place of the desktop to show frequently used files and applications (it is much better than gnome's) Another computer has Kubuntu20.04 which also has a dash for the same purpose (though not as good as unity's), I just put a link to the file manager on the desktop. I hate littering my desktop with launchers and icons like Windows, I keep mine pristine and clean.

I find it kind of interesting that people who insist on having a classic menu are also the same people who put app launchers all over the desktop, which basically says that the menu is kind of useless and cumbersome.

I put apps launchers on the desktop because I support release, and beta versions of Firefox and Thunderbird. Also use the Nightly version of Firefox, so I need a launcher for each.

I'm still using Ubuntu 18.04 LTS, but can dual boot into 20.04 and test those apps by launching them from a terminal.

That will get very old and tedious when/if I update 18.04 to 20.04. I'd like desktop launchers and will try the steps provided by mc4man.

---

