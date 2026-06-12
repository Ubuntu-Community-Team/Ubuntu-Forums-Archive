---
title: "Problem: it shows only the desktop"
date: 2011-05-09
forum: Desktop Environments
---

### Post by aliboy on 2011-05-09
After setting some preference in compiz then restart, now I only have the desktop. 

I want to uninstall the compiz using terminal, please help me by providing the code to do it.

(also, alt+f2 is not working. do you know whats wrong?)

---

### Post by ajgreeny on 2011-05-09
Make sure the gnome-compatibility plugin in the general section of compiz is enabled, and that Alt+F2 is set for the run dialog.

To stop compiz running for now use the run dialog and command **metacity --replace** in the box.  You can then play around with the plugins and changes you made and try again with compiz with the run dialog and **compiz --replace** command, until you get things as you want.

---

### Post by aliboy on 2011-05-09
I type metacity --replace in terminal but nothing happened. I still have only the desktop.

---

### Post by aliboy on 2011-05-09
after typing this> metacity --replace and hit enter,
i have to forced to turned off the pc because i cant type anything or open other application.


after the restart, i type compiz --replace in terminal then there is error:


libcompizconfig: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory

Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
compiz (core) - Error: Couldn't load plugin 'mousepoll'
compiz (core) - Error: Couldn't load plugin 'vpswitch'
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin 'snap'
compiz (core) - Error: Couldn't load plugin 'expo'
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin 'staticswitcher'
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
compiz (core) - Error: Couldn't load plugin 'session'
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
Segmentation fault

---

### Post by aliboy on 2011-05-09
I have the screenshot of whats on the display.

---

### Post by ajgreeny on 2011-05-09
What version of ubuntu?  Are you using unity in 11.04 or the classic gnome desktop in a previous version?

To remove compiz use command ```
sudo apt-get remove compiz-core
``` and see what happens, though if the **metacity --replace** did not help, removing compiz may not help either.

---

### Post by aliboy on 2011-05-09
its 11.04, ok ill try your code

---

### Post by aliboy on 2011-05-09
after uninstalling compiz, i still have only the desktop, the pointer becomes 'x' instead of arrow and i cant maximize the browser by double clicking the title bar but to manually drag the edge to maximize. I think its better to reinstall the OS.

---

### Post by aliboy on 2011-05-09
can i just reinstall the unity?

---

### Post by aliboy on 2011-05-09
i tried this code:

sudo apt-get install unity


but i still have only the desktop

---

### Post by Copper Bezel on 2011-05-09
> (also, alt+f2 is not working. do you know whats wrong?)

Alt+F2 doesn't do anything unless either Unity or the Gnome Panel is running.

Unity is implemented through Compiz, so if you switch to Metacity, it'll naturally disappear. In this case, one of your settings changes seems to have disabled something.

Since you reinstalled Unity, you shouldn't be missing any Compiz parts. Use these commands to restore your Compiz settings and reactivate the Unity plugin:

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

---

### Post by aliboy on 2011-05-09
in the terminal>>


ali@ali-ubuntu11:~$ gconftool-2 --recursive-unset /apps/compiz-1
ali@ali-ubuntu11:~$ unity --reset
unity-panel-service: no process found
compiz (core) - Error: Couldn't load plugin 'ccp'
compiz (core) - Error: Couldn't load plugin 'ccp'
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0


then the cursor is just blinking like its waiting for something...


what should i do next?

---

### Post by Copper Bezel on 2011-05-09
Did you reinstall Compiz before trying it? If you followed ajgreeny's original instructions (and it sounded as if you had,) then the problem above sounds like a result of that (not finding compiz-core.)

---

### Post by aliboy on 2011-05-10
yes. i tried to change the given code to make "remove" into "install" then put compiz. then i tried your code.

---

### Post by Rat2000 on 2011-05-10
> **Copper Bezel said:**
> 
```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```


Oh wow thanks this worked for me. I just wanted ALT-TAB to work (which it didn't in my install) and by changing the compiz settings I ended up with no Unity.

That's way too finicky in my opinion.


Edit: Do NOT activate the "Application Switcher" instead of the "Static Application Switcher" in CompizConfig. It may be prettier by Unity doesn't like it at all (at least in my case).

---

### Post by aliboy on 2011-05-11
so i guess only OS re-installation will resolve my problem. is there any other recommendation?

---

### Post by Krytarik on 2011-05-12
aliboy, please see this troubleshooting guide for anything you haven't tried already:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

Greetings.

---

### Post by aliboy on 2011-05-13
Thanks for the help. The link really help. a little change in compizconfig setting manager and everything is back to normal, and no need to reinstall ubuntu.

---

