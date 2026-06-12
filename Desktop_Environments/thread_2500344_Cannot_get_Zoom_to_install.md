---
title: "Cannot get Zoom to install"
date: 2024-08-30
forum: Desktop Environments
---

### Post by Autodave on 2024-08-30
Ubuntu 24.04.  Cannot get Zoom to install.  I manually installed all the dependencies that it nsaid were needed, but when I click on the INSTALL button on gdebi, nothing happens.  What am I doing wrong?

---

### Post by deadflowr on 2024-08-30
Does any oddball error show when trying to install it through the command line?

---

### Post by Autodave on 2024-08-30
Haven't tried it that way...probably because I have no idea how to.  Would you be kind enough to give me the format for that?

---

### Post by deadflowr on 2024-08-30
Try
```
sudo apt install /full/path/to/deb
```
replace /path/to/deb with the full path to the .deb file.

If it's in the Downloads folder then something like
```
sudo apt install /home/username-here/Downloads/zoom-XXXXX.deb
```

replacing username-here with your username and XXXXX with whatever the deb file says.

Easy trick is to use TAB completion
Once you type the z or whatever the first letter of the deb file is hit TAB and it'll autofill the rest.


TAB completion for the win.

---

### Post by Shibblet on 2024-08-30
I know this is a cop-out, but have you tried the browser version?

---

### Post by Autodave on 2024-08-30
Tried the browser version...same results.....not working.

---

### Post by Shibblet on 2024-08-30
Is this the Snap?

---

### Post by Autodave on 2024-08-30
E: Unsupported file /home/pat/Downloads/zoom_amd64 given on commandline
pat@dave-MS-7641:~$

---

### Post by deadflowr on 2024-08-30
Incomplete filename?
No .deb at the end?

Should be zoom_amd64.deb

---

### Post by Autodave on 2024-08-30
> **deadflowr said:**
> Incomplete filename?
No .deb at the end?

Should be zoom_amd64.deb

It was there...the .deb part.  Having said that, I am assuming that this was my fault.  This particular PC is in the cellar.  The reason for that it because if my wife and I are both on the same Zoom meeting, we can't be close to each other because of feedback and echoing.  So, there are 2 machines in the basement (as well as 2 machines in this computer room).  I was trying to install Zoom on my machine downstairs where she is a second user on it with full privileges.  This worked in 22.04, but will not work in 24.04.  Why?  Dunno.  Anyhow, it is working now after I installed it under my user name......it also installed under her user name.

Thanks all for the help!

Now on to my next nightmare.....neighbors laptop running Win11 won't update.  Why?  Because some idiot at HP figured that a 64G nvme was big enough.  It wasn't.  NOTHING is installed except for one very small EA game, but Windows recommends a minimum of 64G of space to install Win11.  So, there is not enough room to d-l an update!  Yehaw.

---

