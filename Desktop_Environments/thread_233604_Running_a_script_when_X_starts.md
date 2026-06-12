---
title: "Running a script when X starts"
date: 2006-08-10
forum: Desktop Environments
---

### Post by kreso on 2006-08-10
How can I run a shell command when X starts?

I tried looking for .xsession in my home dir but there wasn't any. I made one, but it doesn't get read.

---

### Post by Paerez on 2006-08-10
try using a .xinitrc file instead.

---

### Post by kreso on 2006-08-11
Nope, didn't do it :(

do I have to tell X which file to load or smtg?

---

### Post by Paerez on 2006-08-11
it should check your .xinitrc. Are you using gnome or kde? Because they each have a way of running things when the session starts, and it will be much friendlier.

---

### Post by frodon on 2006-08-11
What do you mean by "when X starts" ?

There's a difference between a session script which is run when you start your session (once you login through GDM or KDM) and a init.d script which is run on bootup (before the GDM or KDM screen).

If what you're looking for is how to set up a session script it depends of the desktop you use (GNOME, KDE or XFCE).

For example if you use GNOME you just have to go to System > Preferences > session then once the apps opened you will see a tab where you can set commands/script to run on GNOME startup, here is the wiki page :
[https://help.ubuntu.com/community/AddingProgramToSessionStartup](https://help.ubuntu.com/community/AddingProgramToSessionStartup)

---

### Post by kreso on 2006-08-11
Sorry, I should have been more specific:

I'm using the latest XFCE beta, and I would like to run a script when X is initialized, before GDM is loaded.

---

### Post by frodon on 2006-08-11
Ok, to run a script on boot do as follow :

1- create a script with the commands you want to laucnch and put it in /etc/init.d
2- make the script executable : ```
sudo chmod +x /etc/init.d/*name_of_script*
```
3- create the rc.d links with this command : ```
sudo update-rc.d *name_of_script* defaults
```
4- reboot

that's all :)

---

### Post by kreso on 2006-08-11
Ok, I'll try, but are you sure that the srcipt gets exectued after X startup? because this script is dependant on X.

---

### Post by kreso on 2006-08-11
what I want to do is setup xmodmap to change some of my keyboard functunalities, but I have to do it before XFCE starts, and after X starts.

---

### Post by frodon on 2006-08-11
oups sorry i beleived you said before X startup, what i wrote is to start a script before x startup and not after.

Go in /usr/share/xsessions/ and find the .desktop file for xfce, in the desktop file look at the "Exec=" parameter it specify the path of the session script used by xfce.
Just put your xmodmap command in this script.

---

### Post by paperdiesel on 2006-08-18
> **frodon said:**
> oups sorry i beleived you said before X startup, what i wrote is to start a script before x startup and not after.

Go in /usr/share/xsessions/ and find the .desktop file for xfce, in the desktop file look at the "Exec=" parameter it specify the path of the session script used by xfce.
Just put your xmodmap command in this script.

What if we want to do the exact same thing, but with KDE?  I want to run xmodmap to change some of my keyboard settings, but I don't know how to get the xmodmap command to run automatically when I start up kde.

---

