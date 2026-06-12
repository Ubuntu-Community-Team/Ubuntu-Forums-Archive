---
title: "Gnome on Xubuntu?"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Banyon on 2006-07-10
**UPDATED**

Well, I just got Xubuntu installed, its nice, but I would still like to have gnome for certain things.

I opened up all the repositories in my sources.list, and I did the following

sudo aptitude update
sudo aptitude install ubuntu-desktop

Gives me this error/prompt half way into it.

```
Need to get 322MB/326MB of archives. After unpacking 1016MB will be used.
The following packages have unmet dependencies:
  xubuntu-system-tools: Conflicts: gnome-system-tools but 2.14.0-0ubuntu11 is to be installed.
  evince-gtk: Conflicts: evince but 0.5.2-0ubuntu3 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
bluez-pcmcia-support [Not Installed]
bsh [Not Installed]
evince [Not Installed]
gnome-system-tools [Not Installed]
openoffice.org [Not Installed]
openoffice.org-base [Not Installed]
openoffice.org-evolution [Not Installed]
openoffice.org-java-common [Not Installed]
openoffice.org-writer [Not Installed]
pcmcia-cs [Not Installed]
ubuntu-desktop [Not Installed]

Score is 93

Accept this solution? [Y/n/q/?]
```

I said yes... it finished without errors, but no install screen and gnome is not avalible.

Thanks for any help.

---

### Post by orb9220 on 2006-07-10
use the package manger for KDE I think its aptitude or something.

It will solve the dependcies issues.

never install a window manger by term unless you know you have all the others packages installed allready.

usally the are multiple apt-get installs for mangers.

Hope this helps some from ](*,)

---

### Post by Dr. Nick on 2006-07-10
aptitude is good when installing appliations with many dependencies especially, usinhg apt-get will work just fine to install aswell, but with apt-get it is difficult to get all the packages removed, aptitude remembers all it installed so it can remove it easier

More info on apt-get vs aptitude  [http://www.psychocats.net/ubuntu/aptitude.php](http://www.psychocats.net/ubuntu/aptitude.php)

Their wont really be a install screen, how are you trying to get gnome? you need to change "session" at the login screen to gnome.

---

### Post by detrate on 2006-07-11
log out.  At the login screen you should see and option for 'session' select gnome from the list and log back in.

---

### Post by encho on 2006-07-11
> **Banyon said:**
> 
While people are here that know about XFCE, is there a way to make CTRL+ALT+DEL bring up the XFCE taskmanager like in Windows?

Go to menu>settings>keyboard settings, <shortcuts> tab.

Click 'Add' to add new theme than click another 'Add' to add shortcut. Choose 'xfce4-taskmanager' as the application and than just press required key combination.

---

### Post by Banyon on 2006-07-11
I am logging out then back it, it doesn't appear to have installed Gnome correctly because I don't have it avalible to me under sessions.

I followed the tut at psychocats to install gnome, but mine came up with that extra prompt telling him it couldn't update some packages or something and asked me "If this solution is acceptable y/n/g".

The tutorial was ment for Kubuntu users... maybe Xubuntu is missing something it really needs?

---

### Post by Dr. Nick on 2006-07-11
make sure gdm is installed, I am not sure which login manager you are using.

sudo aptitude install gdm

---

### Post by srunni on 2006-07-11
The way I did it, I got Ubuntu, then added the package kubuntu-desktop. Now,  I can select between Gnome and KDE right before I log in. The same thing would probably work with Gnome and XFCE.

---

### Post by Banyon on 2006-07-12
This is the error I get while installing... what should I do?

```
Need to get 322MB/326MB of archives. After unpacking 1016MB will be used.
The following packages have unmet dependencies:
  xubuntu-system-tools: Conflicts: gnome-system-tools but 2.14.0-0ubuntu11 is to be installed.
  evince-gtk: Conflicts: evince but 0.5.2-0ubuntu3 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
bluez-pcmcia-support [Not Installed]
bsh [Not Installed]
evince [Not Installed]
gnome-system-tools [Not Installed]
openoffice.org [Not Installed]
openoffice.org-base [Not Installed]
openoffice.org-evolution [Not Installed]
openoffice.org-java-common [Not Installed]
openoffice.org-writer [Not Installed]
pcmcia-cs [Not Installed]
ubuntu-desktop [Not Installed]

Score is 93

Accept this solution? [Y/n/q/?]

```

---

### Post by Banyon on 2006-07-12
Anyone?

---

### Post by Dr. Nick on 2006-07-12
What were you trying to install?

I havent seen that happen before, but it doesnt look like a huge deal, does it say its going to remove anything that you need?

---

### Post by Banyon on 2006-07-12
> **Dr. Nick said:**
> What were you trying to install?

I havent seen that happen before, but it doesnt look like a huge deal, does it say its going to remove anything that you need?

That is the prompt I get when trying to install Gnome on Xubuntu 6.06

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

Gives me that prompt I post about half way through the install.

---

### Post by Dr. Nick on 2006-07-12
I think what is going to happen is the gnome system tools are going to overwrite the xubuntu ones if you accept it. I dont know what happens when you install gnome over xubuntu, ive only installed xubuntu over gnome. 

When I do stuff like this I just ususally make sure something like Xorg isnt going to be removed. I usually feel safe as long as nothing is removed. Hopefullt someone who has installed gnome 2nd can help here.

---

### Post by Banyon on 2006-07-12
> **Dr. Nick said:**
> I think what is going to happen is the gnome system tools are going to overwrite the xubuntu ones if you accept it. I dont know what happens when you install gnome over xubuntu, ive only installed xubuntu over gnome. 

When I do stuff like this I just ususally make sure something like Xorg isnt going to be removed. I usually feel safe as long as nothing is removed. Hopefullt someone who has installed gnome 2nd can help here.

Well, it didn't work the first time, so I logged out, and hit CTRL+ALT+F1 and did it via console.... seems to have worked.

I'm on Gnome right now.

---

