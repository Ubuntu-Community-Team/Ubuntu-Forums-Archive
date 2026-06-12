---
title: "Parts of default desktop environment are missing"
date: 2016-02-05
forum: Desktop Environments
---

### Post by Edward_Fish on 2016-02-05
For anyone who visits this thread, here's my solution.
- Copy your home folder, /opt and anything else with important data to an external drive
- Burn an Ubuntu install disc
- Format Ubuntu's partition and reinstall using the disc
- Put back anything inportant that you miss, but DON'T PUT BACK ANY SETTING FILES!!! These are normally stored in ~/.config/
!! Only use this as last resort, try some other solutions first !!

Recently I stupidly installed openbox and xorg, I'm not sure why. I certainly don't know exactly what they do.
After restarting my computer some time later, I discovered that it is EXTREMELY slow because "compiz" is using 30% cpu and 100 MB RAM. Also, things that were transparent before (like the dash) are now opaque.
Concluding that xorg/openbox was the issue, I removed them both.
After restarting, I found that, upon logging in, the launcher has vanished, as well as the top panel. I cannot use keyboard shortcuts and the desktop icons do not open any applications.
However
I can still access a terminal with Ctrl-Alt-F1. Using this, I installed LXDE (which works!) and I can also run the ccsm compiz setting manager, and any CLI application. (I also tried resetting the compiz setting using dconf, but that did not fix it.)
Also, logging in a a guest, Unity works, but there is still the compiz issue, and transparency is still broken.
What do I have to do to get Unity back? LXDE is... alright I guess, but Unity is prettier, and I know how to use it better. Should I back up my data and reinstall? Is there a reset settings command?

---

### Post by ajgreeny on 2016-02-05
> Recently I stupidly installed openbox and xorg, I'm not sure why. I certainly don't know exactly what they do.
Compiz is a compositing window-manager essential for the unity desktop; openbox is anotyher window-manager that can be used as an alternative WM for other desktop-environments or can be used alone for a very simple windowed system; it does not manage to run unity, you must have compiz for that, as far as I'm aware.
Xorg is the software that at present runs the visual GUI part of *ubuntu, though there is going to be a move away from xorg to a newer server to do that job, which we don't need to discuss here.

What did you start with, Ubuntu with unity or something else?
Why did you need to install xorg? If you had any desktop environment previously you already had xorg and all its dependencies.
Do you really need compiz if you are now using a DE other than unity? Compiz can use a lot of resources and works best on a machine with reasonable specification.

Tell us more, please.  We need to know your machine specs, the version of *ubuntu you are using and all info about what you've done so far in much more detail.

---

### Post by Edward_Fish on 2016-02-05
Ok, I'm on the default Ubuntu Desktop 14.04 installation, installed from live DVD. I've had it about 3-4 months I would guess.
The main partition is ext4 and is 60GB, I still have a lot of free space.
It has 2GB ram and I think 1.6 GHz processor clock. Not sure which make of processor.
Sure, definitely not the best specs, but I could run Unity perfectly fine, with no slowdown, and compiz certainly didn't use so many resources before.
In short - Unity is unusable. I would like to be able to go back to it, but in the meantime, I have to use the command line or LXDE.
Why did I install openbox and xorg in the first place? I'm not sure, I was following a tutorial for something or other which turned out to not work anyway.
I hope this information helps you!

---

### Post by vasa1 on 2016-02-05
> **Edward_Fish said:**
> ... Should I back up my data and reinstall? Is there a reset settings command?
My vote is for backing data and doing a clean re-install. There's no "reset settings" command that I know of. It may be theoretically possible to undo whatever's gone wrong but...

---

### Post by grahammechanical on 2016-02-05
Unity is actually a Compiz plugin and it is possible to deactivate the Unity plugin using Compiz Configuration Settings Manager (CCSM). If we deactivate the Unity plugin without having installed an alternative desktop user interface, then we break to OS.

Making changes in CCSM when using an alternative window manager that does not use Compiz will not have any noticeable effect because the alternative UI does not respond to CCSM but the changes made will still mess up the Unity settings. Possibly.

Have you tried using CCSM and putting all settings back to default? And while you are at it make sure that the Unity plugin is enabled. When using CCSM it is necessary to make a record of the changes that we are making. Otherwise we will not know what settings to correct should the changes mess up the user interface.

