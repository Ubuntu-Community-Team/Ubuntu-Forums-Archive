---
title: "help: error while attempting to install java"
date: 2009-04-10
forum: General Help
---

### Post by deranged_typist on 2009-04-10
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

this error appears after i put in: sudo apt-get install sun-java6-jre sun-java6-fonts sun-java6-plugin

i'm a newb to root :(

---

### Post by Thura on 2009-04-10
Open a terminal and run "sudo dpkg --configure -a"
Then if there is any error, show us the whole messages.

---

### Post by maheshasolkar on 2009-04-10
Something interrupted the installation process and the package manager thinks there may be broken packages/dependencies. These are typically corrected by running what the error message suggests. You can run the following in in the terminal:

```
  sudo dpkg --configure -a
```

When asked for a password, input your password.

---

### Post by deranged_typist on 2009-04-10
unit420-a@unit420-a-desktop:~$ sudo dpkg --configure -a
[sudo] password for unit420-a: 
Setting up java-common (0.28ubuntu3) ...

is there more i must do, or should java be working correctly?

heh, need to google some terminal tutorials or something.

---

### Post by maheshasolkar on 2009-04-10
Is dpkg still running or it is done? You can tell it is done when the prompt reappears. Your prompt is 'unit420-a@unit420-a-desktop:~$'. Wait until dpkg is done. Then make sure that there are no errors reported on the terminal. If there are, post them here.

---

### Post by deranged_typist on 2009-04-10
unit420-a@unit420-a-desktop:~$ sudo dpkg --configure -a
[sudo] password for unit420-a: 
Setting up java-common (0.28ubuntu3) ...

unit420-a@unit420-a-desktop:~$ 

thats it...my update manager appeared and java installed and all, but i restarted firefox and nothing...  nothing else has given me this trouble and i've been doing pretty good.  i've had linux up and running with my partition (which is for school purposes only) for about 6 months now...*sigh*

---

### Post by Fourgun on 2009-04-11
does anybody know if unistall java would work to get rid of error message?

---

### Post by Thura on 2009-04-11
Umm, does "dpkg --configure -a" not work ?
If not, plz post the errors ...

To uninstall java, 
```
sudo apt-get remove --purge sun-java6-jre sun-java6-fonts sun-java6-plugin
```

---

