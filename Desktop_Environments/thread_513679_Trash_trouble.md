---
title: "Trash trouble"
date: 2007-07-30
forum: Desktop Environments
---

### Post by mac71 on 2007-07-30
Hi Everyone,

Can anyone help me with this annoying little thing that's cropped up over the last few days?

When I click on an empty trash can, I get the option to empty it although I know it's already empty. If I try to delete (whether there's trash or not) I get an Error-KDE Panel box pop up saying this:

The file or 
folder /home/myusername/.local/share/Trash/files/amsn.desktop
does not exist.

I should also add that any trash that does exist, does still get deleted.

I realise the amsn.desktop bit is the problem, but how do I get rid of it?

---

### Post by tbroderick on 2007-07-30
Open a terminal and paste;
```

sudo rm ~/.local/share/Trash/files/amsn.desktop

```

---

### Post by mac71 on 2007-07-31
Hi,
Thanks, I tried that and got this:

rm: cannot remove `/home/myusername/.local/share/Trash/files/amsn.desktop': No such file or directory

Any other ideas?

---

### Post by tbroderick on 2007-07-31
Use ls to list the contents of your trash
```

ls ~/.local/share/Trash/files/

```

---

### Post by mac71 on 2007-07-31
Hi 

Tried that and got this:
> username@Ubuntu:~$ ls ~/.local/share/Trash/files/
username@Ubuntu:~$


If I create an aMSN desktop Icon and move it to trash, I then get this:
> username@Ubuntu:~$ ls ~/.local/share/Trash/files/
amsn_1.desktop


It displays it as number 1, although an original doesn't exist. If I open the trash in a window, it is displayed as amsn.desktop. :confused:

If I then empty trash from the desktop I do not get the error warning. All the time aMSN desktop icon exists in my trash, I don't get the warning, as soon as its been deleted the warning comes back. 
 Basically, if I create an aMSN desktop icon and move it to trash every time I need to delete anything, I don't get the warning. If I don't create one, I get the warning.

I'm scratching my head. Any other thoughts?

---

### Post by Jessehk on 2007-08-07
I'm getting the same type of error but on Arch Linux. I assume it's a KDE error and not ubuntu-specific.

Any thoughts anyone?

---

### Post by mac71 on 2007-08-07
I think you're right, as it didn't affect trash in gnome. It drove me mad, I ended up backing everything up and doing a fresh install. So it's gone now. I'd love to know how to get rid of it though, just in case it returns.

---

### Post by Merritt.kr on 2007-08-08
I get the same error, except that occasionally it shows my trash as being perpetually full, even when it's not, and it is giving me this error:

The file or folder /home/kristen/.local/share/Trash/files/Disk 2 does not exist.

I've had this problem for a few months now, sometimes it happens and sometimes it doesn't, and there seems to be no pattern to it. *shrugs*

---

### Post by jbengtsson on 2007-09-29
I get the same error, but I'm not running KDE, only Gnome - KDE has  never even  been installed on this machine.  I just did a totally clean install of 7.04 yesterday, and all the stuff in trash was put there 
when I did all the updates (119 or so) from the install (from the ShipIt disk).  I tried to empty trash as root from the console, and where the original error message was 'no permissions for parent directory for /var/run/console/userid:7', the file it complains about is /var/run/sudo.  Strange, no?  I run a sudo command to empty trash, and now sudo is in the trash.  Anyone?

---

### Post by Sir Hugh on 2007-09-30
I had a similar problem. According to this site KDE uses a "representative trash system" as opposed to a "live one". [http://www.raiden.net/?cat=2&aid=284]("http://www.raiden.net/?cat=2&aid=284")

Basicly when you delete something it puts it in a trash folder (/home/myusername/.local/share/Trash/files) and, in order to prevent overwriting any previously trashed files of the same name, stores some info on the file in /home/myusername/.local/share/Trash/info.

For whatever reason the file has gone and the info hasn't (probably something stupid I did, that's usually why things go wrong for me!).

I've deleted the related files in that info directory and it seems to have fixed the problem. So have a look in /home/myusername/.local/share/Trash/info with konqueror or whatever and see if there is a file there (they're text based so you can open them up if you're curious) related to your problem and delete it!

---

