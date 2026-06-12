---
title: "Minimize, maximize, close buttons randomly missing"
date: 2010-12-03
forum: Desktop Environments
---

### Post by ACupOfCoffee on 2010-12-03
I'm not sure what to call it, but the bar at the top of every window that has the minimize, maximize, and close buttons is missing. I've searched the forums and nothing I could find is quite the same as what I'm experiencing.

I'm running Ubuntu 10.10. metacity --replace works, but only for one session. As soon as I reboot or close the terminal it goes away. I know it's not being hidden by the top panel because it's missing on unmaximized windows regardless of location. I know it's not missing in the config file because every so often I'll boot and it'll be there but the next time it's gone again.

This started a little bit after I upgraded to 10.10. It wasn't right away, so I'm not sure it was related to the upgrade. It's rather annoying, so what can I do to fix it?

---

### Post by sikander3786 on 2010-12-03
Go to Software Center, search for and install fusion-icon.

Once installed, go to Applications > System Tools > Compiz Fusion Icon. You'll see that in your system tray. Use it to switch between Window Mangers ;-)

You can add it to startup by going to System > Preferences > Startup Applications > Add > Command="fusion-icon" without the quotes.

---

### Post by gogolink on 2010-12-03
So is this a Compiz issue?  When the windows' top bar is gone, is that because Compiz Fusion crashed?

Have you entered the command "emerald --replace" into the "command" box in "Window Decoration" (System > Preferences > CompizConfig Settings Manager)?

Or do you just type it in a terminal every time you log in?

---

### Post by ACupOfCoffee on 2010-12-07
So, would removing Compiz and going back to Metacity fix this?

---

### Post by sikander3786 on 2010-12-07
> **ACupOfCoffee said:**
> So, would removing Compiz and going back to Metacity fix this?
Just restarting compiz fixes these type of issues most of the time.

```
compiz --replace
```

Or,

```
metacity --replace
```

Try these and let us know if that brings your title bars back ;-)

---

### Post by ACupOfCoffee on 2011-01-30
It worked. How can I make sure it doesn't happen again? This is what I got when I entered the command.

```
sean@Linux:~$ compiz --replace
compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

```

---

### Post by asmoore82 on 2011-01-30
Try going to "System -> Preferences -> Appearance" and
turn Desktop Effects off and back on again.

Then see if re-saving this setting fixes the issue when logging in.

---

### Post by kevinatjocum on 2011-02-06
here's what I got when I put in

```
 compiz --replace 
```

WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

---

### Post by jroa on 2011-02-06
I used to get this when I used Ubuntu 10.04.  Now, I get it every once in a while with Fedora 13.  It is annoying, but I do believe it is a compiz issue and is not specific to distros.  I just reboot on the rare occasion when it happens.

---

### Post by kevinatjocum on 2011-02-07
well.. when I rebooted and put in that same command (compiz --replace) I got this now

WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz (core) - Warn: Exceeded max texture size

Launching fallback window manager
**
metacity:ERROR:core/prefs.c:2495:meta_prefs_get_workspace_name: assertion failed: (workspace_names[i] != NULL)
Aborted

---

### Post by cbemerine on 2011-02-20
tried the "compiz --replace" and got similar error messages as "ACupOfCoffee" did, but it did not work for me.  I was copy/pasting the messages in this forum to let others know when my system locked up.  My only recovery was pulling the power plug...not something I like to do if there is any other option...there was not.

