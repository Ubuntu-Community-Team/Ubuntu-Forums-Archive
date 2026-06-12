---
title: "Noob is banging head into wall- can't get tar to work on game"
date: 2007-05-24
forum: Gaming &amp; Leisure
---

### Post by WHICKS on 2007-05-24
Please forgive my uselessness.

I am trying to download the game paintball 2 for linux.

I went to the sourceforge.net site and it said to dowload this file

paintball2_build016_linux_full.tar.gz

it was transfered from:  paintball2_build016_linux_full.tar.gz
and downloaded to :     /home/warren/.opera/cache4/temporary_download/paintball2_build016_linux_full.tar.gz

I went to the command line and typed  

tar xfvz paintball2_build016_linux_full.tar.gz

I get the follwing errors:

warren@usr8054:~$  tar xfvz paintball2_build016_linux_full.tar.gz
tar: paintball2_build016_linux_full.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


I am obviously not doing something right.  Can someone walk me through this.  Thank you in advance.

---

### Post by cyrusrayne on 2007-05-24
I would try saving it to your home folder and running it through File Roller to see if that will work.  If there's anything you need to compile or run thereafter you should be set.

---

### Post by WHICKS on 2007-05-25
warren@usr8054:~$ cp /home/warren/desktop/cube_2005_08_29_unix.tar.gz
cp: missing destination file operand after `/home/warren/desktop/cube_2005_08_29_unix.tar.gz'
Try `cp --help' for more information.
warren@usr8054:~$ cp/home/warren/cube_2005_08_29_unix.tar.gz
bash: cp/home/warren/cube_2005_08_29_unix.tar.gz: No such file or directory
warren@usr8054:~$ 


How do I copy it to my home directory ( I assume it must be in the home directory prior to me using the  tar xfvz  command?

Thanks, signed

thouroughly confused, but patient and willing to learn.

---

### Post by nythacker on 2007-05-25
> **WHICKS said:**
> Please forgive my uselessness.

I am trying to download the game paintball 2 for linux.

I went to the sourceforge.net site and it said to dowload this file

paintball2_build016_linux_full.tar.gz

it was transfered from:  paintball2_build016_linux_full.tar.gz
and downloaded to :     /home/warren/.opera/cache4/temporary_download/paintball2_build016_linux_full.tar.gz

I went to the command line and typed  

tar xfvz paintball2_build016_linux_full.tar.gz

I get the follwing errors:

warren@usr8054:~$  tar xfvz paintball2_build016_linux_full.tar.gz
tar: paintball2_build016_linux_full.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


I am obviously not doing something right.  Can someone walk me through this.  Thank you in advance.

Try this...

```
cp /home/warren/.opera/cache4/temporary_download/paintball2_build016_linux_full.tar.gz /home/warren/
cd
tar zxvf ./paintball2_build016_linux_full.tar.gz
```

Hope this helps...

---

### Post by Sef on 2007-05-25
Check out [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by WHICKS on 2007-05-26
this worked perfectly .  Thank you.   The graphical icon within the folder will run the program.  Is there a way that I can make this show up in the applications menu. (under games)  Currently, I have to go into the home directory to find it.

---

### Post by nythacker on 2007-05-28
> **WHICKS said:**
> this worked perfectly .  Thank you.   The graphical icon within the folder will run the program.  Is there a way that I can make this show up in the applications menu. (under games)  Currently, I have to go into the home directory to find it.

_*Right-click*_ on the ***[COLOR="Red"]Applications[/COLOR]*** menu and select ***[COLOR="Red"]Edit Menus[/COLOR]***.

Select ***[COLOR="Red"]Games[/COLOR]*** from the ***[COLOR="Red"]Menus[/COLOR]*** _column_ and click the ***[COLOR="Red"]New Item[/COLOR]*** _button_ on the right-hand side of the _*Menu Layout*_ window.

Hope this helps...

---

### Post by tetris4 on 2008-06-16
Hello..
I extracted the same file on my desktop..
I then try to start the game by clicking on paintball2 executable in it, however nothing happens..

Am i doing smg wrong?

---

