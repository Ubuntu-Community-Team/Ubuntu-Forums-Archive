---
title: "Opening NVU and Thunderbird"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Philz on 2005-10-13
Hi, I am new to Ubuntu, so I am sorry if I will offend any of you with these newbie questions:
1)
I have installed nvu and thunderbird, but when I e.g open nvu I get this errror : 

[I](nvu-bin:10025): Gdk-WARNING **: locale not supported by Xlib

(nvu-bin:10025): Gdk-WARNING **: cannot set locale modifiers
Extension System Warning: Failed to set up default extensions files probably because you do not have write privileges to this location. While you can run Firefox like this, it is recommended that you run it at least once with privileges that allow it to generate these initial files to improve start performance. Running from a disk image on MacOS X is not recommended.*** nsExtensionManager::_disableObsoleteExtensions - failure, catching exception so finalize window can close
*** loading the extensions datasource[/I]

And nothing else happens?

2) Is there a guide to the linux commands? (I havent just followed ubuntoguide.com)

3) I try to install azureus via. the apt, but it can't find the program? What do I then do?

4) Last but not least, is there a guide on how to install programs which you don't install via. apt?

Thanks a lot in advance :)

---

### Post by kassetra on 2005-10-13
[QUOTE=Philz]Hi, I am new to Ubuntu, so I am sorry if I will offend any of you with these newbie questions:
1)
I have installed nvu and thunderbird, but when I e.g open nvu I get this errror : 

[I](nvu-bin:10025): Gdk-WARNING **: locale not supported by Xlib

(nvu-bin:10025): Gdk-WARNING **: cannot set locale modifiers
Extension System Warning: Failed to set up default extensions files probably because you do not have write privileges to this location. While you can run Firefox like this, it is recommended that you run it at least once with privileges that allow it to generate these initial files to improve start performance. Running from a disk image on MacOS X is not recommended.*** nsExtensionManager::_disableObsoleteExtensions - failure, catching exception so finalize window can close
*** loading the extensions datasource[/I]

And nothing else happens?

2) Is there a guide to the linux commands? (I havent just followed ubuntoguide.com)

3) I try to install azureus via. the apt, but it can't find the program? What do I then do?

4) Last but not least, is there a guide on how to install programs which you don't install via. apt?

Thanks a lot in advance :)[/QUOTE]


1. using sudo - change the write permissions to the .nvu file/directory in your home directory to be owned & writable by you (watch capitalization - nVu or nvu!  also name = your username): 
```
sudo chown -R name.name .nvu
```

2. yes - many many many.  the beginner area of this forum has some great references.  In Ubuntu, there are very few commands that you would "need" to know, as most command line functions can be handled with the systems applications.

3. azureus you have to install manually, or wait for the backports to include it.

4. yes, in the beginner area, there should be a nice explanation - but the short of it is this:
```
sudo dpkg -i filename.deb
```

---

