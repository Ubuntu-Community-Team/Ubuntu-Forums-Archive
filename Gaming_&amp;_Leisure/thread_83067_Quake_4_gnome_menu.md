---
title: "Quake 4 gnome menu?"
date: 2005-10-27
forum: Gaming &amp; Leisure
---

### Post by DarkManX4lf on 2005-10-27
ok i installed quake4 perfectly fine to this dir "/media/D/Games/Quake4", i tried to make a short cut in the gnome applications>other menu but it wont launch... this is the command i use [B]media/D/Games/Quake4/quake4[B], what did i do wrong?

---

### Post by seethru on 2005-10-27
[QUOTE=DarkManX4lf]ok i installed quake4 perfectly fine to this dir "/media/D/Games/Quake4", i tried to make a short cut in the gnome applications>other menu but it wont launch... this is the command i use [B]media/D/Games/Quake4/quake4[B], what did i do wrong?[/QUOTE]

well, a few solutions you can try.

Put a dot infront of the current command
```
./media/D/Games/Quake4/quake4.
```
Link the executable so it's a global command
```
sudo ln /media/D/Games/Quake4/quake4 /usr/bin/quake4
```
and then change the current shortcut to just point to "quake4"

---

### Post by DarkManX4lf on 2005-10-27
ok i put a dot in front of the command and it still wont launch, so i then tried to create the link like you said and this is what happened when i tried to create it.

root@ubuntu:~# sudo ln /media/D/Games/Quake4/quake4 /usr/bin/quake4
ln: creating hard link `/usr/bin/quake4' to `/media/D/Games/Quake4/quake4': Invalid cross-device link


i dunno whats wrong i used the Quake4 installer from id software....UT2004 runs fine from its symbolic links....

---

### Post by crane on 2005-10-27
[QUOTE=DarkManX4lf]ok i put a dot in front of the command and it still wont launch, so i then tried to create the link like you said and this is what happened when i tried to create it.

root@ubuntu:~# sudo ln /media/D/Games/Quake4/quake4 /usr/bin/quake4
ln: creating hard link `/usr/bin/quake4' to `/media/D/Games/Quake4/quake4': Invalid cross-device link


i dunno whats wrong i used the Quake4 installer from id software....UT2004 runs fine from its symbolic links....[/QUOTE]


Is /media/d/ a different hard drive? I don't believe you can hard link across devices. You said UT2004 works with symbolic links yet you tried to create a hard link with your command. Try:
[color=blue]$sudo ln -s /media/D/Games/Quake4/quake4 /usr/bin/quake4[/color]
Also when you installed quake 4 did it install ascript in /usr/bin/ can you just type quake4 in you terminal and execute the game? If so just use quake4 as the command instead of /media/D/Games/Quake4/quake4 .

---

### Post by seethru on 2005-10-27
and as a note, is that the root terminal, or are you running ubuntu as root?

---

### Post by DarkManX4lf on 2005-10-27
yea /media/D is a different hard drive, and yea sorry i thought i was making symbolic links...im still a newb to linux...yea when i used the installer for quake4 it did create a link in /usr/local/bin but when i run it (or type quake4 in terminal) it says this

If you read this, then something failed during the setup
See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting


but i dont know whats the problem, i tried to reinstall the game to a different directory and i get the same error...i can manually go to the quake4 directory and double click on the quake4 file/executable and quake4 will run....but iwant to create a link for it in the gnome menu...i made a shortcut for doom3 in the gnome menu and the command for it was **/media/D/Games/Doom3/doom3** and that works fine but when i do it for quake4 it doesnt work....

---

### Post by DarkManX4lf on 2005-10-27
[QUOTE=seethru]and as a note, is that the root terminal, or are you running ubuntu as root?[/QUOTE]

yea im running ubuntu as root.

---

### Post by seethru on 2005-10-27
erm, not that it is relevant to the post, but it's never a good idea to run as root. Thats the whole point of having sudo, so you can run super user commands from your regular account, and it requires a password. Running as root is a security risk, much like the problem with Windows XP and always running as Administrator.

Also, if you're running as root, you really shouldn't need to use the sudo command ever, but like I said the whole idea of sudo is to make it so you can run root commands from your regular user, providing you know the password. This will make your pc more secure so that any malware that does exist can't make changes to the OS itself, just your home directory.

---

### Post by DarkManX4lf on 2005-10-27
[QUOTE=seethru]erm, not that it is relevant to the post, but it's never a good idea to run as root. Thats the whole point of having sudo, so you can run super user commands from your regular account, and it requires a password. Running as root is a security risk, much like the problem with Windows XP and always running as Administrator.

Also, if you're running as root, you really shouldn't need to use the sudo command ever, but like I said the whole idea of sudo is to make it so you can run root commands from your regular user, providing you know the password. This will make your pc more secure so that any malware that does exist can't make changes to the OS itself, just your home directory.[/QUOTE]

yea i know running as root is a security risk...but the problem is when running as user i do certain things with ease, such as like using nautilus or konqueror to create folders, i would have to do sudo mkdir...etc...i guess im lazy :) and there are some others things...but i guess i'll give user a try

---

### Post by DarkManX4lf on 2005-10-28
along with my initial question, here is another one, is there a way to "alt+tab" out of quake4 ?

---

### Post by DarkManX4lf on 2005-10-29
bump anyone?

---

### Post by GameGod on 2005-10-29
Download this and place it in your **/usr/share/pixmaps** folder:
[q4icon.xpm]("http://www.santoni.ca/albert/tweaks/q4icon.xpm")

