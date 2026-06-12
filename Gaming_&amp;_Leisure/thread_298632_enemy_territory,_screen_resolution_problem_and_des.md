---
title: "enemy territory, screen resolution problem and desktop icon problem"
date: 2006-11-13
forum: Gaming &amp; Leisure
---

### Post by misfito on 2006-11-13
Hi, I having some problems with ET, it runs great but every time I quit the game my screen resolution is messed up and I have to reset it.
I'm also having another issue, I have been trying to put an icon of ET in the desktop without any success. I've tried with alacarte menu editor and create launcher but both failed.:-| (well alacarte supposed to add a menu launcher, it did; but when I click on it, it does do anything!) I have to open the folder with ET every time to play.

---

### Post by Mohit on 2006-11-13
Try this command in Terminal 

code- sudo dpkg-reconfigure xserver-xorg

may be this will work

Mohit

---

### Post by qrm on 2006-11-13
have the exact same prob with resolution, I solved it by setting the ingame resolution the same as desktop resolution

---

### Post by misfito on 2006-11-15
What about the icons? There's anybody who can tell me how to make a icon of ET to put on the desktop that actually works?

---

### Post by B0rsuk on 2006-11-15
> **misfito said:**
> What about the icons? There's anybody who can tell me how to make a icon of ET to put on the desktop that actually works?

just type

```
et
```
at terminal. It's most convenient if you use yakuake.

---

### Post by Completenutter2 on 2006-11-15
> **misfito said:**
> What about the icons? There's anybody who can tell me how to make a icon of ET to put on the desktop that actually works?

Right-click on your desktop
Select 'Create Launcher...'
Type: 'Application'
Name: 'Enemy Territory'
Command: 'et'
Comment: 'Play ET'

Select an icon if you want, then press 'OK'

Double click to play :)

---

### Post by misfito on 2006-11-16
I've done that before but without any success...](*,) 

Right-click on your desktop
Select 'Create Launcher...'
Type: 'Application'
Name: 'Enemy Territory'
Command: 'et'
Comment: 'Play ET'

Select an icon if you want, then press 'OK'

Double click to play 

I click on the icon but nothing seems to happen.
Thank you anyways. :)

---

### Post by misfito on 2006-11-17
> **Mohit said:**
> Try this command in Terminal 

code- sudo dpkg-reconfigure xserver-xorg

may be this will work

Mohit


I tried that with an error that said: 

user@User-s-computer:~$ code- sudo dpkg-reconfigure xserver-xorg
bash: code-: command not found

Thanx anyways

---

### Post by B0rsuk on 2006-11-17
Ok, please type ```
et
``` at terminal and see if it works. If it doesn't, you should get error messages. Post them here.

---

### Post by misfito on 2006-11-18
This is  what i got:


```
user@User-s-computer:~$ et
bash: et: command not found

```

I tried to enter the directory and run ET but, same error.

```
user@User-s-computer:~$ cd enemy-territory 
user@User-s-computer:~/enemy-territory$ et
bash: et: command not found
user@User-s-computer:~/enemy-territory$ dir
CHANGES       etmain                                openurl.sh
Docs          et.x86                                pb
et            ET.xpm                                pbcl.db
et-2.60b.zip  EULA_Wolfenstein_Enemy_Territory.txt  pbsv.db
etded         from\ zip                             untitled\ folder
etded.x86     noquarter


```

---

### Post by Matt Yun on 2006-11-18
> I tried to enter the directory and run ET but, same error.

```
user@User-s-computer:~$ cd enemy-territory 
user@User-s-computer:~/enemy-territory$ et
bash: et: command not found
...


```

You're almost there... try this instead (changes in red):
```
user@User-s-computer:~$ cd enemy-territory 
user@User-s-computer:~/enemy-territory$ [COLOR="Red"]./[/COLOR]et
```

When you execute programs from the console (a.k.a. "command line"), the OS will look for the program in your default path.  In Ubuntu, the path is set to /bin, /sbin, /usr/bin, /usr/sbin, /usr/local/bin, /usr/local/sbin.

If you're trying to execute a file from the current working directory, you need to prepend the command with a "./" to override your default path settings.

Also, Enemy-Territory for Linux does not come with an icon prepackaged with the icon.  If you're making an icon for your desktop, you need to provide your own graphic.  I'm attaching the one I that I use (from True Combat: Elite).  When you set the application path for your desktop icon, be sure to use the full pathname ie. /home/user/enemy-territory/et

---

### Post by misfito on 2006-11-18
> **Matt Yun said:**
> You're almost there... try this instead (changes in red):
```
user@User-s-computer:~$ cd enemy-territory 
user@User-s-computer:~/enemy-territory$ [COLOR="Red"]./[/COLOR]et
```

When you execute programs from the console (a.k.a. "command line"), the OS will look for the program in your default path.  In Ubuntu, the path is set to /bin, /sbin, /usr/bin, /usr/sbin, /usr/local/bin, /usr/local/sbin.

If you're trying to execute a file from the current working directory, you need to prepend the command with a "./" to override your default path settings.

Also, Enemy-Territory for Linux does not come with an icon prepackaged with the icon.  If you're making an icon for your desktop, you need to provide your own graphic.  I'm attaching the one I that I use (from True Combat: Elite).  When you set the application path for your desktop icon, be sure to use the full pathname ie. /home/user/enemy-territory/et

Thanx :D I just used the./et and it worked without the need of adding the whole path. I also use the icon:

---

### Post by misfito on 2006-11-18
I got another thread that I would really like to get solved:
[http://ubuntuforums.org/showthread.php?t=295373](http://ubuntuforums.org/showthread.php?t=295373)
I don't know if you (Matt Yun) or some1 else could help me.

---

