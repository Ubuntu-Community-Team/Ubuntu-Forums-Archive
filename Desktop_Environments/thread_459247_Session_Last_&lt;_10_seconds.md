---
title: "Session Last &lt; 10 seconds"
date: 2007-05-30
forum: Desktop Environments
---

### Post by Her Ghost on 2007-05-30
Hi, 

I wonder if you can help.

I recently installed Realtek AC97 sound-drivers, but on reboot I can't log back into Gnome.

The error I get is:

```

Your session lasted less than 10 seconds...etc etc

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: Running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "leigh"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/gnome-session: error while loading shared libraries: libasound.so.2: cannot open shared file: No such file or directory

```

It is definately related to the sounddrivers because I no longer get the startup sounds.

I'm hoping this is simple line to comment out of somewhere, otherwise it's going to be a complete reinstall (which might not be a bad idea anyway, but I would prefer to keep my /home dir..)

(I posted this previously in Absolute Beginners, but have had no luck getting any help.  I hope you don't mind my posting here.  I won't bump this if it falls off the list.)

Thanks in advance

HG

(Ubuntu Feisty, 64bit, onboard AC'97 sound, dual booting with XP)

---

### Post by eggdeng on 2007-05-30
Have you tried to boot in recovery mode? If you can, go into your home directory, remove .asoundrc ```
sudo rm /home/your_username/.asoundrc
``` and reboot.

---

### Post by Her Ghost on 2007-05-30
Hi - thanks.

I can log in using the failsafe terminal, but nothing else (not even recovery mode).

I did what you suggested, but that didn't work :(

Any other things I could try?

Do you know where Ubuntu is referring to when it errors on

```

/usr/bin/gnome-session: error while loading shared libraries: libasound.so.2: cannot open shared file: No such file or directory

```

?

---

### Post by eggdeng on 2007-05-31
libasound belongs to alsa, your default sound driver. Installing the Realtek driver (I think it includes its own version of alsa) has left you with a screwed up driver. Your system locks up when it initiates the alsa driver on boot, which is why you can't get in.
Try
```
sudo apt-get remove alsa
``` from the terminal and reboot. You can reinstall the driver later.

---

### Post by Her Ghost on 2007-05-31
Thankyou

I removed the alsa drivers successfully, but still get the same error message as posted above.

Anything else I could try?

Seriously thank you for trying to help me here - I'm well in the deep end with this!

---

### Post by Spastic on 2007-05-31
i did exactly  the same thing. i am using an M2V motherboard and i tried to install the ac97 drivers on the disk. i should have left well enough aloone...

i uninstalled alsa, and reinstalled it didnt work with or without it -- i did aptitude search for the failed library file and it cant be found.

my theoryis this :
 the installer for the driver set that missing library but did not install it

---

### Post by Spastic on 2007-05-31
OKAY!  i got it to boot again, i discovered that i was right and the installer was unable to  access its own bz2 files because of the cdroms partition. coincidentally the /home  folder also doesn't allow bz2 files.
i copied the directory from the cdrom to a directory outside of the home folder and ran it, the installation ran into some errors.but it got the libraries installed and boots now... 
now i gotta figure out  how to get it working or back to alsa

(edit-  typos fixed. was on girlfriends PC with original post and her rubber keyboard > me.)

---

### Post by Spastic on 2007-05-31
Ok i think i may have found the problem, i found some other suggestions for troubleshooting a sound problem
when i ran the command:
 lspci -v | less
and searched for "Audio" it showed me the device but said "permission denied" so i ran it with sudo and discovered that it was 64bit. 

so im thinking the installer installs a 64bit driver that requires root to acess the device...

---

### Post by si_harp on 2007-06-13
Hi all,

I am having a very similar problem, see...

[http://ubuntuforums.org/showthread.php?t=470589](http://ubuntuforums.org/showthread.php?t=470589)

@Spastic:  It seems that you had some luck, I'm bit of a newbie with Ubuntu.  Could you describe exactly how you fixed it?

Many thanks.  Si

---

### Post by si_harp on 2007-06-15
FIXED!  :D

Found this thread [http://ubuntuforums.org/showthread.php?t=461894](http://ubuntuforums.org/showthread.php?t=461894) 

With thanks to engla who suggested trying...
[B]
*apt-get install --reinstall libasound2*[/B]

Fixed the problem, didn't even need to reboot to log on properley!  

Hope this helps someone. Si

---

### Post by abc123456 on 2007-06-16
When that error has happened to me, I mv .bashrc to bashrc.  Then reboot X ctl alt backspace.:popcorn:

---

