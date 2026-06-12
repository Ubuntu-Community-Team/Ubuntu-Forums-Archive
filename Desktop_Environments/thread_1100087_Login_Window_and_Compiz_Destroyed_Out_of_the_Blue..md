---
title: "Login Window and Compiz Destroyed Out of the Blue..."
date: 2009-03-18
forum: Desktop Environments
---

### Post by richardcarter on 2009-03-18
Hi,

I've been using my computer nicely for awhile with no problems.  Then one day, I turned on the computer and instead of the traditional default Xubuntu login screen, it gives me a warning message stating "There was an error loading the theme human.  Couldn't find file /usr/share/gdm/themes/human/human.xml."  And then it takes me to this bland generic login screen called "Gnome Desktop Manager" and it says "Debian" in giant letters.  And I have to select an "XFCE" session to get things to start properly.  Why would xubuntu/xfce use the "Gnome Desktop Manager"?  How can I make the "XFCE Desktop Manager" default?


So then once it logs in, none of my compiz-fusion effects work anymore.  I've tried reconfiguring them using the guide I used originally, [http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/](http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/) , but it won't work.  It's still using some other window manager, even after I run the command to use compiz.  Ugggg.

I loved my system, but it's so annoying that automatic updates can destroy so much hard work and literally hours upon hours it took me to configure my system.  This seems to be a giant flaw in linux.  It's not intelligent enough to detect that you made customized changes and won't work with them. It just replaces them, leaving you confused and frustrated.

Can someone please help me?

---

### Post by richardcarter on 2009-03-18
bump :(

---

### Post by miegiel on 2009-03-19
Try :
```
sudo apt-get update 
sudo apt-get upgrade 
```
If that doesn't give any errors and doesn't help, then try reinstalling the human theme```
sudo apt-get install human-theme
```

WARNING
```
sudo apt-get remove human-theme
``` Will also uninstall "ubuntu-desktop" and "ubuntu-artwork".

---

### Post by richardcarter on 2009-03-19
> **miegiel said:**
> Try :
```
sudo apt-get update 
sudo apt-get upgrade 
```
If that doesn't give any errors and doesn't help, then try reinstalling the human theme```
sudo apt-get install human-theme
```

WARNING
```
sudo apt-get remove human-theme
``` Will also uninstall "ubuntu-desktop" and "ubuntu-artwork".

Thanks for the response!

I didn't do a single thing but restart my computer (after I'd restarted it five times) and now the "Gnome Desktop Manager" screen says it's missing the "Xubuntu.xml" theme.  And now the background is xubuntu blue, instead of ubuntu brown/orange.  How can I get the xubuntu theme? 

And for some reason, compiz is working fine now.

I downloaded some gdm themes and tried to install them by dragging the tar.gz file to the Applications>Settings"Login Window box under the local tab.  It asks me if I want to install the theme.  When I click yes, it says "Some error occurred while installing the theme."  If I try to navigate to the file, it doesn't show up.  Then I tried adding the theme to my /usr/share/themes/gdm folder.  no luck.  then i tried /home/username/.themes and that didn't work either.  What is going on?

---

### Post by richardcarter on 2009-03-19
> **miegiel said:**
> Try :
```
sudo apt-get update 
sudo apt-get upgrade 
```
If that doesn't give any errors and doesn't help, then try reinstalling the human theme```
sudo apt-get install human-theme
```

WARNING
```
sudo apt-get remove human-theme
``` Will also uninstall "ubuntu-desktop" and "ubuntu-artwork".

Oh and also, when I do the sudo apt-get update 
sudo apt-get upgrade thing, it doesn't add or change anything.

---

### Post by richardcarter on 2009-03-19
> **miegiel said:**
> Try :
```
sudo apt-get update 
sudo apt-get upgrade 
```
If that doesn't give any errors and doesn't help, then try reinstalling the human theme```
sudo apt-get install human-theme
```

WARNING
```
sudo apt-get remove human-theme
``` Will also uninstall "ubuntu-desktop" and "ubuntu-artwork".

and I just tried "sudo apt-get install xubuntu-theme" and of course it doesn't exist.

---

### Post by richardcarter on 2009-03-19
I tried reinstalling GDM from synaptic and it was almost done and then displayed the following error:

"E: /var/cache/apt/archives/gdm_2.20.8-0ubuntu3_i386.deb: unable to stat `./usr/share/gdm/themes' (which I was about to install)"

Uggggg.  In the terminal it says something about a broken pipe and an Input/Output error.

---

### Post by richardcarter on 2009-03-19
Also, I tried to use a terminal to reinstall gdm and got the following:

```
richard@richard-desktop:~$ sudo apt-get install gdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdm is already the newest version.
The following packages were automatically installed and are no longer required:
  libcanberra-gtk-module libosp5 w3c-dtd-xhtml compizconfig-backend-gconf
  libcanberra-gtk0 libgnome-window-settings1 libcanberra0
  xulrunner-1.9-gnome-support
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
richard@richard-desktop:~$ 
```

---

### Post by miegiel on 2009-03-19
Did you run the sugested```
sudo apt-get autoremove
```


and ```
sudo apt-get install xubuntu-desktop
``` does exist

paste ```
sudo apt-get install xubu
``` into the terminal and hit the TAB key twice ;)

---

