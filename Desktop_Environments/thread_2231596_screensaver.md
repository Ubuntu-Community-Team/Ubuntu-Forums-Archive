---
title: "screensaver"
date: 2014-06-26
forum: Desktop Environments
---

### Post by kakashi_12 on 2014-06-26
According to what I'm reading....
[http://askubuntu.com/questions/64086/how-can-i-change-or-install-screensavers](http://askubuntu.com/questions/64086/how-can-i-change-or-install-screensavers)
screensavers have been removed from the latest Ubuntu OS's.
I've added them back in, but now I can not use the "Switch User" option that use to be able to use when the screen Wakes.
I also can not "Lock" the computer when screensaver is not on. I've clicked the option and also used Ctrl + Alt + L. Nothing happens!
Also note, that I am using GNome FlashBack desktop environment. Hope this is not the issue.

---

### Post by kakashi_12 on 2014-06-26
When I do click the Switch User button, this is the error I get:
xscreensaver: 15:08:52: could not execute "gdmflexiserver": No such file or directory

---

### Post by kakashi_12 on 2014-06-27
I just re-installed the OS to troubleshoot a couple ideas. First I installed the screensaver without removing the existing one.
That's didn't help, still same error.
Althought one difference is I am able to lock the computer now, but still can not switch user FROM screensaver.
Also running under Unity instead of GNome, but still get the same error when trying to switch user from screensaver.

Any ideas?

---

### Post by kakashi_12 on 2014-06-28
Ok..... is there support for xScreenSaver anywhere?

---

### Post by Toz on 2014-06-28
Which screensaver are you using? The default one with Ubuntu is now light-locker. The way that user-switching now works with lightdm/light-locker is that after you lock the session and are presented with the unlock dialog, you can enter another user's credentials to "switch" over to a profile for that account. If that person is already logged in, you will be connected to their existing session. If they are not yet logged in, they will then be logged in. So basically, the "switch" happens at the unlock dialog.

xscreensaver is different. It relies on "gdmflexiserver" which is no longer available. A potential workaround (assuming you are using lightdm) is to create a wrapper /usr/local/bin/gdmflexiserver script that runs:
```
dm-tool switch-to-greeter
```
...which will mimick light-locker's process in that you will be presented with another login screen. (An unfortunate side-effect of using xscreensaver now is that on a switch back to an already logged in account will require two password entries - if you set xscreensaver to lock on activation).

---

### Post by kakashi_12 on 2014-06-28
How do I create the script... in gedit? This sounds like a pain in the butt. Is there another flavor of Ubuntu that comes with a screensaver installed that works and allows user switching?

---

### Post by Toz on 2014-06-28
> **kakashi_12 said:**
> How do I create the script... in gedit? This sounds like a pain in the butt. 
Not really.

1. Create the file:
```
sudo -i gedit /usr/local/bin/gdmflexiserver
```
...enter your password when prompted.

2. Copy/paste this content:
```

#!/bin/bash
dm-tool switch-to-greeter
```

3. Save the file then make it executable:
```
sudo chmod +x /usr/local/bin/gdmflexiserver
```

4. Log out and back in again.

Now, on the xscreensaver dialog, clicking the "New Login" option will send you to the lightdm login screen where you can enter another user's credentials.

> Is there another flavor of Ubuntu that comes with a screensaver installed that works and allows user switching?
I'm not sure. Perhaps someone using kubuntu or gnome ubuntu can comment.

---

### Post by kakashi_12 on 2014-06-28
This worked, Thanks! But I need to reformat and do again. This time (according to post #3), I need to NOT remove the current screensaver. Otherwise I can not manually lock the screen. Unless you know another work around. Thanks.

---

### Post by kakashi_12 on 2014-06-28
Nope, nevermind. Doesn't work.
Problem is if I stop the Gnome ScreenSaver like I'm suppose to...
```
sudo apt-get remove gnome-screensaver
```
Then I can NOT manually lock the screen (before screensaver is ready to come on).

If I do not stop the Gnome ScreenSaver, then XScreenSaver never starts... until I go into the XScreenSaver applet and say "Yes" to stop daemon for Gnome screensaver.

I need either another Distro or another desktop environment.
Or sadly, learn to live without it. But I prefer not to.

---

### Post by Toz on 2014-06-29
After you remove gnome-screensaver, you should log out and back in again to stop the gnome-screensaver from running (either that or kill the running process). You should also add xscreensaver to your startup applications so that it auto-starts on login.

To manually activate xscreensaver, bind the command "xscreensaver-command -activate" to a shortcut key of your choosing.

---

### Post by kakashi_12 on 2014-06-29
Ok, I went to Applications > System Tools > Preferences > Keyboard > Shortcuts tab > System.
Then I assigned the keys I wanted. That didn't work.
How do I bind? I am guessing I have to 'sudo gedit' a file.

---

### Post by Toz on 2014-06-29
I've never used gnome fallback so I'm not sure of the process to set up a keyboard shortcut. However, for the keyboard shortcut to work, xscreensaver has to be running. You can check if its running by:
```
ps -ef | grep xscreensaver | grep -v grep
```

---

### Post by kakashi_12 on 2014-06-30
Then how do you set the bind after that?

---

### Post by kakashi_12 on 2014-07-01
Command didn't do anything.

---

### Post by kakashi_12 on 2014-07-01
Even better yet... is there an alternative to XScreenSaver? Some other screensaver app that I can use that is more reliable.
Or... my alternative to not live with a screensaver is if I could get the background to shuffle images. I can't even get it to do that for now.

Unless you know how to bind?

---

### Post by Toz on 2014-07-01
I'm sorry but I've never used gnome flashback and as such, do not know how to setup keyboard shortcuts in that environment. Perhaps you could start another thread asking specifically how to set up the keyboard shortcuts in gnome fallback? 

For what its worth, I use Xubuntu and you can use xscreensaver and shuffle backgrounds in this flavour of Ubuntu.

---

### Post by kakashi_12 on 2014-07-01
So, when you install xscreensaver, the lock function works? you don't have to set it up or tie it to a shortcut key?

---

### Post by kakashi_12 on 2014-07-02
I'm reading another forum that says I can set up a Launcher to do a Lock. How do I set up a launcher? Cause when I right click, that option is not there.

---

### Post by kakashi_12 on 2014-07-02
Got it. Right click on Applications, Edit Menu. I can add a Launcher from here.
Then I can add this launcher to the desktop and make it executable if I wish for it to be on the desktop.
In the launcher I put this command, "**[SIZE=2]xscreensaver-command -lock[/SIZE]**"
[http://ubuntuforums.org/showthread.php?t=195557](http://ubuntuforums.org/showthread.php?t=195557)

Works! :)

---

### Post by kakashi_12 on 2014-07-02
_Final Resolution_:

```
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra
```
```
sudo apt-get remove gnome-screensaver
```

(Note: This step step must be done for ALL USERS.)
```
xscreensaver-demo
```
Click Ok to both prompt to stop Daemon for old screensaver and start new.
Set time for "Blank After", "Lock Screen After", and choose desired screensaver.
Close.

(Note: This step step must be done for ALL USERS.)
Click Applications, System Tools, Preferences, Start Up Applications, Add.
Name: XScreenSaver
Command: xscreensaver -nosplash
Comment: Starts XScreenSaver at log in.
Add, Close.

Reboot.

```
sudo -i gedit /usr/local/bin/gdmflexiserver
```
paste this text below into file:
#!/bin/bash
dm-tool switch-to-greeter

Save and close file.
```
sudo chmod +x /usr/local/bin/gdmflexiserver
```

Log out. Log in.

(Note: This step step must be done for ALL USERS.)
Hold ALT and right click the GNome Panel, Add To Panel.
Select "Custom Applicatoin Launcher", Add.
In the "Create Launcher" dialog box, type...
Name: Lock
Command: [SIZE=2]xscreensaver-command -lock[/SIZE]
Comment: Lock PC and launch screensaver
Icon: click icon and select a lockpad.gif file
Ok, Close.

*Note: when clicking the custom icon (lock button) it will launch ScreenSaver and Lock the PC.
An unfortunate feature about using xscreensaver is that you have to enter your password twice when you use the Switch User feature. Once at the greeter and once at the screensaver.
If you don't want to quickly walk away from your pc and don't want to have to enter your password twice when you come back, you can easily click the Gear icon, then any other UserName in the list.
As long as LightDM is set NOT to show username list on greeter, no user will be logged when when choosing them from the Gear. You would still have to actually enter the UserName.
Clicking any UserName will display go to the Greeter (log in screen), but screensaver will not run in this instance.*

---

