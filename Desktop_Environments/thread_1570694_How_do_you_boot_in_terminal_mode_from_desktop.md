---
title: "How do you boot in terminal mode from desktop"
date: 2010-09-08
forum: Desktop Environments
---

### Post by Derfdog on 2010-09-08
Hello
 
I know I have seen/read this someplace before but I cannot find it.
 
Just installed ver 10.4 -64 bit desktop, I want to make some modifications to the environment -- want to boot in terminal mode and not desktop (for fun and giggles), but if I open up a terminal, enter su- and password, then edit the (I hope) appropriate file it comes back and says that I do not have permission.
 
Is it because I installed the desktop version, or because I don't know enough linux to shoot myself in the foot yet?  
Should I go back to square one and install the server version then configure it so that it starts up the desktop?

---

### Post by jocko on 2010-09-08
> **Derfdog said:**
> Is it because I installed the desktop version, No.> **Derfdog said:**
> or because I don't know enough linux to shoot myself in the foot yet? Very likely.
> **Derfdog said:**
> but if I open up a terminal, enter  [COLOR=Red]su- and password[/COLOR], then edit the (I hope) appropriate file it comes back  and says that I do not have permission.
 
That's because the root user is not enabled in ubuntu, so the "su" command will not work.
Instead you prefix the command with "sudo" (for commands that run in the terminal) or gksudo (for graphical applications), and use your own password (but try not to shoot yourself in the foot).
So to edit a file with nano in the terminal:
```
sudo nano /path/to/filename
```Or to edit it with gedit:
```
gksudo gedit /path/to/filename
```To switch from the gui to a terminal (and leaving the gui running in the background), just press Ctrl+Alt+F1 (or F2-F6), and to switch back press Ctrl+Alt+F7.
To disable gnome from starting at boot, I guess you could remove the executable flag from /etc/init.d/gdm (haven't tested this myself):
```
sudo chmod -x /etc/init.d/gdm
```And to enable it again:
```
sudo chmod +x /etc/init.d/gdm
```

---

### Post by Derfdog on 2010-09-08
Thanks for the info.
So much to learn, so little time.

---

