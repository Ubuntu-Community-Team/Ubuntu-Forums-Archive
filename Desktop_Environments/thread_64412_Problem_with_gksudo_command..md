---
title: "Problem with gksudo command."
date: 2005-09-10
forum: Desktop Environments
---

### Post by celluloid on 2005-09-10
Hey.
When trying to run a program in XFCE4 or GNOME as root or sudo i get this error.

Failed to run rox:
 Unable to copy the user's Xauthorization file.

I know the password is correct as i can sudo or su root in a terminal fine.
It's in relation to running programs such as synaptic, and other programs that require root permissions. 'gksudo'

I have tried 'passwd' and 'passwd root' in a terminal and reset the password but it doesnt seem to help me.

---

### Post by SFN on 2005-09-11
Remove the Xauthority file.

```
sudo rm ~/.Xauthority
``` 

Then log out and log back in. That should re-create your .Xauthority file and all should be well after that.

---

### Post by celluloid on 2005-09-11
[QUOTE=SFN]Remove the Xauthority file.

```
sudo rm ~/.Xauthority
``` 

Then log out and log back in. That should re-create your .Xauthority file and all should be well after that.[/QUOTE]
 eeek. doesn't seem to work :S

grant@xubuntu:/$ sudo rm ~/.Xauthority
rm: cannot remove `/home/grant/.Xauthority': No such file or directory

---

### Post by celluloid on 2005-09-12
Does anyone know what to do here? i cant find anything?

---

### Post by recce101 on 2005-09-12
If you bring up the Run Program window and type "gksudo rox" does it work then? Or did you try deleting the custom launcher icon and creating a new one?

I've had that happen a couple of times and a full reboot (not just log out-in) did the trick.

---

### Post by celluloid on 2005-09-12
[QUOTE=recce101]If you bring up the Run Program window and type "gksudo rox" does it work then? Or did you try deleting the custom launcher icon and creating a new one?

I've had that happen a couple of times and a full reboot (not just log out-in) did the trick.[/QUOTE]
 Yes, i've tried it from the Run Program window and tried creating a new launcher. I've logged in and out, full restart, boot into single user and tried 'passwd' and 'passwd root' and created/reset passwords. Nothing seems to work. :S

---

### Post by sotek on 2005-09-24
I had that problem.

my .Xauthority file was owned by root - a sudo chown and it was fixed.

---

