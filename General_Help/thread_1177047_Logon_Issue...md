---
title: "Logon Issue.."
date: 2009-06-03
forum: General Help
---

### Post by tuxmanic on 2009-06-03
I Installed some Themes from a 3rd party repo([**Link**]("http://ubuntumanual.org/posts/177/eyecandy-themes-for-ubuntu-download-via-launchpad-ppa-repo-and-be-safe"))..

After this i selected one of the newly installed logon theme....

Now after system boot **log on screen is not appearing**.. insted of that only a white screen is there... 
But all the Virtual Consoles are functional.. but i can log on to virtual console..

How i can fix this logon issue ??? **Is there any way to reset all the logon screen setting to Default/chage it using Virtual console** ???? ......  pls Help me...:(

---

### Post by jenkinbr on 2009-06-03
It appears to be a problem with your gdm settings and the theme you have specified in gdmsetup.

When the computer has booted, switch to tty2 (press <ctrl+alt+F2>)

Login using your username/password

Run **sudo nano /etc/gdm/gdm.conf**

Find the following section of the file (it's a ways down) that looks like:
```
# These two keys are for the themed greeter (gdmgreeter).  Circles is the
# standard shipped theme.  If you want GDM to select a random theme from a
# list then provide a list that is delimited by /: to the GraphicalThemes
# key and set GraphicalThemeRand to true.  Otherwise use GraphicalTheme
# and specify just one theme.
GraphicalTheme=Human
#GraphicalThemes=bijou/:blueswirl/:circles/:debblue-list/:debblue/:ayo/:debian-dawn/:debian-greeter/:debian/:glassfoot/:hantzley/:happygnome/:industrial/:crystal/:linsta
GraphicalThemeDir=/usr/share/gdm/themes/
GraphicalThemeRand=false
```

Edit the line **GraphicalTheme=<whatever>** to **GraphicalTheme=Human**

Save the file by pressing <ctrl+x> followed by <y>

Reboot and see if it is fixed now. Type **exit** and then press <ctrl+alt+delete>

---

