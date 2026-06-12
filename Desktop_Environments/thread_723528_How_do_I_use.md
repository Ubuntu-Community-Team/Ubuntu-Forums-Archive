---
title: "How do I use"
date: 2008-03-13
forum: Desktop Environments
---

### Post by Malikius on 2008-03-13
the tar and other archived software that I have downloaded. I don't know how to install these software programs. In windows I knew how to install *.zip and *.rar programs. But, these new files extensions have me confused. 

Please guide me to a unarchiving program and how to use it without have to use coding. 

Thanks

---

### Post by chadeldridge on 2008-03-14
If you are trying to open those through X there is already an application that handles pretty much all compressed file formats.  You don't need to install anything else.  Just double click the archive and file-roller will open it for you.

---

### Post by Malikius on 2008-03-14
Is X an unarchiving program? And is it already on the Ubuntu disc when I installed it?

---

### Post by chadeldridge on 2008-03-14
X ... as in Xwindows ... I should have been more clear and just said the graphical frontend to linux.  

file-roller is what you are looking for though.

---

### Post by aysiu on 2008-03-14
Why don't you tell us what you're trying to install? That might help.

---

### Post by Malikius on 2008-03-15
vb.tar.tar, & wine-0.9.57.tar.bz2  or any of the bz2 files. & tar.gz's 
those file types seem to confuse me.

---

### Post by PurposeOfReason on 2008-03-15
> **Malikius said:**
> vb.tar.tar, & wine-0.9.57.tar.bz2  or any of the bz2 files. those file types seem to confuse me.
Wine is in the repos so you could just do a 
```
sudo aptitude install wine
```

For a typical archive you have to extract (right click and choose extract) it then with a terminal, cd to where the extracted folder is (something like cd /home/yourname/Desktop/wine) and then type (again in a terminal) ./configure && make && sudo make install. That will do just what is says. Configure that package, make it, and install it.

---

### Post by Malikius on 2008-03-15
so the "&&" are the file name or the program name?

---

### Post by oldos2er on 2008-03-15
> **Malikius said:**
> so the "&&" are the file name or the program name?

 No. "./configure && make && sudo make install" means, run ./configure, and when that command has successfully completed, run make, then when THAT has successfully completed, run sudo make install.

---

### Post by PurposeOfReason on 2008-03-15
> **oldos2er said:**
> No. "./configure && make && sudo make install" means, run ./configure, and when that command has successfully completed, run make, then when THAT has successfully completed, run sudo make install.
I always thought && means run no matter what, even if failure.

---

### Post by unutbu on 2008-03-15
I wasn't sure about this either, but your comment motivated me to look this up:
[http://tldp.org/LDP/abs/html/list-cons.html#LISTCONSREF](http://tldp.org/LDP/abs/html/list-cons.html#LISTCONSREF)

---

### Post by Malikius on 2008-04-24
> **PurposeOfReason said:**
> Wine is in the repos so you could just do a 
```
sudo aptitude install wine
```

For a typical archive you have to extract (right click and choose extract) it then with a terminal, cd to where the extracted folder is (something like cd /home/yourname/Desktop/wine) and then type (again in a terminal) ./configure && make && sudo make install. That will do just what is says. Configure that package, make it, and install it.

Is there any listing of how to use the SUDO function? It seems to me that it is alot like MS-Dos commands. That way I don't have to keep asking for help on this matter. I can do it myself. Checked the forums for this type of question, help and hadn't found anything yet.

---

### Post by aysiu on 2008-04-24
> **Malikius said:**
> Is there any listing of how to use the SUDO function? It seems to me that it is alot like MS-Dos commands. That way I don't have to keep asking for help on this matter. I can do it myself. Checked the forums for this type of question, help and hadn't found anything yet.
*sudo* is what you preface commands with if you want the commands to be run with root (or system-wide administrator) privileges.

For example, if you want to move a file from your home folder to your desktop, that isn't a system-wide change, so you don't need *sudo*. It affects only your user account: ```
mv ~/Trip\ to\ Pain.mp3 ~/Desktop/
``` If, however, you want to move a file from your home folder to a system folder (/etc, for instance), you would need *sudo*, since /etc affects everybody: ```
sudo mv ~/sources.list /etc/apt/sources.list
```

---

### Post by Malikius on 2008-04-26
> **chadeldridge said:**
> If you are trying to open those through X there is already an application that handles pretty much all compressed file formats.  You don't need to install anything else.  Just double click the archive and file-roller will open it for you.

I see file-roller in the functions but I still don't understand the installation of several file extensions.

---

