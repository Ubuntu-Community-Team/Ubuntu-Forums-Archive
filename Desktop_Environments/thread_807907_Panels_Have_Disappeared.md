---
title: "Panels Have Disappeared"
date: 2008-05-26
forum: Desktop Environments
---

### Post by arcelios on 2008-05-26
I logged into Ubuntu today, to find both my panels gone. I have restarted about ten times (no, I'm not kidding), to no avail. Please, someone help.

---

### Post by Inferied on 2008-05-26
Try this in terminal:
```
gnome-panel
```

---

### Post by arcelios on 2008-05-26
> **Inferied said:**
> Try this in terminal:
```
gnome-panel
```

I tried that, and I got this output:

```

Cannot open display:
Run 'gnome-panel --help' to see a full list of available command line options.

```

Please help :(

---

### Post by arcelios on 2008-05-26
Please, I am unable to do anything on Ubuntu while the panels are gone.

---

### Post by SkonesMickLoud on 2008-05-26
Does

```
killall gnome-panel
```

do anything?

If not, try removing and reinstalling gnome-panel:

```

sudo apt-get remove gnome-panel
sudo apt-get install gnome-panel

```

---

### Post by arcelios on 2008-05-26
> **SkonesMickLoud said:**
> Does

```
killall gnome-panel
```

do anything?

If not, try removing and reinstalling gnome-panel:

```

sudo apt-get remove gnome-panel
sudo apt-get install gnome-panel

```

I put in 
```
killall gnome-panel
```
but I got this out:
```
gnome-panel: no process killed
```
I tried the second one, and it seemed to work all right, but it didn't help at all. Panels are still gone :(

---

### Post by SkonesMickLoud on 2008-05-26
Does

```

killall gnome-panel
gnome-panel
```

produce the same result?

---

### Post by r_gudimella on 2008-05-26
Hey guys,

I had the same thing happen to me as arcelios... thing is, it happened a bit after a software update (just installed hardy). I tried both killall gnome panel, and restarted gnome panel, now im installing kubuntu-desktop to see whether this problem is limited to gnome. If anyone has a fix, we would greatly appreciate it.

-thanks,

RG

---

### Post by arcelios on 2008-05-26
> **SkonesMickLoud said:**
> Does

```

killall gnome-panel
gnome-panel
```

produce the same result?

Yeah, no change. :(

---

### Post by drewcoon on 2008-05-26
nvm bad idea so I removed :o

---

### Post by EdGato on 2008-05-26
Had the same problem with XFCE under Xubuntu. So in case anyone else here has a similar problem and would like to get their feet wet...

Create a new user then copy the /home/<username>/* directory of the new user to the home directory of the old username which has the missing panels. I think with my case it replaced the old XFCE panel configuration files with the default one which was in the newly-created user.

> cp -rv /home/<NewUsername>/* /home/<CorruptedUsername>/ 

 Back up your /home/<CorruptedUsername> folder first. Worked with mine - XFCE was restored. It was still a new install, though (and a SEVENTH re-install coz I love messing around with the settings and I am not very familiar with editing the config files - it's a good way to learn, though. I found out later that right-clicking on the panel and clicking remove contiually will eventually cause the panel to disappear :)...

---

### Post by pedrogl on 2008-05-27
Haven't tried them myself:

Opt. 1:
Press ALT-F2, and type gnome-panel

Opt. 2:
Switch to text console with CTRL-ALT-F1, then type
```
gnome-panel --display=:0.0
```
Then, switch back to X display with ALT-F7

---

### Post by arcelios on 2008-05-27
> **pedrogl said:**
> Haven't tried them myself:

Opt. 1:
Press ALT-F2, and type gnome-panel

Opt. 2:
Switch to text console with CTRL-ALT-F1, then type
```
gnome-panel --display=:0.0
```
Then, switch back to X display with ALT-F7

I'll give it a try right now...

---

### Post by arcelios on 2008-05-27
I tried 
```
gnome-panel --display=:0.0
```
It spewed out a bunch of text, then ended with "ABORTED". I went back to the desktop, and there was no change. :(

---

### Post by sisco311 on 2008-05-27
Try to remove the configuration files of the panel:
```
rm -rf ~/.gconf/apps/panel
```Alt+F2:
```
gnome-panel
```

---

### Post by arcelios on 2008-05-27
> **EdGato said:**
> Had the same problem with XFCE under Xubuntu. So in case anyone else here has a similar problem and would like to get their feet wet...

Create a new user then copy the /home/<username>/* directory of the new user to the home directory of the old username which has the missing panels. I think with my case it replaced the old XFCE panel configuration files with the default one which was in the newly-created user.



 Back up your /home/<CorruptedUsername> folder first. Worked with mine - XFCE was restored. It was still a new install, though (and a SEVENTH re-install coz I love messing around with the settings and I am not very familiar with editing the config files - it's a good way to learn, though. I found out later that right-clicking on the panel and clicking remove contiually will eventually cause the panel to disappear :)...

How do you add a new user if you can't see the panels?

---

### Post by sisco311 on 2008-05-27
> **arcelios said:**
> How do you add a new user if you can't see the panels?

```
sudo adduser username
```Add the user to the Administrator group:
```
sudo addgroup username admin
```But first try to delete the config files.

---

### Post by arcelios on 2008-05-27
> **sisco311 said:**
> [But first try to delete the config files.

what do you mean, delete the config files?

---

### Post by sisco311 on 2008-05-27
this:
> **sisco311 said:**
> Try to remove the configuration files of the panel:
```
rm -rf ~/.gconf/apps/panel
```Alt+F2:
```
gnome-panel
```

---

### Post by arcelios on 2008-05-27
Didn't help :(
All right, I'm gonna try the new user thing.

---

### Post by arcelios on 2008-05-27
> **EdGato said:**
> Had the same problem with XFCE under Xubuntu. So in case anyone else here has a similar problem and would like to get their feet wet...

Create a new user then copy the /home/<username>/* directory of the new user to the home directory of the old username which has the missing panels. I think with my case it replaced the old XFCE panel configuration files with the default one which was in the newly-created user.



 Back up your /home/<CorruptedUsername> folder first. Worked with mine - XFCE was restored. It was still a new install, though (and a SEVENTH re-install coz I love messing around with the settings and I am not very familiar with editing the config files - it's a good way to learn, though. I found out later that right-clicking on the panel and clicking remove contiually will eventually cause the panel to disappear :)...

I tried this, but after creating a user and logging in under them, I found that their panels were gone too. I guess this problem is not user-explicit, so whatever this problem is, it's affecting my whole OS-not just one user. Any ideas? :confused:

---

### Post by kpkeerthi on 2008-05-28
I had similar problem - In my case, the panels were present but invisible (when I right-click on the area where the panel should be displayed, I could see the right-click context menu but not the panels).

Deleting the compiz folder under ~/.config immediately fixed the problem.

---

### Post by lanzen on 2008-05-28
Well in this case, and provided compiz has been setup for opacity control, Alt+Wheel on the panel area should show it, shouldn't it?

---

### Post by kpkeerthi on 2008-05-28
> **lanzen said:**
> Well in this case, and provided compiz has been setup for opacity control, Alt+Wheel on the panel area should show it, shouldn't it?

I don't think it is related to opacity. If it was, I should be able to read the text (Applications Places System) on the panels but I was not. Also if I click on the area where "Applications" is present (but not visible) I could see it expanding and displaying the menu categories just fine.

---

### Post by arcelios on 2008-05-28
Here is a summary of the problems I am having:

- My panels, both top and bottom, are gone.

- When I right click, nothing happens. No matter where I'm clicking. Weather it's on the area where the panel should be or on the desktop, nothing.

- When I click on the area where the panel should be, I also get nothing. 

- I should've mentioned this earlier, all my desktop icons are gone.

- When I click+drag, nothing happens. (You know, there's supposed to be a lighter-colored box adjusting size as you drag, that allows you to select things. I can't think of what it's called right now.)


I'm on the verge of just reinstalling ubuntu :(

---

### Post by arcelios on 2008-05-28
Any help would be GREATLY appreciated! (Read previous post for summary)

-Arcelios

---

### Post by jackocleebrown on 2008-05-28
Hi,
I had a similar problem and think I have managed to work around it. I only have the issue when I use my ubuntu laptop at work. The symptoms are the same as you describe - the panel does not load on login (or partially loads and is unresponsive). I connect to the internet at work through a proxy server which required authentication - I don't have this setup by default because it messes up my settings for home. I think that this was the problem for me, something on the panel was trying to get access to the net (perhaps the weather applet or the calendar (via evolution)) and hanging because it could not authenticate with the proxy server - I found that after I setup the proxy using "gnome-network-preferences" everything worked fine. I guess that you can also work around it just by unplugging your ethernet connection (turn off your wireless) before you login. Give it a go.

Jack.

---

### Post by arcelios on 2008-05-28
> **jackocleebrown said:**
> Hi,
I had a similar problem and think I have managed to work around it. I only have the issue when I use my ubuntu laptop at work. The symptoms are the same as you describe - the panel does not load on login (or partially loads and is unresponsive). I connect to the internet at work through a proxy server which required authentication - I don't have this setup by default because it messes up my settings for home. I think that this was the problem for me, something on the panel was trying to get access to the net (perhaps the weather applet or the calendar (via evolution)) and hanging because it could not authenticate with the proxy server - I found that after I setup the proxy using "gnome-network-preferences" everything worked fine. I guess that you can also work around it just by unplugging your ethernet connection (turn off your wireless) before you login. Give it a go.

Jack.

I'm on a mac, and there's no button I can press externally to disable my wireless. How can I disable my wireless? I can disable it from OS X, but without the panel, I can't do that from Ubuntu.

---

### Post by jackocleebrown on 2008-05-29
You can stop all networking using the command "sudo /etc/init.d/networking stop". It can be started again with "sudo /etc/init.d/networking start". If you use "ctrl+alt+F1" before you login to switch to a terminal, you can stop networking from there and then "ctrl+alt+F7" back to gdm and login to see if it made any difference.

Jack.

---

