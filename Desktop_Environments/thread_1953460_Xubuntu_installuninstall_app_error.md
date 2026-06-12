---
title: "Xubuntu install/uninstall app error"
date: 2012-04-06
forum: Desktop Environments
---

### Post by tdlam on 2012-04-06
Hello folks,
I am new to linux and have installed Xubuntu on my Dell Inspirion laptop. I have spent a few days getting it to do exactly what I need and am very pleased with the result. 
But I ma having trouble with error messages that pop up now either during install or uninstall of any application. I believe it has to do with some modem software/ app that I installed but didnt work correctly. I saved the errors and am posting them here. Please understand that I am new and hopefully some one can help me solve this. 
I also get errors in a text dump at shut down on my screen but it still shuts down ok.
Any ideas folks?  Thank you in advance.
----------------------------------------------------------------


Reading database ... 301136 files and directories currently installed.)
Removing yate-core ...
Removing libspandsp2 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Setting up capiutils (1:3.12.20071127-0ubuntu9) ...
Note: running MAKEDEV to create CAPI devices in /dev...
mount: unknown filesystem type 'capifs'
invoke-rc.d: initscript capiutils, action "start" failed.
dpkg: error processing capiutils (--configure):
 subprocess installed post-installation script returned error exit status 32
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of isdnactivecards:
 isdnactivecards depends on capiutils (>= 1:3.12.20071127-0ubuntu9); however:
  Package capiutils is not configured yet.
