---
title: "Can't install applications"
date: 2009-05-16
forum: Desktop Environments
---

### Post by Fernando Hernandez on 2009-05-16
Hello, I recently had a problem and needed to uninstall and reinstall kubuntu, and now i'm having a problem installing applications.  When i open my application manager (it's KPackageKit) and search for apps it's only showing for some reason packages i already have installed...nothing new to install, just programs to remove, and i don't know why or how to fix it.  Is there a way to fix it or another way to install programs?  i know nothing about compiling source code, i always use the manager to install my apps...what can i do?  I really need to install applications, i can't get by on just the KDE4 defaults.

---

### Post by x33a on 2009-05-16
maybe some filter is enabled. i am not using kubuntu, so i don't have an idea about its interface. but, check for some settings, which might have enabled something similar to " show currently installed applications".

---

### Post by Screwdriver0815 on 2009-05-16
check if the filter for installed packages is enabled and set it on "all packages" if necessary. To do this, click on "Filter" in the righthand upper corner and go to "installed". Check if there a filter like "installed only" is set.

Another way to install software is to use the terminal.

If you want to search for a package by its name or description, simply type in:

```
sudo apt-get search *keyword*
```

*keyword* has to be replaced with the keyword which you are searching for.

If you found something usefull and want to install it:

```
sudo apt-get install *packagename*
```

*packagename* has to be replaced by the actual name of the package.

hope this helps!

---

### Post by Fernando Hernandez on 2009-05-24
Sorry for the delayed reply, I've had some personal issues lately to contend with.

Anyway, I do not have a filter enabled, it was the first thing I checked.  Every category under the filters heading has 'no filter' enabled.  So it's not filtering my searches...it's just somehow not accessing the list of available programs.  If I type in a search that doesn't match a program or package already installed, it just turns up no results.

I've since uninstalled and reinstalled Kubuntu from the live CD, and the problem remains.  Do I have to format my computer?  Will that even fix this problem?  I have no idea what's going on, and even trying to install from the command line, it says it turns up no matches.  No programs found.  And I am typing the actual package names verbatim...still no results.  I don't know what's going on.  Is it possible that after my initial uninstall there were some files that remained on the machine and it's not reinstalling all the proper files but somehow working on those ghost files?  I have no idea how hardware works.  I just know I had to uninstall my kubuntu because I accidentally wiped some crucial system files...and it's as though even after reinstalling more than once those files aren't being replaced.  Something is wrong...and I don't know what so I don't even know where to begin.

---

### Post by Screwdriver0815 on 2009-05-27
> **Fernando Hernandez said:**
> Sorry for the delayed reply, I've had some personal issues lately to contend with.

Anyway, I do not have a filter enabled, it was the first thing I checked.  Every category under the filters heading has 'no filter' enabled.  So it's not filtering my searches...it's just somehow not accessing the list of available programs.  If I type in a search that doesn't match a program or package already installed, it just turns up no results.

I've since uninstalled and reinstalled Kubuntu from the live CD, and the problem remains.  Do I have to format my computer?  Will that even fix this problem?  I have no idea what's going on, and even trying to install from the command line, it says it turns up no matches.  No programs found.  And I am typing the actual package names verbatim...still no results.  I don't know what's going on.  Is it possible that after my initial uninstall there were some files that remained on the machine and it's not reinstalling all the proper files but somehow working on those ghost files?  I have no idea how hardware works.  I just know I had to uninstall my kubuntu because I accidentally wiped some crucial system files...and it's as though even after reinstalling more than once those files aren't being replaced.  Something is wrong...and I don't know what so I don't even know where to begin.
sounds like that you have no software sources enabled. can you check the /etc/apt/sources.list if there are any entries? Just open the file with a texteditor and paste the content into the thread.

Another way for checking is:
open the KpackageKit and go to "settings" and in the menu on "edit software sources". In there, check if the sources are checked-on.

hope this helps

---

