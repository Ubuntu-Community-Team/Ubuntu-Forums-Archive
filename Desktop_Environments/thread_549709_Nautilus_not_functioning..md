---
title: "Nautilus not functioning."
date: 2007-09-12
forum: Desktop Environments
---

### Post by sixblades on 2007-09-12
I have just done a clean install of Ubuntu Fiesty Fawn 7.04, and it appeared that everything was going perfectly, which was a big surprise (I've had numerous graphics card issues in the past). For some reason, nautilus decided to stop working.

The desktop does not respond to any kind of clicking, there are no icons, and I can't open up any folders (if I click on Places->Computer a new tab will appear on the bottom saying "Staring Computer..." for awhile, then it will simply disappear). I took a look at the system monitor and the main Nautilus process is running just fine (but with a significant amount of CPU usage...), and whenever I try to open a folder a new "nautilus" process will appear and won't leave, but the same thing happens as mentioned previously.

I've tried restarting the computer and reinstalling nautilus, but to no avail. Any suggestions would be greatly appreciated as I'm just not experienced enough to deal with file manipulation solely in terminal.

---

### Post by rocketship on 2007-09-12
What happens when you start Nautilus from a terminal?

While you're at it, try:
```
nautilus --check
```

---

### Post by sixblades on 2007-09-12
```
sean@sean-desktop:~$ gksudo nautilus
(nautilus:8373): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension

sean@sean-desktop:~$ gksudo nautilus

sean@sean-desktop:~$ nautilus --check
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_icon_factory
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_icon_factory

```
There's my console output; the first time resulted in the above text being printed, but I still could not access anything. I closed all nautilus processes, then entered the command again; no output, but no change either. The output for nautilus check is shown above as well.

---

### Post by rocketship on 2007-09-12
Why are you using ```
gksudo
```

FYI, I get the same error message when I run ```
gksudo nautilus
```
but I get a nautilus window.

Can you try just ```
sudo killall nautilus
nautilus
```

---

### Post by sixblades on 2007-09-13
```
sean@sean-desktop:~$ sudo killall nautilus
sean@sean-desktop:~$ nautilus
Initializing gnome-mount extension
```
No windows open or anything, there is simply no response, and I still can't open folders.
I checked the monitor and nautilus is indeed running.

---

### Post by sixblades on 2007-09-13
bump...

---

### Post by sixblades on 2007-09-13
Ok, right when I log in the desktop seems to function (I get icons that I can click on, although once I click on them the whole thing stops working). If no one knows of any solutions, are there any alternatives to nautilus that I could use?

---

### Post by divali on 2007-09-26
> **sixblades said:**
> Ok, right when I log in the desktop seems to function (I get icons that I can click on, although once I click on them the whole thing stops working). If no one knows of any solutions, are there any alternatives to nautilus that I could use?

I've got a similar problem and I'm using Thunar in the meantime.

---

### Post by Kwunman on 2007-10-02
Hey, I too am getting this problem, and would be grateful if anyone has any possible ideas in getting this working again.

Thanks,

Kwun-Man

---

### Post by divali on 2007-10-05
Still no solution?

---

### Post by outer_space on 2007-10-09
I get a bug where nautilus is not in the tray but it is in process monitor. If I kill the nautilus process, it starts a new one with a new pid.  I hope this is fixed when gutsy comes out.

---

