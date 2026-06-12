---
title: "how can i run .exe"
date: 2009-02-11
forum: General Help
---

### Post by suhas6ue on 2009-02-11
frens can anyone tell me how 2 run .exe files in ubuntu.

---

### Post by snowpine on 2009-02-11
.exe files are Windows executables. They will not run natively in Linux. They'll run best in Windows, but you might try a Linux program called wine: [www.winehq.org](www.winehq.org) They have a database on that site of applications that are known to work/not work.

---

### Post by roshanjose on 2009-02-11
just go to terminal and type

sudo apt-get install wine

and then yyou can run .exe apps

---

### Post by Tibuda on 2009-02-11
> **roshanjose said:**
> just go to terminal and type

sudo apt-get install wine

and then yyou can run .exe apps

Don't tell beginners to use the terminal.
To install packages, open System > Adminstration > Synaptic Package Manager. Search for the package wine, and install it.

---

### Post by SunnyRabbiera on 2009-02-11
Wine should work for most windows applications, but keep in mind we have many alternatives for your favorite windows apps just depending on the app you wish to install.

---

### Post by snowpine on 2009-02-11
> **danielrmt said:**
> Don't tell beginners to use the terminal.


Are you joking?!?

---

### Post by SunnyRabbiera on 2009-02-11
> **snowpine said:**
> Are you joking?!?

well not many even know what a terminal is...

---

### Post by Tibuda on 2009-02-11
> **snowpine said:**
> Are you joking?!?

[No.]("http://ubuntuforums.org/showthread.php?t=898328")

---

### Post by roshanjose on 2009-02-11
> **danielrmt said:**
> Don't tell beginners to use the terminal.
To install packages, open System > Adminstration > Synaptic Package Manager. Search for the package wine, and install it.



Sometimes people such as these lose sense on what to ask and what not to ask and end up making a fool of themselves....


If someone doesn't know what's a terminal..then they can ask and get it clarified....doesn't hurt anyone to explain even silly things

---

### Post by snowpine on 2009-02-11
> **danielrmt said:**
> [No.]("http://ubuntuforums.org/showthread.php?t=898328")

Fair enough, I respect you opinion. :)

When helping others on the forums, I personally prefer to say "copy and paste this command into the terminal" instead of "click the purple button" because people's GUI varies from system to system (what if the button is green on my computer? what if you're running Ubuntu and I'm running Xubuntu?) whereas terminal commands are unambiguous. Plus terminal commands give good output for troubleshooting any problems that might arise.

Plus, which takes longer? Pasting 'sudo apt-get install wine' into the terminal, or "opening System > Adminstration > Synaptic Package Manager. Search for the package wine, and install it." How do I search for the package wine? How do I install it? Your tutorial is not complete. "Open a terminal and type/paste 'sudo apt-get install wine' is a complete tutorial that takes about 5 seconds to follow. :)

---

### Post by Simian Man on 2009-02-11
The reason the terminal is better is because it is independent of their desktop.  If the user is using Xfce or KDE, he won't have "System -> Administration -> Synaptic Package Manager".

---

### Post by roshanjose on 2009-02-11
Snowpine's answer is right......this is apt...

---

### Post by Tibuda on 2009-02-11
This is getting off-topic, but what if someone tells a begginner to type 'sudo rm -fR /'? I agree the terminal is universal and faster. Just telling copy & paste on the terminal works, but is not enough and may confuse some users. We should not think about 'which takes longer' but 'which makes sense'. 'sudo apt-get install' makes sense for me because I know some shell commands, but may not make sense for everyone as does the menus.

Edit: I agree my instructions suppose the user is in Gnome and knows how to work with Synaptic. More info about it can be found here: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by snowpine on 2009-02-11
> **danielrmt said:**
> This is getting off-topic, but what if someone tells a begginner to type 'sudo rm -fR /'? I agree the terminal is universal and faster. Just telling copy & paste on the terminal works, but is not enough and may confuse some users. We should not think about 'which takes longer' but 'which makes sense'. 'sudo apt-get install' makes sense for me because I know some shell commands, but may not make sense for everyone as does the menus.

Hi Daniel, your argument seems to be "the command line is more dangerous than a GUI tool." However, when I click on the "GUI Fan Club" you linked to, I see advice like this: 

> 13.GUI Tip: Put icon on the panel for instant navigation as root, so you can modify files with root permissions (post#3 & 4 Thanks meindian523)
Right click on panel.
Add to Panel > Custom Application Launcher > Add
Name "root" or whatever you want
Command "gksudo nautilus"
"OK"
Should provide a new icon on panel.
Click icon.
Insert your own password (not root password).
Should open navigation window "root &#8211; file browser"

I would argue it is equally easy for an uninformed user to break his/her system, whether they use GUI tools or the terminal. One should always follow tutorials from a trusted source, and understand what the commands do prior to running them. :)

---

### Post by Tibuda on 2009-02-11
Terminal is not dangerou, sudo is dangerous. My argument is: the user should know what he is doing, and understand the menus is easier than the terminal.

---

### Post by snowpine on 2009-02-11
> **danielrmt said:**
> Terminal is not dangerou, sudo is dangerous. My argument is: the user should know what he is doing, and understand the menus is easier than the terminal.

OK, I agree with you 100% there (except maybe that last part). Just a friendly debate. :)

---

### Post by darksideforge on 2009-04-21
I definitely think we're all way off-topic; rosh & daniel both attempted to give good advice. All of us have to be careful from time to time in terms of what we say as opposed to what we mean, and I've gotten in trouble with the Mods myself for posting something too quickly without thinking it through first.

I won't pretend to have the experience you guys have, but I'd like to offer a third suggestion for future use: prior to any of us giving too much advice to a beginner, we might consider taking the time to ask that user what his/her experience level is (with Linux and/or Ubuntu).

My first attempt at using the CLI came when I got on here and tried to follow some directions to un-tar a file...with no concept of the different -**** configs. I crashed my poor lappy twice before one of the senior members took pity on me.

~Just my thoughts.

---

