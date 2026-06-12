---
title: "Mount from desktop shortcut"
date: 2021-08-24
forum: Desktop Environments
---

### Post by stager2 on 2021-08-24
I run in terminal the mount commandl:
```
mount /dev/.....
```
It's works.

I create desctop shortcut with same command. It does not wrk.

Why?

---

### Post by vanadium on 2021-08-24
I dont know. Maybe the format of the desktop shortcut is wrong. Can't really tell from here.

---

### Post by ActionParsnip on 2021-08-24
Users cannot mount devices so it'll need sudo adding to the command, this will give the access required. What do you mean by a desktop shortcut to the same command? Did you make a script to mount and then make a desktop icon to run the script?
Details please......

---

### Post by grahammechanical on 2021-08-24
Does your desktop icon have on it a purple circle with a white arrow pointing upwards to the right? If it does not then right click the icon and select Allow Launching. We need to give the code embedded in the icon permission to run or execute.

Regards

---

### Post by stager2 on 2021-08-25
Ok, concretely:
```
stager@stagerLaptop:~$ sshfs 192.168.10.10:/home/www-data /home/stager/mnt/home.www-data
```
works.
Desktop shortcut:
```

#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Icon=mate-panel-launcher
Exec=sshfs 192.168.10.10:/home/www-data /home/stager/mnt/home.www-data
Name=sshfs 192.168.10.10

```
not works.
Yes, terminal opens, prompt to password from 192.168.10.10 appears. After entering a password, terminal closing. Mounting not happen.

The same thing in ```
sudo mount ...
```

---

### Post by vanadium on 2021-08-25
> **ActionParsnip said:**
> Users cannot mount devices so it'll need sudo adding to the command, this will give the access required. 
Users can mount if they are granted permission to do so.

This time you have provided information as clear and specific as it can get.

What you do with your launcher is opening a terminal, setting up the mount in FUSE and then closing the terminal. Is it possible that all processes are terminated when the terminal from where you launch is closed? You could try by giving the mount command in the terminal. If you then close that terminal, is the mount preserved?

You also could try the following Exec= line in the launcher:

```
Exec=sh -c "sshfs 192.168.10.10:/home/www-data /home/stager/mnt/home.www-data ;  bash"
```

This will keep the terminal open on a terminal prompt. If the mount is there until you quit that terminal, then there is the reason why it did not work.

(Edit) [Here](https://unix.stackexchange.com/questions/629827/launcher-sshfs-mount-disappears-after-terminal-is-closed) a user reports that such connection indeed is closed when closing the terminal (and accordingly all processes launched from it), so there will be no need for you to test that. Unfortunately no answer there.

You could attempt to use "nohup". This disconnects the process entirely from the terminal where it is launched. Alternatively, and perhaps safer, is to "disown" the process after the password has been given and the connection is established. 

I would probably go for a password less solution using an ssh key file. Then you could launch the command with "Terminal=false" in the launcher. That way, clicking the launcher would establish the mount silently.

These mounts are visible in the file manager, and can be stopped there anytime.

---

### Post by stager2 on 2021-08-25
> **vanadium said:**
> 
You also could try the following Exec= line in the launcher:

```
Exec=sh -c "sshfs 192.168.10.10:/home/www-data /home/stager/mnt/home.www-data ;  bash"
```


nothing changes

> **vanadium said:**
> 
(Edit) [Here]("https://unix.stackexchange.com/questions/629827/launcher-sshfs-mount-disappears-after-terminal-is-closed") a user reports that such connection indeed is closed when closing the terminal (and accordingly all processes launched from it), so there will be no need for you to test that. Unfortunately no answer there.

Of course not. Why should it be like this?
Certainly mounting keep after the terminal close.

---

### Post by vanadium on 2021-08-26
> **stager2 said:**
> nothing changes
Of course not. Why should it be like this?
Certainly mounting keep after the terminal close.
Your mileage may vary. Good luck!

---