For the "compiz --replace" I got two error messages like this one, (had my system not locked up, they would have been copied here, not sure what was in parends, but do not think it was cube or video....

compiz (???) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
compiz (???) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png


While I noted the "Or" in the file, but I went on and entered 

metacity --replace

nothing happened.

exit
exit
exit

I attempted to "Exit" by enter exit... when the first one did not take, I entered exit two more times.  Whether the metacity --replace or the three "exit" commands in the terminal window caused the system to lockup I do not know.

A <Ctrl><Alt><Delete> would not let me shutdown the system, in fact the keyboard was locked.

Next time I might try the "metacity --replace" first.  Another logical choice is to find the exact commands to restart Compiz, or stop Compiz and than restart it.  Perhaps there is a compiz restart command.

Last year I used the CompizConfig Settings Manager to restore the buttons and enable the moving of windows on Gnome in the past.  To get to the CompizConfig Settings Manager I did the following two steps:

Application/System Tools/Compiz Fusion Icon
Right mouse clicked the Compiz Fusion Icon and selected "Settings Manager"
. . . sadly I do not remember which config setting specifically fixed it...but just knowing that it provides a potential solution will help someone.

There are other ways to load the CompizConfig Settings Manager, however I know first hand when you are new to a Linux distro, i.e. Ubuntu in this case, it helps to have the sequence of action bar menu items to get to where you need to do something and not 'assume' that the reader knows how to get there...thus I have provided them.

I do NOT remember which setting allowed me to restore the buttons and again move / resize windows, just that it worked for me in the past.  If you see a solution that suggests this, hopefully they will tell you exactly which settings to select and what to set them too, and you should expect it to work.

As I stated earlier, shutting down and restarting the PC will often resolve this problem, but its a pain to have to do that, I feel you should not have to reboot and will continue to search for a command line solution to this problem.  

I don't care if I have to edit config files in the process or not.  I simply like to know how to fix my system via the command line first and GUI second.  As the GUI might fail, but you can always get access to a command line.  Yea I am old school.

When I find a command line solution I will post the version of Ubuntu and Compiz that I am using and provide the answer.  Until someone provides specific, explicit steps to resolving the problem this thread probably should remain open.

Of course I will have to wait for the problem to randomly happen again in the future.

---

### Post by cbemerine on 2011-02-21
Darn thing happened again this AM...

FYI

metacity --replace 

on the command line as the default user (whatever account you use to login to on Ubuntu) did "sort of" work for me.  I did not need to become superuser (sudo -i) aka root, aka su to do this.

By "sort of" While I got the buttons back and can now resize windows and move them around, I am unable to move between the various windows that I expect to have available to me which is a bit frustrating...at least I got the buttons back, but this is obviously NOT a complete solution.

I can move between the four screens and open new windows in each one, but I can not move anything from one of the four to the others...FYI.

I attempted to find the GUI options to restore the minimize, maximize, close buttons and re-enable the ability to move my windows around but was unsuccessful.


@zareason-breeze:/# cat /etc/issue
Ubuntu 10.04.1 LTS \n \l

@zareason-breeze:/# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
root@zareason-breeze:/# 

In case anyone cares about that.  Based on what I have read, this problem that first was reported with Beryl (no longer supported) and is now happening with CompizFusion is pretty much the same problem/issue.  

I am using Nvidia if that matters...as well as Gnome. I got a laugh at the following in my /var/log/dmesg    log: 

[   16.540681] nvidia: module license 'NVIDIA' taints kernel.
[   16.540694] Disabling lock debugging due to kernel taint

I have been tainted, lmao, will have to look into this at another time.

Thats all I have time for right now, will learn more and report back later, this problem is not fixed and rebooting to fix it, well that is not an acceptable fix for me.

---

### Post by Copper Bezel on 2011-02-22
> As I stated earlier, shutting down and restarting the PC will often resolve this problem, but its a pain to have to do that, I feel you should not have to reboot and will continue to search for a command line solution to this problem. 

Small consolation, I know, but logging out and back in will also restart the X server, and there's an instant-kill option in your keyboard layout that's turned off by default (Ctrl+Alt+Backspace.)

---

### Post by BigSilly on 2011-02-22
No, it's just changed to ALT-Printscreen-K. This works. :)

I get this problem occasionally, but I was sure it was a Gnome bug, as I'm having a few of those of late! Suppose it makes sense that it's a Compiz issue.

---

### Post by ohadle on 2011-03-06
Is there a bug open about this?

---

