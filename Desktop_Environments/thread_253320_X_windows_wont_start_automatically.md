---
title: "X windows wont start automatically"
date: 2006-09-08
forum: Desktop Environments
---

### Post by TheBishopOfSoho on 2006-09-08
Hi there. Have had very few problems with my Ubuntu installation, but this morning when I booted up, instead of the graphical login it now goes to the command prompt login. To get X started I have to use the command "startx" and it runs then, but for some reason the system wont boot it automatically. Can anyone help me fix this?

---

### Post by mority on 2006-09-08
The default runlevel in Ubuntu is 2. So could you check if there is a symlink in /etc/rc2.d to /etc/init.d/gdm like this:
```

# ls -l /etc/rc2.d/*gdm
lrwxrwxrwx 1 root root 13 2006-06-07 19:57 /etc/rc2.d/S13gdm -> ../init.d/gdm

``` 
If not, create this link like this:
```

# ln -s /etc/init.d/gdm /etc/rc2.d/S13gdm

``` 
I assume, that you previously got root priviledges with
```

sudo -s

```

---

### Post by TheBishopOfSoho on 2006-09-08
I did your first command, the ls one, and got this reply:

```
lrwxrwxrwx 1 root root 13 2006-08-22 08:31 /etc/rc2.d/S13gdm -> ../init.d/gdm
```

What now?

---

### Post by mority on 2006-09-08
Try to restart your system and execute
```

sudo /etc/init.d/gdm

``` by hand.

What exactly is happening when you boot up your machine? Are there any error messages?
After you logged in in textmode, what does the command
```

runlevel

```
return?

---

### Post by TheBishopOfSoho on 2006-09-09
Hi, sorry about the delay, was waiting for an email to say someone replied but got nothing! Anyway ran your first command "sudo /etc/init.d/gdm" and nothing seemed to happen. No errors, alerts anything, and when I run runlevel I get runlevel 5 as output.
This is starting to drive me mad. I didnt do anything to change startup. All I do is make sure all updates are installed. Can anyone please tell me why the desktop manager no longer loads automatically?

---

### Post by mority on 2006-09-09
Sorry, the gdm command was wrong. Use:
```

sudo /etc/init.d/gdm start

```

All my Ubuntu systems are in runlevel 2 when I work with X starting up autmatically, yours is in runlevel 5. Maybe that is the problem. Could you post the content of /etc/inittab?

---

