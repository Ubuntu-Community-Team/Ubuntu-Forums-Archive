---
title: "gnome-settings-daemon crash"
date: 2012-06-21
forum: Desktop Environments
---

### Post by hwychld on 2012-06-21
I have been having a host of problems (see other threads by me) that I believe I have traced down to a crash in the gnome-settings-daemon.

I have the following information in my .xsessions_errors

```

(gnome-settings-daemon:8953): Gdk-WARNING **: The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 557 error_code 8 request_code 141 minor_code 22)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

gnome-session[8870]: WARNING: App 'gnome-settings-daemon.desktop' respawning too quickly
gnome-session[8870]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Initializing unityshell options...done


```

It is not shown in the list of running processes either:

```

user@precise:~$ ps aux | grep gnome-settings-daemon
1000     21087  0.0  0.2 455052  8820 ?        Sl   17:33   0:00 /usr/lib/gnome-settings-daemon/gnome-fallback-mount-helper
root     21608  0.0  0.1 369604  4696 pts/0    Sl   17:36   0:00 /usr/lib/gnome-settings-daemon/gsd-printer
1000     22361  0.0  0.0  13580   892 pts/0    S+   19:53   0:00 grep --color=auto gnome-settings-daemon
user@precise:~$ 


```

I get the same error as seen in the .xsessions_error file if I try to launch gnome-settings-daemon manually from the command line.  I have no doubt that the trouble I have been having is due to this process not running.

Anybody have a solution?

Thanks

---

### Post by hwychld on 2012-06-22
So noone else is having this problem.  Anybody know how to fix this?

---

### Post by CMDR:ZOD on 2012-06-23
So I came across your post while trying to fix a similar error where gnome-settings-daemon would fail like it has been for you. I found it to be a Xrandr problem as everytime I would try to run gnome-settings-daemon after using Xrandr once, would fail - even after subsequent boots without first using Xrandr. This resulted in the ugly old Gtk theme being in use right from boot. Everytime I would try to run the settings daemon the display would blank for a split second, affirming my suspicions of Xrandr + Gnome interaction gone bad. This is what I did to fix it:

In your home folder there are many hidden folders. Find .config and enter the folder. Find monitors.xml and delete it.

Next hit Alt+F2 to enter the run programs dialog. In it type "gksudo nautilus". Enter your password. This will bring up your file browser, but in a mode where you can alter system files as well as the files in your home directory. Find the directory named "etc" in your file system. In "etc" there is another folder named "gnome-settings-daemon". Enter that folder and in it there should be a folder named "xrandr". In that folder you will find another file named monitors.xml. Delete it. Exit nautilus.

Now in accessories enter the terminal and type "gconf-editor". Since we are only editing options inside of your home folder, no sudo or gksudo passwords prompts are necessary. 

In the gconf-editor window goto the "apps" folder and open it. 

Now open the "gnome_settings_daemon" folder and open the plugins folder inside. 

Find the xrandr folder and click on it, and uncheck the active box on the right side. This is where I rebooted, it may or may not be necessary.

 Now close the plugins folder and click on the "xrandr" folder outside of the plugins folder but inside the gnome_settings_daemon folder. Uncheck all options. Once again this may or may not be necessary.

Now for the moment of truth. Enter the plugins folder again and click on the xsettings folder. Uncheck the active button, then recheck it. This is where all of my themes came back to life, even after rebooting.:guitar:  I hope this works for you!! 

P.S. I broke my themes by playing with xrandr. I advise you stay away from it as it obviously has some harsh unintended consequences that are persistent until you fix it the way I've shown. Good luck!
P.P.S. Specifically, I changed the orientation using the monitors utility in Preferences. This caused massive problems. Do not use this function unless you really do want to orient your screen (left, right, upside-down). I was just playing with it and it worked once then from the command line I had to use "xrandr - o normal" just to get the screen back to the proper orientation. This is where I noticed, "Hey where is my theme?'

---

### Post by hwychld on 2012-06-23
Thanks cmdr, I will give that a shot.  I am actually away from my machine for a few days but  I will try it as soon as I am back.  I really appreciate the response.

---

### Post by hwychld on 2012-07-09
Well, I tried the suggestions above but still no dice (and many did not apply - no monitors.xml in /etc/xrandr and no xrandr plugin in gconf-editor) and still am not able to get the gnome-settings-daemon to run.  I have even tried dropping back to the version that was shipped with precise when it came out, but no luck.  

I tried downloading the code but there are so many dependencies that are not on my machine (since I am not a developer) that ./configure is not able to run.  I gave up after fixing the first few.  If I have more time I might get back to it.  It would be nice to compile a version with symbols so I could step through using gdb.

Anybody have any other suggestions?

---