Download this and place it in your **/usr/share/applications** folder:
[quake4.desktop]("http://www.santoni.ca/albert/tweaks/quake4.desktop")

Voila!
Quake 4 in your GNOME menu (under "games")... Enjoy :)

P.S. If you installed Quake 4 to a directory other than /usr/local/games/quake4, then edit the quake4.desktop file accordingly.

:)

---

### Post by DarkManX4lf on 2005-10-29
[QUOTE=GameGod]Download this and place it in your **/usr/share/pixmaps** folder:
[q4icon.xpm]("http://www.santoni.ca/albert/tweaks/q4icon.xpm")

Download this and place it in your **/usr/share/applications** folder:
[quake4.desktop]("http://www.santoni.ca/albert/tweaks/quake4.desktop")

Voila!
Quake 4 in your GNOME menu (under "games")... Enjoy :)

P.S. If you installed Quake 4 to a directory other than /usr/local/games/quake4, then edit the quake4.desktop file accordingly.

:)[/QUOTE]


thanks but i tried to edit the file accordingly (/media/D/Games/Quake4/quake4 in the command box) and it still wont launch :(

---

### Post by crane on 2005-10-29
Sorry man, I just got back intown from working.
When you type your command [color=blue]/media/D/Games/Quake4/quake4 /usr/bin/quake4[/color] what kind if error does it give? 
Did you try the [color=blue]ln -s[/color] from earlier post? no Luck?

You could look at the script that quake4 installed and try modifying it.
Mine was located in /usr/local/bin and looks like this:

```
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/quake4"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
./quake4.x86 $*
exit $? 
```

make sure the line [color=red]cd "/usr/local/games/quake4"[/color] points to where you installed it.

---

### Post by DarkManX4lf on 2005-10-29
[QUOTE=crane]Sorry man, I just got back intown from working.
When you type your command [color=blue]/media/D/Games/Quake4/quake4 /usr/bin/quake4[/color] what kind if error does it give? 
Did you try the [color=blue]ln -s[/color] from earlier post? no Luck?

You could look at the script that quake4 installed and try modifying it.
Mine was located in /usr/local/bin and looks like this:

```
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/quake4"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
./quake4.x86 $*
exit $? 
```

make sure the line [color=red]cd "/usr/local/games/quake4"[/color] points to where you installed it.[/QUOTE]


yea when i used the installer it made the links and i edited like you said and when i run it in terminal it gives me this

root@ubuntu:~# quake4
/usr/local/bin/quake4: line 4: cd: /media/D/Games/Quake4/quake4: Not a directory/usr/local/bin/quake4: line 6: ./quake4.x86: No such file or directory


but /media/D/Games/Quake4/quake4 is a directory ! (its also another hard drive)


heres another oddity if i do this

root@ubuntu:~# cd /media/D/Games/Quake4
root@ubuntu:/media/D/Games/Quake4#sh ./quake4

it will work fine

but if i type

root@ubuntu:~#sudo sh ./media/D/Games/Quake4/quake4

it will say there is no such directory

---

### Post by pmj on 2005-10-29
Still not solved?

I have Quake 4 in my menu. I really can't remember exactly what I did and why, a whole week ago is just way too long ago for me to remember.

Anyway, looking at my menu item it seems it's a link to a one line bash script that just starts the game with a few parameters. It works just fine for me.

---

### Post by DarkManX4lf on 2005-10-29
[QUOTE=pmj]Still not solved?

I have Quake 4 in my menu. I really can't remember exactly what I did and why, a whole week ago is just way too long ago for me to remember.

Anyway, looking at my menu item it seems it's a link to a one line bash script that just starts the game with a few parameters. It works just fine for me.[/QUOTE]

yea, i'm pretty sure that you used the quake4 installer from id software and if so then the installer puts shortcuts in the gnome menu but it didnt for me, it put a link in /usr/local/bin but it doesnt work...its really weird i can manually go to the directory and double click on the quake4.x86 file and the game will run, or i can do as i said above in terminal and it works but i cant make  a shortcut its really weird.

---

### Post by pmj on 2005-10-29
[QUOTE=DarkManX4lf]yea, i'm pretty sure that you used the quake4 installer from id software and if so then the installer puts shortcuts in the gnome menu but it didnt for me, it put a link in /usr/local/bin but it doesnt work...its really weird i can manually go to the directory and double click on the quake4.x86 file and the game will run, or i can do as i said above in terminal and it works but i cant make  a shortcut its really weird.[/QUOTE]
The installer didn't add shorcuts to the menu for me either, despte saying it would do so. I added it myself.

The installer should have put scripts that launches the game in your home folder, unless you changed the default binary path. I placed a shortcut to it in my menu just now and it worked.

---

### Post by DarkManX4lf on 2005-10-29
when installing i didnt change anything but the path where the quake4 files go, 
if that is what you are talking about?

---

### Post by DarkManX4lf on 2005-11-02
update, i reinstalled quake4 using the id installer and the links it made magically work now somehow....ah well thanks guys.

---

### Post by crane on 2005-11-04
[QUOTE=DarkManX4lf]update, i reinstalled quake4 using the id installer and the links it made magically work now somehow....ah well thanks guys.[/QUOTE]

Strange. Sometimes thats how things work though.
Glad it's working for you now start the game drop the console (ctrl)(alt)(~) and type:
connect q4.aswp.net.

---

