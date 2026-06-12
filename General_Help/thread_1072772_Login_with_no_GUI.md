---
title: "Login with no GUI"
date: 2009-02-17
forum: General Help
---

### Post by RedSingularity on 2009-02-17
I know that if i press Ctl+alt+F1 i can get to the terminal login instead of the graphical one.  My question is, can i login with the textual interface and then switch to the graphical one once i login?

And also can i restart the GNOME desktop from within the terminal?

---

### Post by Titan8990 on 2009-02-17
To stop graphical login at startup you need to prevent gdm from booting at startup.

The syntax is different depending on the distro but I believe for Ubuntu it is:

sudo rc.update -f gdm


Then to start gdm from TTY: sudo /etc/init.d/gdm start


Or to use a more widespread startx method, make a file in your home folder (if it doesn't already exist) called .xinit

Inside of it put:

exec gnome-session


Then you should be able to start gnome with the startx command.

> And also can i restart the GNOME desktop from within the terminal?

Just hit CTRL+ALT+BACKSPACE twice. or: sudo /etc/init.d/gdm stop.

---

### Post by cariboo on 2009-02-17
@Titan8990

I believe you have a typo, th command should be:

```
sudo update-rc.d -f gdm
```

Jim

---

### Post by mb_webguy on 2009-02-17
You could also add a console login entry to your GRUB menu.

Open your GRUB menu file with "sudo gedit /boot/grub/menu.lst".  Copy the main entry for Ubuntu from inside the Automagic kernels section, and paste it either before or after that section.  Add the word "text" to the end of the kernel line, and change the title to whatever you like.  Save and exit.

The next time you reboot, you'll have the option of booting into a basic shell prompt.

---

