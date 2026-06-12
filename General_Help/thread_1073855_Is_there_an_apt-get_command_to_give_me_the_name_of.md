---
title: "Is there an apt-get command to give me the name of the last few packages installed."
date: 2009-02-18
forum: General Help
---

### Post by Chilli Bob on 2009-02-18
(SOLVED)

Hi, last night I installed two packages through "add/remove". One was the search utility "Beagle, I think", the other was a Gnome menu that includes a search function.  I did this on a whim, and can't remember the name of the packages.  After installation I ran them both from the dialog box.  My desktop froze and my hard drive ran for about an hour, and now when I boot, I don't have a task bar and can't interact with the desktop at all.

Anyway, I want to uninstall these last two packages, but can't remember the names.  Is there a way of finding the names of recently installed packages?  I looked at the apt-get man page, but couldn't find anything.

Thanks in advance.

---

### Post by spcwingo on 2009-02-18
I'm not sure of the apt-get command, but you can try looking in synaptic under file>history.

EDIT:  I missed the part about losing your taskbar, etc.  Have you tried pressing alt+F2 and entering "gksu synaptic" then proceeding as above?

---

### Post by Zip247 on 2009-02-18
You could try looking at your local repository and finding the programs you think you installed.

local repository is in /var/cache/apt/archives 

If you haven't done an apt-get clean in a while the contents of this directory may be big.

wdecker

---

### Post by Coreigh on 2009-02-18
If you have some idea of the package name then you can do this:
```
sudo dpkg -l | grep <keyword>
```
Where <keyword> is some part of the name of what you are looking for.'


Is there similar switch to show the list sorted by date?


EDIT:
the history is in /var/log/dpkg.log

so you could:
```
sudo less /var/log/dpkg.log
```
to scroll through the history. The log files are archived too so there may be more info in dpkg.log.1.gz or dpkg.log.2.gz etc.

---

### Post by mikewu on 2009-02-18
I think this should work. 

sudo grep "Setting up " /var/log/apt/term.log

It will  return a list of packages that have been install or updated.

If you want more details on the dates, just open up the log file with any text editor.

---

### Post by Chilli Bob on 2009-02-19
Thank-you all.  I went with mikewu's suggestion and it worked perfectly. Luckily I had the LXDE desktop installed as was able to work from there.

 "gnome-main-menu" was the package causing the problem.

Thank goodness for the terminal, eh?

---

### Post by mavior on 2009-02-23
> **Chilli Bob said:**
> (SOLVED)

Hi, last night I installed two packages through "add/remove". One was the search utility "Beagle, I think", the other was a Gnome menu that includes a search function.  I did this on a whim, and can't remember the name of the packages.  After installation I ran them both from the dialog box.  My desktop froze and my hard drive ran for about an hour, and now when I boot, I don't have a task bar and can't interact with the desktop at all.

Anyway, I want to uninstall these last two packages, but can't remember the names.  Is there a way of finding the names of recently installed packages?  I looked at the apt-get man page, but couldn't find anything.

Thanks in advance.

Let's try apt-log [http://mavior.eu/apt-log](http://mavior.eu/apt-log)

---

