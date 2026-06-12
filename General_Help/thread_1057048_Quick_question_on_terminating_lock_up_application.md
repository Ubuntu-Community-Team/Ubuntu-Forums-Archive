---
title: "Quick question on terminating lock up application"
date: 2009-02-01
forum: General Help
---

### Post by beetlejuice321 on 2009-02-01
K, I need help terminating a program running in full screen mode without killing X.

The reason is, I have been currently downloading and installing packages, games, and updates to my recently upgraded Ubuntu system.

When installing applications some programs require interaction such as agreeing to licenses etc.

I was installing Enemy Territory at the time when after selecting yes to the license, it asked me if I wanted to run the program. I accidentally selected 'yes'!

[http://en.wikipedia.org/wiki/Enemy_Territory_Fortress](http://en.wikipedia.org/wiki/Enemy_Territory_Fortress)

The problem is that I have not yet installed my Nvidia graphics drivers and now the program has locked up on the main Enemy Territory start menu.

I can't figure out how to exit the program.  Its in full screen mode.  I don't want to perform a cold restart or terminate X because I have updates running in Gnome which require further interaction to complete.

I have tried Ctrl/Alt/Del, Alt+F2, Alt+Tab, Ctrl+C, Alt+F4, and some others as well.  Does anyone know a graceful way to terminate the running program without killing X?  Thanks!

---

### Post by taurus on 2009-02-01
Can you still get to the menu where you can open a terminal, Applications -> Accessories -> Terminal?

If you can, then you can kill the program/process with the PID.

```
ps -A
```
Assuming the program has a PID (first column) of 1234, you would kill it with

```
sudo kill -9 1234
```

---

### Post by alexmaco on 2009-02-01
You can try switching to a virtual terminal ( Alt + Ctrl + F1-F5 ). If it works (it's very likely to) log in from that terminal , use ps + grep and kill, or top, or anything you like to kill the process.

Also, first attempt to kill it with 15 (SIGTERM), and if this fails use 9 (SIGKILL).

---

### Post by beetlejuice321 on 2009-02-01
Wow both your ideas were really helpful.  Thank you very much!

I totally forgot about virtual terminals using ( Alt + Ctrl + F1-F5 )!  That worked and I did relogin, but I cannot find the PID for Enemy Territory.  I tried looked at the process time, but I am unable to tell which one it is....I did some quick Google searching but still not sure what the process name might be.

Well I will have to look some more.  But since I can now access a virtual terminal is there any other things I can try to locate the process and kill it?

---

### Post by taurus on 2009-02-01
Can you post the output of this command?

```
ps -A
```

---

### Post by alexmaco on 2009-02-01
Also 

```
ps -e | grep wolf
```

then 

```
kill -15 <pid>
```

---

### Post by beetlejuice321 on 2009-02-01
Well I finally found the process, I killed it using "sudo kill -9 (process ID)". I am not sure what the "kill -15" option does, but tried the -9 first.

Anyways, it definitely killed the App.  But it left me in at a full screen terminal window!  X was still running as when I type "startx", I receive an error stating X is still active.

I am betting that I am in a terminal window that is in full screen mode.  meaning I killed the app, but the console is still active that the appication must have been running in, or some such thing.  I still couldn't exit out of the console with "ctrl+c" or anything like that.

Anyways I just finally got so frustrated I decided to warm reboot with "shutdown -r now".  And sure enough as soon as I ran that, the screen flashed, and I could see my whole X desktop (Gnome) before the system completely rebooted!  

Man that's weird, I just wish there was a way to kill these full screen apps like these in X gracefully.  Something like using Ctrl-Alt-Del in windows exits out of the shell a game is running in for instance (or using the Windows Key) and returns you to the desktop where you can kill the apps, or run another program while still in your graphical environment.  

If anyone has any idea how I could have still gotten through closing this app easily please let me know.  I would like to know how to handle it next time a game freezes on me in X!

---

### Post by taurus on 2009-02-01
If you run the game from a terminal, kill the game _and_ then kill the terminal (gnome-terminal).  That would bring you back to your desktop.

---

### Post by compman25 on 2009-02-01
Or you can ctrl-alt- then left or right arrow key, open terminal and killall whatever program it is.

---

