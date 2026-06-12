---
title: "[Debian] Dropbox runs in background, but no indicator panel icon"
date: 2015-01-20
forum: Debian
---

### Post by parker-hugh on 2015-01-20
Hi, I just installed Debian 7.8 on ASUS Eee Box EB1501P. Then installed Dropbox.

Dropbox runs in the background and syncs ok, but does not show the indicator panel icon on desktop. I tried enabling icons on desktop but still no Dropbox indicator panel icon.

This is the steps I did to install .... (I have managed to install Dropbox on previous occasions on other laptops and the indicator panel icon displayed ok) not sure what is the problem.

[https://www.dropbox.com/install?os=lnx](https://www.dropbox.com/install?os=lnx)

download 'dropbox_1.6.2_amd64.deb'

terminal window...

```
    $ cd /home/hugh/Downloads

    $ su -c 'dpkg -i dropbox_1.6.2_amd64.deb'
```

terminal output...

   ```
 root@EEE-BOX-DEBIAN:/home/hugh/Downloads# su -c 'dpkg -i dropbox_1.6.2_amd64.deb'
    Selecting previously unselected package dropbox.
    (Reading database ... 129220 files and directories currently installed.)
    Unpacking dropbox (from dropbox_1.6.2_amd64.deb) ...
    Setting up dropbox (1.6.2) ...
    Please restart all running instances of Nautilus, or you will experience problems. i.e. nautilus --quit
    Dropbox installation successfully completed! You can start Dropbox from your applications menu.
    Processing triggers for desktop-file-utils ...
    Processing triggers for gnome-menus ...
    Processing triggers for hicolor-icon-theme ...
    Processing triggers for man-db ...
    root@EEE-BOX-DEBIAN:/home/hugh/Downloads# 
```

I then started Dropbox from the applications menu and received a message (same message as I received on previous successful dropbox installs) ...

Dropbox message states...

In order to use Dropbox, you must download the proprietary daemon.
Note: python-gpgme is not installed, we will not be able to verify binary signatures.

Clicked OK

Msg window states... Downloading Dropbox

Dropbox setup window appears for login.

Looks good, so it must download the proprietary daemon & python-gpgme in the background.

I have used this install method in the past without any problems so not sure what has went wrong here.

I ran following code to see if I could start dropbox or check the status...


  ```
  hugh@EEE-BOX-DEBIAN:~$ ~/bin/dropbox.py start
    bash: /home/hugh/bin/dropbox.py: No such file or directory
    hugh@EEE-BOX-DEBIAN:~$ ~/bin/dropbox.py status
    bash: /home/hugh/bin/dropbox.py: No such file or directory
    hugh@EEE-BOX-DEBIAN:~$ 
```

any help would be appreciated.

EDIT: Also any feedback on whether this is best method to install Dropbox in Debian or is there a better method I could use? if there is, how would I uninstall dropbox using the terminal as I'm still fairly new to Linux.

P.S. I have posted this on Debian forums but didn't get any reply so thought I would try ubuntuforums as I have had good advice here in the past.

EDIT: I found following hit on google...

[https://www.dropbox.com/en/help/246](https://www.dropbox.com/en/help/246)

It suggests to add the following line to /etc/apt/sources.list....

deb [http://linux.dropbox.com/debian](http://linux.dropbox.com/debian) squeeze main

would I then run ? ....

```
apt-get install nautilus-dropbox
```

Is this a better way to install Dropbox? if so how would I uninstall existing Dropbox?  I'm still quite new to Linux and would like to install Dropbox the correct way to ensure I get udates going forward.

---

### Post by kerry_s on 2015-01-20
> how would I uninstall existing Dropbox?

su
apt-get purge dropbox  <-uninstall dropbox
apt-get autoremove  <- clean up anything installed with dropbox, dependencys.

---

### Post by parker-hugh on 2015-01-20
> **kerry_s said:**
> su
apt-get purge dropbox  <-uninstall dropbox
apt-get autoremove  <- clean up anything installed with dropbox, dependencys.

Thanks for feedback, I'll try that. What do you this is the best way to re-install Dropbox, is the instructions I found here the best way ....

[https://www.dropbox.com/en/help/246](https://www.dropbox.com/en/help/246)

and then run....

```
apt-get install nautilus-dropbox
```

Any advice would be appreciated

---

### Post by kerry_s on 2015-01-20
sorry, don't use dropbox, but that is the way they recommend, so it must work the best.

---

### Post by Kurt_Alan on 2015-05-16
> **vasa1 said:**
> Click on the "Report" button in the lower left corner of your post (or anyone else's) and ask for what you want.

I did so. Thanks.

---

### Post by bapoumba on 2015-05-17
*Thread moved to **Debian**.*

installing nautilus-dropbox has always worked for me (on Ubuntu).

---

### Post by buzzingrobot on 2015-05-17
Dropbox rebuilt their installer app based on QT. (If it was a bright blue vertical rectangle when you used it, that's the one.)

Apparently, the icon will not show up unless the system Dropbox is running on has exactly the same version of QT installed.

---

