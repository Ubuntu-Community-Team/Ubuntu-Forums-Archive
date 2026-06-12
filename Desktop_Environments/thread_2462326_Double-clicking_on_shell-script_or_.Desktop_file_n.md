---
title: "Double-clicking on shell-script or .Desktop file no longer works?"
date: 2021-05-18
forum: Desktop Environments
---

### Post by victorhooi on 2021-05-18
I am trying to write a simple wrapper around FreeRDP, so that a user can launch this when double-clicking on it within Ubuntu (GNOME).

However, double-clicking on either a Bash shell script, or .desktop file no longer seems to work in Ubuntu.

Is this intended behaviour?

(There's a discussion of this [https://askubuntu.com/questions/1184558/ubuntu-19-10-cannot-run-desktop-files](https://askubuntu.com/questions/1184558/ubuntu-19-10-cannot-run-desktop-files) - apparently it broke in Ubuntu 19.10, and hasn't been fixed since?)

Is there any way to get it working, or some way to run a command in a script file, by double-clicking on it within Ubuntu?

---

### Post by grahammechanical on 2021-05-18
> Is this intended behaviour?

If it is anything to do with Gnome then it is most definitely intentional by the Gnome developers. I have one application icon on my desktop and when I upgraded from 18.04 to 20.04 it lost the ability to launch the application until I did a right click and selected Allow Launching. Can you not do the same?

Regards

---

### Post by ActionParsnip on 2021-05-19
If you put the file in
```

/usr/share/applications

```
You should be able to launch it from the ALT+F2 dialogue / search for it just like an application

---

### Post by yancek on 2021-05-20
This is deliberate by the Gnome developers.  See the link below for a detailed explanation.

[https://www.omgubuntu.co.uk/2018/01/gnome-desktop-icons-removed-3-28](https://www.omgubuntu.co.uk/2018/01/gnome-desktop-icons-removed-3-28)

1 methods of doing this are explained at the link below.

[https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux)

Another option is to install the following extension;  ```
 ]sudo apt install gnome-shell-extension-desktop-icons 
```

I used the last option which worked as advertised.

---

### Post by yancek on 2021-05-20
This is deliberate by the Gnome developers.  See the link below for a detailed explanation.

[https://www.omgubuntu.co.uk/2018/01/gnome-desktop-icons-removed-3-28](https://www.omgubuntu.co.uk/2018/01/gnome-desktop-icons-removed-3-28)

1 methods of doing this are explained at the link below.

[https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux)

Another option is to install the following extension;  ```
 ]sudo apt install gnome-shell-extension-desktop-icons 
```

I used the last option which worked as advertised.

> You should be able to launch it from the ALT+F2 dialogue / search for it just like an application 				 

First thing I tried, didn't work but I can't remember exactly the error.

---

### Post by monkeybrain20122 on 2021-05-21
> **victorhooi said:**
> I am trying to write a simple wrapper around FreeRDP, so that a user can launch this when double-clicking on it within Ubuntu (GNOME).

However, double-clicking on either a Bash shell script, or .desktop file no longer seems to work in Ubuntu.

Is this intended behaviour?

(There's a discussion of this [https://askubuntu.com/questions/1184558/ubuntu-19-10-cannot-run-desktop-files](https://askubuntu.com/questions/1184558/ubuntu-19-10-cannot-run-desktop-files) - apparently it broke in Ubuntu 19.10, and hasn't been fixed since?)

Is there any way to get it working, or some way to run a command in a script file, by double-clicking on it within Ubuntu?

Double click script works here (if you set preferences in nautilus and of course set file to executable) but .desktop files don't. Ubuntu 20.04. One alternative is to use nemo as your file manager. Install nemo  and run this in the terminal
```
xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search
```

To reverse, go to ~/.config/mimeapps.list and remove this line in the [Default Applications] section.
```
inode/directory=nemo.desktop 
```

If you find that nemo doesn't refresh itself as I have in one of my laptops, add this line to /etc/sysctl.conf  and reboot
```
fs.inotify.max_user_watches=524288
```

---

