---
title: "I broke lubuntu.. lxde and ubuntu still work fine"
date: 2014-12-02
forum: Desktop Environments
---

### Post by RabbitWho on 2014-12-02
On the log in screen i can still choose lxde, ubuntu and openbox, but lubuntu is gone. 

rabbit@penguin:~$ sudo apt-get install lubuntu-desktop
[sudo] password for rabbit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 lubuntu-desktop : Depends: modemmanager
E: Unable to correct problems, you have held broken packages.


I uninstalled a bunch of lubuntu and ubuntu apps that i don't use or need, I guess i accidentally uninstalled something important at the same time. The only thing i can think of that i deleted (removed using the software centre) that wasn't just a music player or something similar would be the file manager pacman or whatever it's called and the bluetooth stuff (i haven't got bluetooth hardware)

---

### Post by carlwsnyder on 2014-12-02
First, let's try to get you back to where you were before you broke the packages.  And yes, pcmanfm is part of Lubuntu-desktop.  Let's try with the terminal commands as follows:```
sudo apt-get update && sudo apt-get -f install
```That _should_ have installed any broken dependencies, including modemmanager.  These commands are meant at this point to be run as one line from a command prompt in a terminal.  If you didn't get any new error messages, log out and attempt to log back in on the Lubuntu desktop.

If everything worked, great.  Use the forum tools to mark this thread as solved.

If you are still getting the same error, let's try this from a terminal:```
sudo apt-get install modemmanager
```Again, log out and try to log back in with Lubuntu selected.

Please report any continued errors as they occur.

---

### Post by RabbitWho on 2014-12-02
That worked! thanks very much. 

There was one more step, I had to enter sudo apt-get install lubuntu-desktop again before logging out, it didn't work without that. there were only a few files to install this time. 

Thanks again!

---

