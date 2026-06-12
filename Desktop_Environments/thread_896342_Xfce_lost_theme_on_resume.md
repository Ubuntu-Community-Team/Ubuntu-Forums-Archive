---
title: "Xfce lost theme on resume"
date: 2008-08-21
forum: Desktop Environments
---

### Post by joele on 2008-08-21
I am using an eeePC 900 and got xubuntu working well on it, just one problem. When I suspend the device and resume again, everything is fine BUT the theme drops back to the default. I then just go into '>Settings>Settings Manager' and while settings manager is loading all the theme elements come back (I don't need to do anything in the settings manager)...

Is there a command I can issue in the acpi resume, that would do the same thing, without actually loading the settings manager up.. failing that what command can I issue that would load the settings manager (quicker to close that, than start it manually and close it too each time)...

---

### Post by prshah on 2008-08-21
> **joele said:**
> 
Is there a command I can issue in the acpi resume, that would do the same thing, without actually loading the settings manager up.. failing that what command can I issue that would load the settings manager (quicker to close that, than start it manually and close it too each time)...

You can try the following: 

Place a script in the directory "/etc/apm/resume.d/" that will start the settings manager, wait a couple of seconds, and then close it down. I don't know how well/properly it will work, use at your own risk! Type out the commands; don't copy/paste as a block; if you want to copy/paste, do so line-by-line.

```

sudo -i
#at this point you are in root shell, please be extra careful with commands
cd /etc/apm/scripts.d/
cat > settheme.sh
/usr/bin/xfce-setting-show && sleep 3 && killall xfce-settings-show
#press Ctrl+D to save this script.
chmod 755 settheme.sh
cd ../resume.d/
ln -s ../scripts.d/settheme.sh 96resumetheme
exit
cd

```

At this point, you've created a last-to-be-executed script that will startup the settings manager and kill it three seconds later.

Note that the GUI may actually not be running at this point, so I don't know how far it will help you.

Once again, this is at your own risk; you may want to wait for someone else to confirm these steps before you attempt them.

---

### Post by joele on 2008-08-21
Thanks that works to start it, but says there is nothing to kill on the kill part.. still it is an improvement :KS

---

### Post by prshah on 2008-08-22
> **joele said:**
> Thanks that works to start it, but says there is nothing to kill on the kill part.. still it is an improvement :KS

```
usr/bin/[color=blue]xfce-setting-show[/color] && sleep 3 && killall [color=red]xfce-settings-show[/color]
```

Yes, my (spelling) mistake; correct the script so that the part in red is the same as the part in blue (knock off the extra "s" in the middle); eg```
usr/bin/xfce-setting-show && sleep 3 && killall xfce-setting-show
```

---

### Post by joele on 2008-08-22
mmm, still starts but doesn't stop and says...

xfce-setting-show: no process killed

---

### Post by prshah on 2008-08-22
> **joele said:**
> mmm, still starts but doesn't stop and says...
xfce-setting-show: no process killed

Hmm.. apparently all xfce-setting-show does is send a signal to xfce-mcs-manager and then disappears, itself; mcs-manager seems to be producing the dialog box; killing mcs-manager removes all customisations.

Try this: Comment out all lines in the little script we made, and just add a single line as below:```

# /usr/bin/xfce-setting-show && sleep 3 && killall xfce-setting-show
xfce-mcs-manager
```

Now it will not display the settings window, but should bring up your theme automatically.

---

### Post by joele on 2008-08-22
awesome problem solved!!!

Thanks again...

---

### Post by prshah on 2008-08-22
> **joele said:**
> awesome problem solved!!!


OK! Please mark this thread as solved; near the upper right hand side of the page, you will find a link "Thread Tools", click on this, then click "Mark thread as solved."

---

