---
title: "[SOLVED] ICEauthority, and just a blue screen after."
date: 2008-12-07
forum: Desktop Environments
---

### Post by Sohlman on 2008-12-07
Hi, I have bad problem.
First i got this message.> "User's $HOME/.dmrc file is being ignored. This prevents the default sessin and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."
 then i did```
sudo chown user:user /home/user/.dmrc
chmod 644 /home/calle/.dmrc
sudo chown -R calle /home/calle
```Then when i restarted the computer i got> Could not update ICEauthority file /home/calle/.ICEauthority. and >  **"Norwegian"** Det er problemer med konfigurasjonstjeneren. (/usr/lib/libgconf2-4/gconf-sanity-check-2 avsluttet med status 256)  
**"English"** There is a problem with the configurationservice. (usr/lib/libgconf2-4/gconf-sanity-check-2 ended with state 256)
There is only one option "exit", after that i only see a blue screen and my mouse. i could press CTRL-ALT-F3 to open console login, i enter username and password and im in the desctop console/terminal, but don't know what write after that...

So pleas any help i cant use the computer, now im using a second pc to find the solution. and also pleas say what information you need to help me fix the problem.

---

### Post by Sohlman on 2008-12-11
Anyone pleas, I need help.
I can't use the computer at all. All I see is a blue screen after the warnings has gone...

So Pleas!!! help. :???:

I have no idea of what to search for on google or other sites...
So everyone could help me here, i tried to search for ICEauthority but with no luck...

---

### Post by taurus on 2008-12-11
What's the output of this command from a terminal?

```
ls -la /home/calle/.ICEauthority
```
Looks like you have two different users on your machine:  user & calle.

---

### Post by dabl on 2008-12-11
Doing root operations in your /home/user folder is a very bad idea -- it can indeed lock you out of your login.  Whatever was wrong in the first place was probably made worse by these:

> sudo chown user:user /home/user/.dmrc
chmod 644 /home/calle/.dmrc
sudo chown -R calle /home/calle

If it were my system, I would boot a Live CD, get my data saved off/backed up, and then reinstall the OS.

Alternatively, you may be able to boot Recovery Mode, and set up a new user account, and use that, going forward.  Then use the Live CD to get your data files (but nothing else!) out of your old user folder.  Warning - if you saved any data in your user folder with root privileges attached, then it may bork up your new folder to copy that data.

---

### Post by Sohlman on 2008-12-11
The ```
ls -la /home/calle/.ICEauthority
``` gave me permission denied

I don't have any files on the computer that I need. so i cant lose anything...
I do have a cd with this download "[Ubuntu.com/Download]("http://www.ubuntu.com/getubuntu/download")"

---

### Post by taurus on 2008-12-11
Try

```
sudo chown calle:calle /home/calle/.ICEauthority
sudo chmod 600 /home/calle/.ICEauthority
```
Now see if you can log in as calle.

---

### Post by Sohlman on 2008-12-11
```
Sudo chown calle:calle /home/calle/.ICEauthority
``` first it wantedt password, i wrote the p-word but it rejected it, then i did the other chown 600, it just run with no feed back. the i tried chown calle:calle agin and it gave: No such file or directory, so i don't know what happend

---

### Post by taurus on 2008-12-11
Are you currently logged in as user?  Does user have root privilege (can user use sudo)?

Otherwise, boot into recovery mode from GRUB menu and change the ownership and permission of /home/calle/.ICEauthority.

---

### Post by Sohlman on 2008-12-11
In the terminal it say ```
calle@calle-desktop:/$ 
```
and i loged in with 
Calle-desktop login: calle
Password: ********
 then im in

---

### Post by taurus on 2008-12-11
Post the output of this command from a prompt then.

```
ls -la
```
What will list the permissions and ownerships of all your files and directories in your $HOME.

---

### Post by Sohlman on 2008-12-11
Now im in bot menue i have 5 oprions...
```
Ubuntu 8.10, Kernel 2.6.27-9-generic
Ubuntu 8.10, Kernel 2.6.27-9-generic /recovery mode)
Ubuntu 8.10, Kernel 2.6.27-7-generic
Ubuntu 8.10, Kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, memtest86+
```

