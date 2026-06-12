---
title: "Razer Orbweaver Chroma"
date: 2020-06-16
forum: Gaming &amp; Leisure
---

### Post by motokohutt on 2020-06-16
Hello there, newbie to Ubuntu really trying my darndest to get into the new operating system. Moved over to Ubuntu because I could not stand how restrictive and slow Windows 10 was, however being a gamer I have a bunch of gaming peripherals and one is the Razer Orbweaver Chroma. However I just can't seem to get any of the software to work with it enabling me to edit the keys. I have tried Razer Genie but it is not supported and I have no idea how to add support. I have tried Keyboarding Master but I can not get it to install, here is the things I have tried in that regard's.

I tried:
sudo kbmaster-pre4_0.4.4-linux-installer.run
and I get error : command not found

I tried:
sudo bash kbmaster-pre4_0.4.4-linux-installer.run
and I get error : cannot execute binary file

I tried running the run file through the Ubuntu GUI and I get "This program requires root privelages" so I watched a video on youtube how to become "superuser" but that didn't work ether.

I even tried changing the executable function of the file using chmod but nope nothing.

So I was wondering, does anyone have any experience with getting this running? Or maybe even alternatives I could try to program my Razer Orbweaver Chroma? I really don't wan't to have to crawl back to windows T_T

---

### Post by CatKiller on 2020-06-16
Razer do not make their hardware work with Linux. In those situations some users are able to reverse engineer things to make them work, depending on access, interest, and technical skill. There is every chance that your Razer hardware will never function, and Razer don't really care about that.

To run a program in a directory that isn't one of the directories specified in your PATH (which are searched automatically so that you don't have to type them in) you need to specify the path. The path to "the directory I'm in now" is "." just as "the directory above this one" is "..". So to run an executable in the current directory you'd use ```
./nameofexecutable
```

---

### Post by motokohutt on 2020-06-16
When using this I just get the error prompt "This program requires root privilages. Please become superuser before executing the installer."

---

### Post by CatKiller on 2020-06-16
> **motokohutt said:**
> When using this I just get the error prompt "This program requires root privilages. Please become superuser before executing the installer."

And you were most of the way on the right track there; you'd use *sudo* to temporarily elevate your privileges.

```
sudo ./nameofexecutable
```

---

### Post by motokohutt on 2020-06-16
> **CatKiller said:**
> And you were most of the way on the right track there; you'd use *sudo* to temporarily elevate your privileges.

```
sudo ./nameofexecutable
```

Thanks for the reply, I figured it out in the end, for anyone else having this issue here is what worked for me, open the folder where your downloaded file is in the GUI. Right click and open the terminal in that directory (not needed just saves hassle) then enter as follows.

```
chmod 775 kbmaster-pre4_0.4.4-linux-x64-installer.run
sudo su
sudo ./kbmaster-pre4_0.4.4-linux-x64-installer.run
```

If the Installer does not add a shortcut to your desktop, the location of the installed file by default is #/opt/kbmaster-pre4_0.4.4/ the file can be ran through terminal by using this codeline.

```
sudo ./run.bash
```

---

