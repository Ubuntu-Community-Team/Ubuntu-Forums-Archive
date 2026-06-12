---
title: "Can't login after enabling system sounds"
date: 2015-02-03
forum: Desktop Environments
---

### Post by ManyBeers on 2015-02-03
Hi. 
OS=Xubuntu 14.04 xfce session.
Anyways following instructions from [This guide post#2]("http://ubuntuforums.org/showthread.php?t=2156763&highlight=system+sounds"), except step#1 my password is no longer accepted at the login prompt and I am locked out of my machine. Anybody know why?

---

### Post by Illydth on 2015-02-03
There's nothing there that changes the way the login prompt hashes/manages your password.  WHile I hate to suggest you might have mis-typed your password, that is what everything indicates at this point.

You can try to 'unset' the settings you did though that guide post (looks like edits to several files) but it's unlikely that's going to get you fixed.  I assume SUDO is throwing the same error at you as login is?  (assuming of course you even have a prompt you can get to)

Assuming this is your main administrative account, you're probably looking at loading a recovery CD, mounting the root partition, making sure /etc is loaded, and forcing a passwd on your user account to change the password...at which point you should be back good to go.

--Illydth

---

### Post by ManyBeers on 2015-02-03
> **Illydth said:**
> There's nothing there that changes the way the login prompt hashes/manages your password.  WHile I hate to suggest you might have mis-typed your password, that is what everything indicates at this point.

You can try to 'unset' the settings you did though that guide post (looks like edits to several files) but it's unlikely that's going to get you fixed.  I assume SUDO is throwing the same error at you as login is?  (assuming of course you even have a prompt you can get to)

Assuming this is your main administrative account, you're probably looking at loading a recovery CD, mounting the root partition, making sure /etc is loaded, and forcing a passwd on your user account to change the password...at which point you should be back good to go.

--Illydth

Thanks for the response. I uused the Guest account to get to a session and C+Alt+f1 logged into my account  startx and I am currently at my desktop
So my account and password still function I guess? I am trying to undo everything I did in that guide. So far I have removed the /.xprofile file from my user folder. And am now trying to get rid of this file=52libcanberra-gtk3-module_add-to-gtk-modules which is owned by root even though I created it. Any suggestions? By the way I'm 
afraid to shutdown and reboot though I could go the same route I just did.

---

### Post by Illydth on 2015-02-03
So you did manage to get back into your account via a normal login.  Ok, so now what's the difference between where you cannot get logged in and where you can?

It sounds like your password is properly accepted at the Console login prompt, but maybe not accepted in the Visual/graphical login prompt?  That would be wierd.  More details here?

I don't think I'd reboot at this point, though so long as you can get in via your main admin account in a console based session you should be fine to reboot...nothing's been permanently damaged.

Remember that you do have "sudo" capabilities so long as you're logged into your main admin account...in other words, you can "sudo su -" or "sudo <somecomand>" to run as root, so permissions problems should not be an issue for you.

It will prompt you for your account password, but that is your account password, not root's password.

--Illydth

---

### Post by ManyBeers on 2015-02-03
> **Illydth said:**
> So you did manage to get back into your account via a normal login.  Ok, so now what's the difference between where you cannot get logged in and where you can?

It sounds like your password is properly accepted at the Console login prompt, but maybe not accepted in the Visual/graphical login prompt?  That would be wierd.  More details here?

I don't think I'd reboot at this point, though so long as you can get in via your main admin account in a console based session you should be fine to reboot...nothing's been permanently damaged.

Remember that you do have "sudo" capabilities so long as you're logged into your main admin account...in other words, you can "sudo su -" or "sudo <somecomand>" to run as root, so permissions problems should not be an issue for you.

It will prompt you for your account password, but that is your account password, not root's password.

--Illydth

Everything is fine right now.I have deleted both those files I created via that tutorial. My system is booting normally now.  I've  put system sounds on hold for now and will concentrate on getting hibernate to work on this netbook. It worked fine on 12.04.

---

### Post by Toz on 2015-02-03
Just came across this thread.
I wonder whether something was wrong in the .xprofile file. An bad one might cause an error aborting the login process. The tutorial should still work, but instead of adding the startup sound file to .xprofile, perhaps it would be better to add it to your startup applications (Settings Manager >> Session and Startup >> Application Autostart) where it shouldn't affect the system login process as it might possibly do. I'll edit that original post to change that information.

---

### Post by ManyBeers on 2015-02-03
> **Toz said:**
> Just came across this thread.
I wonder whether something was wrong in the .xprofile file. An bad one might cause an error aborting the login process. The tutorial should still work, but instead of adding the startup sound file to .xprofile, perhaps it would be better to add it to your startup applications (Settings Manager >> Session and Startup >> Application Autostart) where it shouldn't affect the system login process as it might possibly do. I'll edit that original post to change that information.

     Oh hey thanks for stopping by. Would you help me get system sounds working on my Netbook. Xubuntu14.04 Xfce session(always). Pretty much stock. 
I've installed Xfcegoodies, the mp3 codec package, Gparted. That's about it. Sound works as I can play mp3's with Gmusic browser. I;m ready anytime.

---

### Post by Toz on 2015-02-03
Okay. I just ran through the same steps on a new Xubuntu 14.04.02 pre-release install and these worked for me (I changed some of the original steps to make it easier and made all instructions command-line based to save on time).

1. Install some required packages:
```
sudo apt-get install gnome-session-canberra sox
```

2. Download: [https://www.dropbox.com/s/bfyk05r4y8qog2c/usr_share_sounds_borealis.tar.gz](https://www.dropbox.com/s/bfyk05r4y8qog2c/usr_share_sounds_borealis.tar.gz) (this is a modified [Borealis]("http://xfce-look.org/content/show.php?content=12584&forumpage=7&PHPSESSID=6") sound theme).

3. Extract the file:
```
cd ~/Downloads
tar xzvf usr_share_sounds_borealis.tar.gz
```

4. Copy the contents to your sounds directory:
```
sudo cp -rv usr/share/sounds/Borealis /usr/share/sounds
```

5. Enable sounds:
```
xfconf-query -c xsettings -p /Net/EnableEventSounds -s true
xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds -s true
```

6. Set the default sound theme:
```
xfconf-query -c xsettings -p /Net/SoundThemeName -s "Borealis"
```

7. Setup the necessary environment variable. Add to the end of **~/.profile**:
```
GTK_MODULES="$GTK_MODULES:canberra-gtk-module"
export GTK_MODULES
```

8. For a startup sound, create a new autostart application (Settings Manager >> Session and startup >> Application autostart) with the following parameters:
> - Name = Login Sound
- Command = canberra-gtk-play -f /usr/share/sounds/Borealis/stereo/Startup1_1.ogg

9. For logout sound, you need override xfce4-session. To do so, _with root privliges_, create the file **/usr/local/bin/xfce4-session** with the following content:

```
#!/bin/bash

# run the real xfce4-session executable
/usr/bin/xfce4-session

# on exit, run my stuff
canberra-gtk-play -f /usr/share/sounds/Borealis/stereo/Exit1_2.ogg
```

...and make this file executable:
```

sudo chmod +x /usr/local/bin/xfce4-session
```

10. Log out and back in again and check (clicking on the clock plugin should generate a click. Minimize/maximize windows should also "zap"). You may need to increase the "System Sounds" volume in your Sound Settings.


Notes:
[LIST]
[*]Event sounds are a GTK thing - not an Xfce thing (Xfce is built using the GTK toolkit).
[*]The [canberra project]("http://0pointer.de/lennart/projects/libcanberra/") extends GTK sound events to provide an interface to them (you use the canberra binaries and modules to play sound events).
[*]Xfce simply provides an interface to enable or disable them.
[*]Any problems with event sounds should really be directed towards GTK or canberra. For example, only certain events are supported by canberra:
> /*
We generate these sounds:
dialog-error
dialog-warning
dialog-information
dialog-question
window-new
window-close
window-minimized
window-unminimized
window-maximized
window-unmaximized
notebook-tab-changed
dialog-ok
dialog-cancel
item-selected
link-pressed
link-released
button-pressed
button-released
menu-click
button-toggle-on
button-toggle-off
menu-popup
menu-popdown
menu-replace
tooltip-popup
tooltip-popdown
...and even some of them don't work.
[*]The Borealis sound theme from above was put together from an existing sound theme where I changed the filenames to better match up with the canberra implementation.
[/LIST]

---

### Post by ManyBeers on 2015-02-04
ok thanks /I'm on it

---

### Post by ManyBeers on 2015-02-04
Ok #7 do I just run that code or is it to br appended to that /.profile file?.

---

### Post by Toz on 2015-02-04
> **ManyBeers said:**
> Ok #7 do I just run that code or is it to br appended to that /.profile file?.

Append those two lines to the end of that file.

---

### Post by ManyBeers on 2015-02-04
THat file is the one in my Home folder correct?

One othr thing that 1st command returned. Evidentally it is alreasdy installed.
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-session-canberra is already the newest version.
sox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

Anyways I have done everything except the logout sound. I have checked the Auto Start entry and ther is an entry
for Login sound and Indicator sound. Xsetttings are also correct.
I just heard a pop!pop! sound when I adjusted the output volume of Pulse Audio's mixer.

---

### Post by ManyBeers on 2015-02-05
Toz Thanks for the help all sounds are working. The Login Sound Command I copied and pasted that Verbatim...well I t took me a while to realize '
 -Command= is not necessary or part of the actual command.

---