I also see re-installing as a simple way to fix things. It will certainly undo all the things that were done by following that tutorial.

Regards.

---

### Post by ajgreeny on 2016-02-05
Whoa, whoa!  Don't reinstall just yet; let's try to sort this out first.

What exactly did you install when you added openbox and xorg?  If you're not sure let's see the output of command ```
grep -iw install /var/log/dpkg.log.1 /var/log/dpkg.log
``` which will list all packages that have recently been installed, listed by date and time so you will be able to find all the packages that were added at the same time as those two.

Can I assume you are aware that you need to choose Ubuntu from the sessions available to you at the login-screen if you have previously chosen openbox as your session.  If not openbox will remain the chosen WM, though it should not look anything like unity.

I am also wondering if the openbox window manager has confused your system, so before doing anything so all-encompassing as reinstalling try removing openbox with command ```
sudo apt-get remove openbox
``` and then to make doubly sure that the system is using compiz run command ```
compiz --replace
``` then logout and login again to restart the xsession.

---

### Post by vasa1 on 2016-02-05
Wouldn't```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
```be cleaner?

---

### Post by Edward_Fish on 2016-02-05
grahammechanical:
Where's the reset settings button located?

ajgreeny:
Oh, there's an installed packages log. That's handy.
Yes, I realise that I have to select a desktop environment when I log in. LXDE appears in that menu.
I already removed openbox.
How do I do compiz --replace without being able to open a terminal in the desktop and how do I log out and back in without being able to access the top panel?

The command produced a lot of output, I'll try to link a pastebin.

---

### Post by ajgreeny on 2016-02-05
> **vasa1 said:**
> Wouldn't```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
```be cleaner?
Yes, you're correct; it is cleaner and removes the startup and information lines.

Thanks for that tip.

---

### Post by Edward_Fish on 2016-02-05
Here's a link to a pastebin: [http://pastebin.com/raw/TGWNmyGe](http://pastebin.com/raw/TGWNmyGe)

EDIT: I should mention that the pastebin only contains the packages which were installed at the same time as xorg and openbox.
So should I just run:
~# for i in $(cat dpkg.log); do apt-get remove $i; done
to remove all of those packages? Would that work?

---

### Post by vasa1 on 2016-02-05
> **Edward_Fish said:**
> Here's a link to a pastebin: [http://pastebin.com/raw/TGWNmyGe](http://pastebin.com/raw/TGWNmyGe)

EDIT: I should mention that the pastebin only contains the packages which were installed at the same time as xorg and openbox.
So should I just run:
~# for i in $(cat dpkg.log); do apt-get remove $i; done
to remove all of those packages? Would that work?

Did you also get that code (**~# for i in $(cat dpkg.log); do apt-get remove $i; done**) from some tutorial? Judging from what you plan to remove, I hope you've backed up all your data and have a Live CD or Live USB or Live DVD close at hand.

Tip: apt-get offers a simulation mode. Use that in future before installing/removing stuff.

---

### Post by Edward_Fish on 2016-02-06
Really? I hoped that command might fix the problem. Good thing I didn't try it!
It's probably easier to reinstall in onto the same partition without formatting it first. That way it will fix the OS files. Yes, I have looked this up on multiple sources, and it will work. I also have a backup of all my important files just in case.
Yeah, I'm going to reinstall Ubuntu. I'll let you know how it goes.

---

### Post by vasa1 on 2016-02-06
> **Edward_Fish said:**
> Really? I hoped that command might fix the problem. Good thing I didn't try it! ...

I doubt that "command" would have run.
Even if it worked it would have removed programs essential to most GUI-applications.
I prefer to add one thing or to remove one thing at a time and to test each step with a simulation to know what will happen (to a close approximation).

Edit: one small point ... there are quite a few "tutorials" out there. It would be nice to know which ones you referred to.

---

### Post by ajgreeny on 2016-02-06
If you were using unity desktop previously you will already have had xorg installed so I am still baffled about why you thought it necessary to install that, and also how you managed to do it, unless you used the **apt-get install --reinstall** command.
Can you enlighten us?

There is also a 20 minute gap between installing all those xorg packages and the 5 openbox packages, so to clean up you could still remove these:-
> 2016-02-04 17:34:38 install libimlib2:amd64 <none> 1.4.6-2
2016-02-04 17:34:39 install libobt2:amd64 <none> 3.5.2-6
2016-02-04 17:34:40 install libobrender29:amd64 <none> 3.5.2-6
2016-02-04 17:34:41 install obconf:amd64 <none> 1:2.0.4+git20130908-2
2016-02-04 17:34:43 install openbox:amd64 <none> 3.5.2-6 but **do not remove any of the others in your long list** or you will be left with command-line only.

---

### Post by vasa1 on 2016-02-06
> **Edward_Fish said:**
> Here's a link to a pastebin: [http://pastebin.com/raw/TGWNmyGe](http://pastebin.com/raw/TGWNmyGe)

EDIT: I should mention that the pastebin only contains the packages which were installed at the same time as xorg and openbox.
So should I just run:
~# for i in $(cat dpkg.log); do apt-get remove $i; done
to remove all of those packages? Would that work?
I'm still curious to know the source of the code. Where did you get it from? Why did you think it might work?

---

### Post by Edward_Fish on 2016-02-08
Reinstalling did NOT work, so it's not broken packages, it's some bad setting stored in my home directory. I tried a few things to fix the settings, including using ccsm to enable the unity plugin. Didn't work.
So right now I'm using duplicity to restore my backup from before it happened. Let's hope this one works, or I'm stumped.

---

### Post by vasa1 on 2016-02-08
[SUP][/SUP]> **Edward_Fish said:**
> Reinstalling did NOT work, so it's not broken packages, it's some bad setting stored in my home directory. I tried a few things to fix the settings, including using ccsm to enable the unity plugin. Didn't work.
So right now I'm using duplicity to restore my backup from before it happened. Let's hope this one works, or I'm stumped.
Did you not choose to overwrite your /home folder? If you have backed up your personal data[SUP]***[/SUP], there's no harm in overwriting your home folder.

As you seem to feel, there may have been some "bad" settings in your ~/.config or elsewhere that will continue to cause you problems.

***Maybe it should be clear that "personal data" would be things like *your* documents, music, videos, pictures, etc expressly created by you and _***not***_ any of the files or folders which are automatically created by programs.

---

### Post by Edward_Fish on 2016-02-08
The backup was restored, but IT'S STILL BROKEN! AAH!
I tried moving some configuration files (~/.config/compiz-1, ~/.compiz) to another place so they would be recreated with the default settings. But, it appears they were recreated with broken settings, or I moved the wrong config files. Nothing happened.
So I'm going to have to backup all my documents (but not .folders) to a drive, delete my user account, and recreate it so the settings reset. Hopefully. Is this the right decision? Please advise.

Oh yeah, I ought to mention that the compiz CPU + memory usage problem fixed itself, so that's something at least. Also, if I log in to a guest account, Unity/compiz/whatever works perfectly, so the problem is definitely a bad setting.

---

### Post by vasa1 on 2016-02-08
> **Edward_Fish said:**
> ...
I tried moving some configuration files (~/.config/compiz-1, ~/.compiz) to another place so they would be recreated with the default settings. But, it appears they were recreated with broken settings, or I moved the wrong config files. Nothing happened.
So I'm going to have to backup all my documents (but not .folders) to a drive, delete my user account, and recreate it so the settings reset. Hopefully. Is this the right decision? Please advise.

Oh yeah, I ought to mention that the compiz CPU + memory usage problem fixed itself, so that's something at least. Also, if I log in to a guest account, Unity/compiz/whatever works perfectly, so the problem is definitely a bad setting.
Some settings are in dot files or dot folders, others aren't. I suggest you back up all data expressly created by you.
If you do a clean reinstall, there's no need to delete your "user account and recreate it so the settings reset". Everything will be wiped clean. New slate, new user.

I hope you're the type of person who keeps personal data in easily identifiable folders and don't have a lot of personal stuff directly in ~/ as opposed to ~/Documents, ~/Music, ~/Pictures, etc.

Bottom line, no need to panic. You've seen for yourself that there's nothing intrinsically wrong with your hardware. But next time you want to follow something you find on the 'net, try to understand what's being suggested. It's quite easy to bork things. And not all steps are simple to reverse.

---

### Post by Edward_Fish on 2016-02-09
Yay it works now

I copyied my home directory to a usb drive, formatted the partition and reinstalled Ubuntu. Then I put back the important stuff from the drive. It works! Thanks for the support!

---

### Post by vasa1 on 2016-02-09
Great! Now please be careful running commands and scripts :)

---

