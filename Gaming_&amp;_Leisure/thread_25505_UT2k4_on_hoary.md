---
title: "UT2k4 on hoary"
date: 2005-04-10
forum: Gaming &amp; Leisure
---

### Post by furunculus on 2005-04-10
i'm sure you are getting bored of UT2k4 help requests, but humour me:

i double click on the >linux-installer.sh< and it asks me if i want to run it in a terminal, i say "yes" and then nothing happens................?

while i realise this may be blindingly obvious, i'm lost and would appreciate a walk thru.  ](*,) 

many thanks

furunculus

---

### Post by soul_rebel on 2005-04-10
open a terminal and do
sh /media/cdrom(or whathever)/linux-installer.sh

---

### Post by Silwenae on 2005-04-10
Copy linux-installer.sh to your /home directory (or /home/user/ut2004) and then click it, it will start the install.

---

### Post by furunculus on 2005-04-10
how do i open a terminal?

i knew where the terminal button was on suse, but i ain't spotted it so far on ubuntu.

cheers

---

### Post by furunculus on 2005-04-10
thanks, i'll give that whirl.

---

### Post by furunculus on 2005-04-10
[QUOTE=Silwenae]Copy linux-installer.sh to your /home directory (or /home/user/ut2004) and then click it, it will start the install.[/QUOTE]

i have no write permissions to that directory
?

---

### Post by IceAxe18 on 2005-04-10
Click on Applications, highlight system tools, click on Terminal.

This should work for you:

```
sudo sh /cdrom/linux-installer.sh
```

---

### Post by furunculus on 2005-04-10
[QUOTE=IceAxe18]Click on Applications, highlight system tools, click on Terminal.

This should work for you:

```
sudo sh /cdrom/linux-installer.sh
```[/QUOTE]

cheers, but:

> hosiah@ubuntu:~$ sudo sh /cdrom/linux-installer.sh
Password:
sh: /cdrom/linux-installer.sh: No such file or directory
hosiah@ubuntu:~$


:D

---

### Post by furunculus on 2005-04-10
[QUOTE=furunculus]i have no write permissions to that directory
?[/QUOTE]
i've had most success with this one so far, just need to get around the write permissions problem.............?

---

### Post by IceAxe18 on 2005-04-10
[QUOTE=furunculus]i have no write permissions to that directory
?[/QUOTE]

You need to use the Sudo comand to be able to have write permission.

```
 sudo cp -v -r linux-installer.sh
```

---

### Post by furunculus on 2005-04-10
[QUOTE=IceAxe18]You need to use the Sudo comand to be able to have write permission.

```
 sudo cp -v -r linux-installer.sh
```[/QUOTE]
oddly enough, i have managed to begin the install by click-n-dragging the linux-installer.sh file into the terminal, and then pressing "enter".

i'm sure it makes sense to someone...........?

---

### Post by IceAxe18 on 2005-04-10
Weird, but Cool  :-D

---

### Post by furunculus on 2005-04-10
installation is complete, but:

> open /dev/[sound/]dsp: Device or resource busy
Couldn't set video mode: Couldn't find matching GLX visual&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
              &#9474; Installation complete!                         &#9474;
              &#9474; Would you like to start now?                   &#9474;
History:      &#9474;                                                &#9474;
              &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;
Exiting due to error        < Yes >       < No  >              &#9474;
root@ubuntu:/home/hosiah #

---

### Post by furunculus on 2005-04-10
it will load the splash screen, then nothing.

i only did the base install not the openAL stuff etc, is that why the installation is borked?

i want to try again, this time with the second install option and see if that works better.
how do i remove the curretn borked installation?

cheers

---

