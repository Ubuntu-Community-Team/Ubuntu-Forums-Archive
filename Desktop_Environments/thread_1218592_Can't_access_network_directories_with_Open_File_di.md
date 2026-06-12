---
title: "Can't access network directories with Open File dialog"
date: 2009-07-20
forum: Desktop Environments
---

### Post by Luke has no name on 2009-07-20
Correct me if I'm missing something. I want to load music files from my server through Exaile's "Open File" command, but when I'm in a file prompt-browser, none of my network shares are up (Samba or SFTP). Why is this?

---

### Post by baryonyx on 2009-07-30
I noticed the same thing since I prefer exaile to rythmbox.  

I'm guessing it's a result of how the developers implement the open dialog.  The Ubuntu 'native' apps (rythmbox, totem) all display network bookmarks in the open dialog  but banshee, exaile, vlc do not.  

I've just resorted to using smbmount and sshfs instead of the gui to mount remote filesystems.

---

### Post by rmflagg on 2009-08-22
*Bump*

   Does anyone have any idea as to why this happens?  I would love to know the reason and if there is a fix available.

Thanks,
RMF

---

### Post by mbn18 on 2009-08-24
I am also very interested in finding a solution.

SFTP folders in my bookmark are not seen when I click 'open file' through some application ( like Deffuse ).

Other work as expected ( like Text editor ).

---

### Post by magicfab on 2010-01-08
You should find those in the .gvfs folder in your home folder. I have no idea why :) I am looking for a master bug for this.

---

### Post by larseko on 2010-05-03
IMHO this is a serious shortcoming. Users except the same bookmarks, places and mount points in the file open chooser as in the default file manager (nautilus). I see that they haven't fixed this in lynx either. I can't really see why, because it seems so obvious that this should be how it worked :)

---

### Post by QueequegAZ on 2010-12-15
Agreed.  It's little things like this that keep me away from gnome.  In KDE all the network locations show up in the places panel, or are accessed by typing smb:/[location] in the location field.  The gnome open file dialog doesn't seem to let you open network locations at all.  I would love to see this fixed, as some programs use a gtk file dialog (IE Chrome) and leave me no way to access networked files. 

And no, I don't want to mount my network locations to a directory.  It's unnecessary in KDE and shouldn't be necessary in gnome either.

---

### Post by Morbius1 on 2010-12-15
> **QueequegAZ said:**
> In KDE all the network locations show up in the places panel
Gnome: Places > Network
> or are accessed by typing smb:/[location] in the location fieldSame in Nautilus.
> The gnome open file dialog doesn't seem to let you open network locations at all. I'll admit that it does seem like some kind of prcticle joke by the developers but as stated above it's in a "hidden directory: When you're in the open file dialog, right click and select "show hidden files". Then go to .gvfs and your mounted remote share will be there.
> I don't want to mount my network locations to a directory.  It's unnecessary in KDE and shouldn't be necessary in gnome either.One way or another the remote share needs to be mounted. In Gnome when you go to Places > Network it will mount it to the .gvfs directory in your home directory.

---

### Post by Boondoklife on 2010-12-15
Now I could be wrong on this but I recall reading some where that this has to do with the application being nautilus aware.

The easy fix is to just run:
```

cd
ln -s .gvfs Network

```
It will create a folder called Network that is a link to where the shares are mounted. From there you should be able to do what you need to do. Now if only this folder was made by default or provided by gvfs instead of that hidden directory, I mean you already know you mounted it and it is not like it makes things easier to fudge by changing it.

---

### Post by Morbius1 on 2010-12-15
> Now if only this folder was made by default or provided by gvfs instead of that hidden directoryAmen. ;)

---