what shall i chose

---

### Post by taurus on 2008-12-11
> **Sohlman said:**
> Now im in bot menue i have 5 oprions...
```
Ubuntu 8.10, Kernel 2.6.27-9-generic
**[COLOR="Blue"]Ubuntu 8.10, Kernel 2.6.27-9-generic (recovery mode)[/COLOR]**
Ubuntu 8.10, Kernel 2.6.27-7-generic
Ubuntu 8.10, Kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, memtest86+
```

what shall i chose

Look at my previous reply first.  Otherwise, recovery mode is in blue.

---

### Post by Sohlman on 2008-12-11
CODE]drwxr-xr-x 3 root root 4096 2008-11-11 22:52 home[/CODE] do you meen this one?

i cant scroll up the list...
Just the lower part of screen

---

### Post by taurus on 2008-12-11
I mean your $HOME--/home/calle.  /home is not the same as $HOME.

```
ls -la ~ | more
```

p.s.  You are in a console, right.  Just pipe it through more.  Hit Space key for the next 24 lines.

---

### Post by Sohlman on 2008-12-11
This is what it look like [http://home.online.no/~sohlman/Bilder/root.jpg](http://home.online.no/~sohlman/Bilder/root.jpg)
on the first one.

---

### Post by Sohlman on 2008-12-11
found it!
```
calle@calle-desktop:/home$ ls -la
drwxr-xr-x 3 root root 4096 2008 11-11 22:52 .
drwxr-xr-x 20 root root 4096 2008-12-01 16:45 ..
drw-r-r-- 55 calle admin 4096 2008-12-02 21:21 calle
```

---

### Post by taurus on 2008-12-11
> **Sohlman said:**
> found it!
```
calle@calle-desktop:/home$ ls -la
drwxr-xr-x 3 root root 4096 2008 11-11 22:52 .
drwxr-xr-x 20 root root 4096 2008-12-01 16:45 ..
**[COLOR="Blue"]drw-[/COLOR]**r-r-- 55 calle admin 4096 2008-12-02 21:21 calle
```

```
sudo chmod 755 /home/calle
ls -la /home
```

---

### Post by Sohlman on 2008-12-11
Ty it worked and changed it to drwxr-xr-x that i belive is good...

---

### Post by taurus on 2008-12-11
Reboot and see if you can log in to calle from GUI login screen.

---

### Post by Sohlman on 2008-12-11
GUI do that meen the normal start up? 
just before i do any thing stupid

---

### Post by taurus on 2008-12-11
Just boot normally and at the GUI log in screen, log in as calle with the password and see if there is any more problem with your account.

---

### Post by Sohlman on 2008-12-11
Im so glad, i can finaly use my computer again...
Thank you so much...:KS

---

### Post by taurus on 2008-12-11
So everything is peachy again with calle account.

---

### Post by Sohlman on 2008-12-11
Now i can log on normaly and i think everything is working...
So ty for you help.):P
or i see that the updates wont install...
i have 30 updates that wont install...

---

### Post by taurus on 2008-12-11
Post the outputs of these commands from a terminal.  Remember to close down the update-manager first before you run these two commands.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Sohlman on 2008-12-11
Tanks again, now my computer is alive again, what caused this problem was that I wanted to install some FPS games, but the computer didn't see my grapic card. and it still don't, I belive.

So I wrote some commands i read or was told to, but maybe i wasn't in the right folder for the commands. 

So do you know how to install or detect my grapic card.

---

### Post by taurus on 2008-12-11
What video card do you have?  What's the output of this command from a terminal?

```
lspci | grep VGA
```
Otherwise, look in System -> Administration -> Hardware Drivers to see if your graphic card is on the list.

---

### Post by Sohlman on 2008-12-11
The Hardware Drivers gave me: No proprietary drivers are in use on this system.

the lspci | grep VGA gave me: Intel Corporation 82865G integrated graphics controller (rev 02)

I remember that I have Intel graphic controler and on Windows it where called Intel Extreme2 grapich controler  and something abput some chips
Do this mean that its fixed then?

---