dpkg: error processing isdnactivecards (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 capiutils
 isdnactivecards
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up capiutils (1:3.12.20071127-0ubuntu9) ...
Note: running MAKEDEV to create CAPI devices in /dev...
mount: unknown filesystem type 'capifs'
invoke-rc.d: initscript capiutils, action "start" failed.
dpkg: error processing capiutils (--configure):
 subprocess installed post-installation script returned error exit status 32
dpkg: dependency problems prevent configuration of isdnactivecards:
 isdnactivecards depends on capiutils (>= 1:3.12.20071127-0ubuntu9); however:
  Package capiutils is not configured yet.
dpkg: error processing isdnactivecards (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 capiutils
 isdnactivecards

-----------------------------------------------------------------
Reading database ... 301223 files and directories currently installed.)
Removing efax ...
Removing efax-gtk ...
Removing gnome-ppp ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up capiutils (1:3.12.20071127-0ubuntu9) ...
Note: running MAKEDEV to create CAPI devices in /dev...
mount: unknown filesystem type 'capifs'
invoke-rc.d: initscript capiutils, action "start" failed.
dpkg: error processing capiutils (--configure):
 subprocess installed post-installation script returned error exit status 32
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of isdnactivecards:
 isdnactivecards depends on capiutils (>= 1:3.12.20071127-0ubuntu9); however:
  Package capiutils is not configured yet.
dpkg: error processing isdnactivecards (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 capiutils
 isdnactivecards
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up capiutils (1:3.12.20071127-0ubuntu9) ...
Note: running MAKEDEV to create CAPI devices in /dev...
mount: unknown filesystem type 'capifs'
invoke-rc.d: initscript capiutils, action "start" failed.
dpkg: error processing capiutils (--configure):
 subprocess installed post-installation script returned error exit status 32
dpkg: dependency problems prevent configuration of isdnactivecards:
 isdnactivecards depends on capiutils (>= 1:3.12.20071127-0ubuntu9); however:
  Package capiutils is not configured yet.
dpkg: error processing isdnactivecards (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 capiutils
 isdnactivecards

---

### Post by Paddy Landau on 2012-04-06
You don't show the command you were doing when those errors occurred.

Try opening a terminal and entering these commands, in order:
```
sudo apt-get --fix-broken install
sudo dpkg --configure --pending
sudo apt-get update
sudo apt-get upgrade
```If successful, that will install any pending updates. Try doing whatever it was you were trying before and let us know if it works.

---

### Post by tdlam on 2012-04-06
Thank you for your kind and quick response. It is greatly appreciated and is an example of the linux helpful community I had heard so much about.
Unfortunately, none of it worked...I got errors for each command inputted..and I still get the same error installing or un installing from synaptic package manger or the Ubuntu software center.

(Reading database ... 301094 files and directories currently installed.)
Removing bomber ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up capiutils (1:3.12.20071127-0ubuntu9) ...
Note: running MAKEDEV to create CAPI devices in /dev...
mount: unknown filesystem type 'capifs'
invoke-rc.d: initscript capiutils, action "start" failed.
dpkg: error processing capiutils (--configure):
 subprocess installed post-installation script returned error exit status 32
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of isdnactivecards:
 isdnactivecards depends on capiutils (>= 1:3.12.20071127-0ubuntu9); however:
  Package capiutils is not configured yet.
dpkg: error processing isdnactivecards (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 capiutils
 isdnactivecards
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up capiutils (1:3.12.20071127-0ubuntu9) ...
Note: running MAKEDEV to create CAPI devices in /dev...
mount: unknown filesystem type 'capifs'
invoke-rc.d: initscript capiutils, action "start" failed.
dpkg: error processing capiutils (--configure):
 subprocess installed post-installation script returned error exit status 32
dpkg: dependency problems prevent configuration of isdnactivecards:
 isdnactivecards depends on capiutils (>= 1:3.12.20071127-0ubuntu9); however:
  Package capiutils is not configured yet.
dpkg: error processing isdnactivecards (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 capiutils
 isdnactivecards

---

### Post by Paddy Landau on 2012-04-07
It looks as though [FONT=Lucida Console]capiutils[/FONT] and [FONT=Lucida Console]isdnactivecards[/FONT] are causing problems. Are they applications that you need?

Please try the following from a terminal.
```
sudo apt-get purge isdnactivecards capiutils
sudo apt-get autoremove
```Then repeat the commands in [post=11822635]post #2[/post].

Let us know what happens.

BTW, when posting responses from the terminal, please enclose them within [noparse]```
[/noparse] and [noparse]
```[/noparse] (or highlight the responses and press the "#" sign in the toolbar).

---

### Post by tdlam on 2012-04-07
Well that solved it. Thank you ever so much for your kind help. I will try to post better in the future using the parameters you set forth.
Since I am new I was wondering if you could perhaps enlighten me as to what you think may have happened and if my issue was or is a rather common issue. That would be a great help as I want to learn as much as I can.
Again all the best and thanks for your kind patience.

---

### Post by mörgæs on 2012-04-08
Please mark the thread 'solved' using 'thread tools'.

---

### Post by Paddy Landau on 2012-04-08
> **tdlam said:**
> Since I am new I was wondering if you could perhaps enlighten me as to what you think may have happened and if my issue was or is a rather common issue.
It's not common, but just recently it seems to have happened to a number of people.

I'm not exactly sure what happened, but somehow an installation failed part-way through. The dependencies meant that the package manager was unable to proceed until the error was fixed.

If you are coming from Windows, it is important for you to know the role of a package manager. The package manager manages all installations, updates, upgrades and deinstallations. This way, you have a central place to manage your programs and their dependencies. If you stick to the official (default) repositories, you can be sure that every program you install has been tested, is virus-free (not that any Linux viruses are known, at the moment, to be in the wild), and is compatible with your system.

In other words, don't ever download programs from websites until such a time as you know what you are doing; and even then, stick only to websites with a high reputation. If you must install a program that is unavailable on the official repositories, as a newbie please ask for help.

> **mörgæs said:**
> Please mark the thread 'solved' using 'thread tools'.
A link: [marking your thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by tdlam on 2012-04-08
That is good info...and yes now that you mentioned it I believe I did go to a random site and downloaded something for my laptop modem that started the problem.
Once again I appreciate you time and kind explanations. You have made my life easier and I thank you for it. I look forward to using linux for a long time form here on out.
I will now mark this thread as solved.

All the best to you and those you care about in your life.

---

### Post by Paddy Landau on 2012-04-08
> **tdlam said:**
> ... I believe I did go to a random site and downloaded something for my laptop modem that started the problem.
I'm sure it wasn't random! ;)

If you want capiutils and isdnactivecards, install them from the standard repositories, using Ubuntu Package Manager, Synaptic Package Manager or from the terminal with apt-get.

> **tdlam said:**
> ... I appreciate you time and kind explanations.
Thank you for your kind words. This is a friendly and helpful forum, and one day soon you'll get the chance to pay it forward.

---