### Post by furunculus on 2005-04-10
dammit! i'm back to the "lack to write permissions" problem, and i don't know what i did differently last time with my click-n-drag routine to bypass the problem. :(

i'm running in a root terminal, how can i NOT have write permissions?  :-s  :-?

---

### Post by furunculus on 2005-04-10
come on people, we were doing so well before, a veritable dreamteam of n00b amateurism, where have you all gone................?

---

### Post by furunculus on 2005-04-10
i accidently ran the dkpg command in an effort to get skype to install, and voila, UT2k4 started installing again, no more probs with write permissions........? once again; i'm sure this makes sense to someone, but its a mystery to me!

i mentioned before i had two instal options the first time around; base install, and Open AL install. i chose the former and the game wouldn't load properly. well this time i only had the option of the Open AL presumably because it knows the first lot is already installed.

now hoping the dang thing will work.

---

### Post by furunculus on 2005-04-10
nope, same problem:
> open /dev/[sound/]dsp: Device or resource busy
Couldn't set video mode: Couldn't find matching GLX visual&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
                             &#9474;
History:      &#9474;                                                &#9474;
              &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;
Exiting due to error                   &#9474;
root@ubuntu:/home/hosiah # &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; nd file

anyone going to let me in on the big secret?

---

### Post by jdodson on 2005-04-10
did you enable 3D video?  [http://ubuntuforums.org/showthread.php?t=25723](http://ubuntuforums.org/showthread.php?t=25723)

check that guide.  let me know your glxgears FPS count.

---

### Post by furunculus on 2005-04-11
it looks like i hadn't installed the nvidia drivers.

GLX gears was 290fps.

---

### Post by furunculus on 2005-04-11
this is where i'm up to:

> root@ubuntu:/home/hosiah # sh NFORCE-Linux-x86-1.0-0301-pkg1.run
sh: NFORCE-Linux-x86-1.0-0301-pkg1.run: No such file or directory
root@ubuntu:/home/hosiah # apt-get install nvidia-glx nvidia-settings
Reading package lists... Done
Building dependency tree... Done
nvidia-glx is already the newest version.
nvidia-settings is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/home/hosiah # nvidia-glx-config enable

A backup of xorg.conf has been stored as:
/var/backups/xorg.conf.2005-04-11-18:17:23.
If the new configuration will not work you will be able to
revert the changes simply using this command:
cp /var/backups/xorg/xorg.conf.2005-04-11-18:17:23 /etc/X11/xorg.conf


Warning: your X configuration has been succesfully changed.
In order to take full advantage of the changes, X needs to
be restarted.

root@ubuntu:/home/hosiah # sh NVIDIA-Linux-x86-1.0-7174-pkg1.run
sh: NVIDIA-Linux-x86-1.0-7174-pkg1.run: No such file or directory
root@ubuntu:/home/hosiah # cd
root@ubuntu:~ # sh NVIDIA-Linux-x86-1.0-7174-pkg1.run
sh: NVIDIA-Linux-x86-1.0-7174-pkg1.run: No such file or directory
root@ubuntu:~ #


what next?

---

### Post by Tseug on 2005-04-11
Correct me if im wrong, but you shouldn't have anything to run if you used apt-get. Once you sudo apt-get install the drivers, they are installed, and theres nothing left to run. But im a semi-noob too, so corrections are welcome :D

Edit!

Or maybe im just not understanding your question :D Thats a possibility also. I just finished patching and adding the bonus pack to UT a few days ago, so if you need help with that, just lemme know :D

---

### Post by furunculus on 2005-04-11
you are correct, i can load the game now, i was just confused by the lack of a nvidia option in the system tools.

i haven't got sound tho........?

cheers all.

---

### Post by jdodson on 2005-04-11
[QUOTE=furunculus]this is where i'm up to:



what next?[/QUOTE]

installing the drivers via apt-get is all you need to do.  you dont need to install anything else.  i will make that more clear from the piece i created.  

now follow the steps after you get the driver installed.

---

### Post by Tseug on 2005-04-11
AHA! i can fix the sound problem! In the terminal, type : sudo killall esd . Then hit enter. Then youll have sound in UT. But, when youre done, you wont have any sound from any other programs, so that requires you to run esd again, either alt+f2 and type in esd, or run it from the terminal. Either one is fine :D

---

