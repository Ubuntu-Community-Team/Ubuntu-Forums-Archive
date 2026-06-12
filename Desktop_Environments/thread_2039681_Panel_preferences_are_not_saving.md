---
title: "Panel preferences are not saving"
date: 2012-08-09
forum: Desktop Environments
---

### Post by RieuxTarrou on 2012-08-09
Hello,

My panel preferences for xubuntu are not saving after I shutdown. The preferences default back to a random configuration that I setup much earlier. Do I need to ask to save the session each time I reconfigure the desktop layout?

Thanks for any help!

---

### Post by Toz on 2012-08-09
A couple of things to check to make sure that the save of the settings isn't being prevented.

1. Make sure you own the ~/.config/xfce4/panel and ~/.config/xfce4/xfconf/xfce-perchannel-xml/ directories and files. From a terminal prompt:
```
ls -l ~/.config/xfce4/ | grep panel && ls -l ~/.config/xfce4/
ls -l  ~/.config/xfce4/xfconf &&  ls -l ~/.config/xfce4/xfconf/xfce-perchannel-xml/
```

2. Check to see if xfce is crashing on logout. Logout and go to the first tty (Ctrl+Alt+F1). Login to the text screen there and save the .xsession-errors file (it will be over-written on next login):
```
mv ~/.xsession-errors ~/.xsession-errors.BAK
```
Go back to the GUI screen (Ctrl+Alt+F7), log back in and post the contents of ~/.xsession-errors.BAK. You can use pastebinit for this:
```
pastebinit ~/.xsession-errors.BAK
```
...and post back the link that is generated.

---

### Post by SantaFe on 2012-08-09
In Settings Manager/Session & Startup, do you have Automatically Save Session On Logout checked?  

If it's unchecked, try checking it & resetting everything & log out & back in.

I assume that saves everything panel prefs and all.

---

