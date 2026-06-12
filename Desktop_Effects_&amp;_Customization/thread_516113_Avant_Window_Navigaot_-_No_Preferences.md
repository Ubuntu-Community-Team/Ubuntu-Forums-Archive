---
title: "Avant Window Navigaot - No Preferences?"
date: 2007-08-02
forum: Desktop Effects &amp; Customization
---

### Post by chaser209 on 2007-08-02
I installed AWN from the Synaptic Package Manager, and it works great. But when I right click the bar and click preferences, I get nothing. Did I install it wrong? Do I need to run it from a terminal?

---

### Post by chaser209 on 2007-08-02
Anyone?

---

### Post by smartboyathome on 2007-08-02
Try opening it up in the terminal and seeing what you get when you try to open preferences.

---

### Post by chaser209 on 2007-08-02
How would I run it in the terminal?

---

### Post by chaser209 on 2007-08-02
Anyone? would like to change some preferences..

---

### Post by FuturePilot on 2007-08-02
Copy this into a terminal
```
avant-window-navigator
```

---

### Post by Kasper42 on 2007-08-16
Hi

I am also having similar problems with AWN, I have tried running avant-window-navigator in the terminal and the following appears when I right-click and select "Preferences" "Configure Launcher" or "Configure Applets":

```

:~$ avant-window-navigator
APPLET : /usr/local/lib/awn/applets/taskman.desktop
Failed to execute child process "avant-launchers" (No such file or directory)
Failed to execute child process "avant-preferences" (No such file or directory)
Failed to execute child process "avant-applets" (No such file or directory)
```

When I click "Preferences" "Configure Launcher" or "Configure Applets" nothing seems to appear or load.

I used this thread to install AWN [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

Thanks!

---

### Post by reacocard on 2007-08-16
what do you get if you enter this in the terminal?

```
avant-preferences
```

---

### Post by isaacj87 on 2007-08-16
> **reacocard said:**
> what do you get if you enter this in the terminal?

```
avant-preferences
```

I've used your Repo before to install the SVN version and the avant-preferences did not work. I suggest telling the original poster how to add your repo and to use the BZR version, not the SVN version. That might be the problem.

---

### Post by Kasper42 on 2007-08-16
@reacocard, 

```
:~$ avant-preferences
bash: avant-preferences: command not found

```

Thanks :)

---

### Post by reacocard on 2007-08-16
> **Kasper42 said:**
> @reacocard, 

```
:~$ avant-preferences
bash: avant-preferences: command not found

```

Thanks :)

huh, thats REALLY wierd. are you sure its installed from my repo? package anem should be avant-window-navigator-bzr and version should be something like 0.1.2-bzr34-1.

---

### Post by isaacj87 on 2007-08-16
> **reacocard said:**
> huh, thats REALLY wierd. are you sure its installed from my repo? package anem should be avant-window-navigator-bzr and version should be something like 0.1.2-bzr34-1.

I have your repo...and oddly enough I still have the option to install the SVN version...both BZR and SVN are there...should it not be like that?

---

### Post by reacocard on 2007-08-16
> **isaacj87 said:**
> I have your repo...and oddly enough I still have the option to install the SVN version...both BZR and SVN are there...should it not be like that?

no it shouldn't, I thought I deleted them. I guess I'll have to double-check that.

---

### Post by isaacj87 on 2007-08-16
OH! sorry, it was Trevino's Repo that the SVN was in...sorry...:oops:

---

### Post by Kasper42 on 2007-08-19
Sorry for taking so long to reply.

I did use your howto reacocard, I've no idea how I managed how to do what I did :confused:

Anyway, I now have both affinity and avant-window-navigator working :)

I uninstalled AWN by following the steps in your howto and then ran:

```
sudo apt-get install avant-window-navigator-bzr
```

(using the repository and the key from your howto) I could then run AWN fine including preferences :)

---

### Post by superyounan1 on 2007-08-27
I have the same problem, i need to uninstall AWN but i got rid of the source. I tried redownloading it and running "sudo make uninstall", but it didnt work, "no hit target", somethign along those lines

---

