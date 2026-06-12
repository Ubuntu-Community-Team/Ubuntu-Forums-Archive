---
title: "Emerald theme manager, not switching themes?"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by NoTiG on 2007-04-23
when i click on a theme in the emerald theme manager... nothing chances. i do not see any buttons that say "apply" .

i am assuming that its suppose to automatically change and that its not because something is wrong? i tried clicking on all of them and nothing worked

---

### Post by UbieNoobie on 2007-04-23
I had the same issue and had to install the Beryl Manager from the synaptic package thingumny. Then you right click the red diamond in your task bar to choose emerald them.

It works but I have to load up the Beryl Manager everytime I restart.

---

### Post by catof on 2007-04-24
If you right-click the beryl manager icon and select "Reload Window decorator" after selecting a new theme in the "Emerald Themer" application it should work. At least it did for me.

---

### Post by compmodder26 on 2007-04-24
Are you sure you have Emerald set up as your window decorator?

---

### Post by FuturePilot on 2007-04-24
Are you using XGL? This happened to me and I figured out it was XGL's fault. If you log out and log back in it might change.

---

### Post by NoTiG on 2007-04-25
thanks guys. i right clicked the beryl ruby and i didnt have emerald as my decorator. apparently i was using heliodor

---

### Post by g0ow on 2007-04-28
> **catof said:**
> If you right-click the beryl manager icon and select "Reload Window decorator" after selecting a new theme in the "Emerald Themer" application it should work. At least it did for me.

i try to do this, but those two options are dimmed, and i can not click on them...any advice?

---

### Post by alx.joom on 2007-10-20
Hello guys , i m having the same problem with the themes but i cannot find the icon
beryl manager .At system > preferences > Emerald theme manager is properly installed so are desktop effects. Any ideas what i m missing?

I ve just installed 7.10

---

### Post by linfidel on 2007-10-21
> **NoTiG said:**
> when i click on a theme in the emerald theme manager... nothing chances. i do not see any buttons that say "apply" .

i am assuming that its suppose to automatically change and that its not because something is wrong? i tried clicking on all of them and nothing workedI'm finding that the only way I can get a theme to work is to click on the theme, then run a terminal and type in "emerald& --replace";  but if I close the terminal, I lose the titlebar completely.

Is this the only way to do it?

---

### Post by kregg on 2007-10-21
> **linfidel said:**
> I'm finding that the only way I can get a theme to work is to click on the theme, then run a terminal and type in "emerald& --replace";  but if I close the terminal, I lose the titlebar completely.

Is this the only way to do it?
Thanks for that linfidel! Now I understand how to get it to work properly!

1.  Right click on the GNOME Top panel, and select "Add to Panel"
2. Search for "run" and click on the cog-wheels and press Add.
3. Close the window and click on the cog wheel
4. Enter (or copy and paste) the following:
```
emerald --replace
```

If this works, then follow on:
5. Go to System>Preferences>Sessions
6. Click the add button
7. Add the same command as you did with the run box (here it is again):
```
emerald --replace
``` and give it a name like "Emerald theme applier" (or whatever you wish)

You can restart Ubuntu now, and it should work all the time.

---

### Post by linfidel on 2007-10-21
After I restarted, Emerald came up automatically.  Maybe I have the option to save sessions automatically, but now when I make changes, it happens right away.

---

### Post by kregg on 2007-10-22
Yes, you have the option "Save settings when logged off" ticked in the Sessions panel.

Just incase you want to get rid of it, Go to Systems>Preferences>Sessions, go to the third tab, and untick the checkbox and close.

---

### Post by ben2talk on 2008-04-14
All of the above used to work, however I recently rendered my account incapable of logging in to the gnome desktop, so I rm'ed the settings folders and started more or less from scratch. I uninstalled emerald, reinstalled it. Now I have a lot of themes available, but cannot apply any of them. Moreover, if I click the theme and then go to edit I see the buttons that are currently applied to my windows.

I have one emerald theme, it's a new human ubuntu theme - but I made my own theme based on humanoid, with very small light blue borders... very nice (no titlebar or buttons). Now it's stuck even after uninstalling.

Should I look to delete config files and rebuild (I kept copies of the themes on another partition...)?

---

### Post by Linkinxp on 2008-04-14
In terminal type:

emerald --reload && deown 

or emerald --restart && deown 

im not sure which one is it!

---

### Post by ben2talk on 2008-04-15
ben@601-Linux:~$ emerald --reload && deown
emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"

ben@601-Linux:~$ emerald --restart && deown 
emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"

Sorry, that doesn't work!

What is 'deown'?

---

### Post by timopat2000 on 2008-04-22
I too had the problem with making the emerald theme manager stick.  I found that if you go into the CompizConfig Settings Manager (system/preferences/Advanced Desktop Setting and then scroll down to the "effects" area and if "Window Decoration" is checked, make sure that in its settings, the "Command" is set to "/usr/bin/emerald"  after that, you will need to restart and well for me it worked. After that I was able to switch themes on the fly with no trouble and when I restarted, the theme was what I had last set it to.... Lots of luck..

Timothy


Ubuntu 8.04 Hardy

---