### Post by RieuxTarrou on 2012-08-09
Here is the link for the output from pastebinit [http://paste.ubuntu.com/1138048/](http://paste.ubuntu.com/1138048/)

Any explanation of the results would be much appreciated.

Thanks for the help.

> **Toz said:**
> A couple of things to check to make sure that the save of the settings isn't being prevented.

1. Make sure you own the ~/.config/xfce4/panel and ~/.config/xfce4/xfconf/xfce-perchannel-xml/ directories and files. From a terminal prompt:
```
ls -l ~/.config/xfce4/ | grep panel && ls -l ~/.config/xfce4/
ls -l  ~/.config/xfce4/xfconf &&  ls -l ~/.config/xfce4/xfconf/xfce-perchannel-xml/
```2. Check to see if xfce is crashing on logout. Logout and go to the first tty (Ctrl+Alt+F1). Login to the text screen there and save the .xsession-errors file (it will be over-written on next login):
```
mv ~/.xsession-errors ~/.xsession-errors.BAK
```Go back to the GUI screen (Ctrl+Alt+F7), log back in and post the contents of ~/.xsession-errors.BAK. You can use pastebinit for this:
```
pastebinit ~/.xsession-errors.BAK
```...and post back the link that is generated.

---

### Post by Toz on 2012-08-09
Posting back the results from step #1 would be helpful as well.

Here are the interesting things from your .xsession-errors log file:
1. liblauncher errors:
```
liblauncher-Message: launcher-11: Failed to cleanup the configuration: Error removing file: Directory not empty
liblauncher-Message: launcher-10: Failed to cleanup the configuration: Error removing file: Directory not empty
liblauncher-Message: launcher-20: Failed to cleanup the configuration: Error removing file: Directory not empty
liblauncher-Message: launcher-5: Failed to cleanup the configuration: Error removing file: Directory not empty
liblauncher-Message: launcher-19: Failed to cleanup the configuration: Error removing file: Directory not empty
liblauncher-Message: launcher-3: Failed to cleanup the configuration: Error removing file: Directory not empty
liblauncher-Message: launcher-8: Failed to cleanup the configuration: Error removing file: Directory not empty
```
From the xfce4-panel source code:
> Print cleanup failure in a console message.
    
    When a launcher plugin is removed, it tries to cleanup
    the desktop dir. Hower this might fail because of leftover
    files in the (re-used) directory from a previously
    craches launcher.
    
    Only print this in the terminal, because nothing is going
    'wrong', just not so nice.
But I wonder if something has gone wrong. In addition to running request #1 from my previous post, can you also run:
```
ls -l ~/.config/xfce4/panel/
```
...I want to see if the permissions are correct and you have access to those directories.

2. I/O Errors:
> IOError: [Errno 5] Input/output error: '/home/gabriel/.config/software-center/softwarecenter.cfg.new'
Although not related to xfce4-panel, I/O errors are worrisome because they tend to indicate drive failure. Note however, that I'm not convinced its a drive error, the error message itself might be erroneous. Lets just keep this one in mind for now.

3. xfce4-panel crash:
> The application 'xfce4-panel' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
It looks like it did crash. Can you try creating another account on your computer and trying to make the same changes to the panels? If it works there, then the problem is probably within your own configuration files and we can try resetting them (a reset will lose all your configuration settings so lets do that as a last resort).

---

### Post by RieuxTarrou on 2012-08-10
Oh, I'm sorry I didn't post the first step. Below is what I should have posted earlier including the additional steps you suggest in your last post.

1. 

Results from ls -l ~/.config/xfce4/ | grep panel && ls -l ~/.config/xfce4/

```
drwxrwxr-x 17 gabriel gabriel 4096 2012-08-10 10:38 panel
total 84
drwx------  2 gabriel gabriel 4096 2012-08-09 12:44 desktop
-rw-rw-r--  1 gabriel gabriel   24 2012-08-05 09:39 helpers.rc
drwxrwxr-x 17 gabriel gabriel 4096 2012-08-10 10:38 panel
drwx------  2 gabriel gabriel 4096 2012-08-08 15:23 parole
drwx------  2 gabriel gabriel 4096 2012-03-04 16:35 Verve
-rw-rw-r--  1 gabriel gabriel  281 2012-03-26 14:22 xfce4-notes.gtkrc
-rw-rw-r--  1 gabriel gabriel  128 2012-03-26 14:28 xfce4-notes.rc
-rw-rw-r--  1 gabriel gabriel  108 2012-04-25 19:31 xfce4-screenshooter
-rw-rw-r--  1 gabriel gabriel  302 2012-07-27 14:12 xfce4-taskmanager.rc
drwxrwxr-x  3 gabriel gabriel 4096 2012-01-02 11:14 xfconf
drwx------  2 gabriel gabriel 4096 2012-01-02 11:14 xfwm4

```

Results from ls -l  ~/.config/xfce4/xfconf &&  ls -l ~/.config/xfce4/xfconf/xfce-perchannel-xml/

```
total 4
drwx------ 2 gabriel gabriel 4096 2012-08-09 12:04 xfce-perchannel-xml
total 208
-rw-rw-r-- 1 gabriel gabriel 1373 2012-08-06 18:48 displays.xml
-rw-rw-r-- 1 gabriel gabriel  204 2012-01-02 22:47 keyboards.xml
-rw-rw-r-- 1 gabriel gabriel  470 2012-02-25 11:42 pointers.xml
-rw-rw-r-- 1 gabriel gabriel  657 2012-04-11 19:53 ristretto.xml
-rw-rw-r-- 1 gabriel gabriel  335 2012-03-23 19:12 xfce4-appfinder.xml
-rw-rw-r-- 1 gabriel gabriel 1546 2012-08-06 18:48 xfce4-desktop.xml
-rw-rw-r-- 1 gabriel gabriel 9485 2012-03-09 21:30 xfce4-keyboard-shortcuts.xml
-rw-rw-r-- 1 gabriel gabriel 1924 2012-04-28 15:35 xfce4-mixer.xml
-rw-rw-r-- 1 gabriel gabriel  328 2012-08-06 19:18 xfce4-notifyd.xml
-rw-rw-r-- 1 gabriel gabriel 7454 2012-05-25 08:28 xfce4-panel.xml
-rw-rw-r-- 1 gabriel gabriel    0 2012-05-25 08:38 xfce4-panel.xml.new
-rw-rw-r-- 1 gabriel gabriel  434 2012-08-06 19:17 xfce4-power-manager.xml
-rw-rw-r-- 1 gabriel gabriel 1356 2012-08-06 18:49 xfce4-session.xml
-rw-rw-r-- 1 gabriel gabriel  279 2012-03-01 17:19 xfce4-settings-editor.xml
-rw-rw-r-- 1 gabriel gabriel  220 2012-08-09 12:04 xfce4-settings-manager.xml
-rw-rw-r-- 1 gabriel gabriel 4894 2012-08-09 08:37 xfwm4.xml
-rw-rw-r-- 1 gabriel gabriel 2242 2012-08-09 08:37 xsettings.xml

```

Results from ls -l ~/.config/xfce4/panel/ 

```
total 84
drwx------ 2 gabriel gabriel 4096 2012-08-09 10:04 launcher-10
drwx------ 2 gabriel gabriel 4096 2012-08-09 09:56 launcher-11
drwx------ 2 gabriel gabriel 4096 2012-08-09 09:56 launcher-13
drwx------ 2 gabriel gabriel 4096 2012-08-04 20:48 launcher-19
drwx------ 2 gabriel gabriel 4096 2012-08-04 20:48 launcher-20
drwx------ 2 gabriel gabriel 4096 2012-08-05 09:24 launcher-21
drwx------ 2 gabriel gabriel 4096 2012-08-09 12:00 launcher-22
drwx------ 2 gabriel gabriel 4096 2012-08-09 12:00 launcher-23
drwx------ 2 gabriel gabriel 4096 2012-08-09 12:01 launcher-24
drwx------ 2 gabriel gabriel 4096 2012-08-05 09:41 launcher-29
drwx------ 2 gabriel gabriel 4096 2012-08-09 14:12 launcher-3
drwx------ 2 gabriel gabriel 4096 2012-08-09 09:53 launcher-5
drwx------ 2 gabriel gabriel 4096 2012-08-09 09:55 launcher-6
drwx------ 2 gabriel gabriel 4096 2012-08-09 09:56 launcher-7
drwx------ 2 gabriel gabriel 4096 2012-08-09 09:56 launcher-8
-rw-rw-r-- 1 gabriel gabriel  213 2012-08-10 10:38 places-1.rc
-rw-rw-r-- 1 gabriel gabriel    0 2012-05-25 08:38 places-1.rc.1671.tmp
-rw-rw-r-- 1 gabriel gabriel  254 2012-04-02 17:45 XfceTimer.rc

```

All try your "cheat" account workaround and see what happens after I rearrange the panel there.

---

