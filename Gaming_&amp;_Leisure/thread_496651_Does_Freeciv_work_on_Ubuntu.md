---
title: "Does Freeciv work on Ubuntu?"
date: 2007-07-09
forum: Gaming &amp; Leisure
---

### Post by Cornerville on 2007-07-09
If so, how did you do it?

---

### Post by cogadh on 2007-07-09
Yes it works. You just need to install it from the repositories and then run it.

---

### Post by hikaricore on 2007-07-09
It's in the [universe repos]("https://help.ubuntu.com/community/Repositories/Ubuntu"):

```
sudo apt-get install freeciv
```

---

### Post by Cornerville on 2007-07-09
I have installed it from the repositories and it does not work.  I have installed it both ways you have suggested and also from the .deb installations on the web.  The result is always the same.  It freezes when you try to start a game.  Have tried to compile it from a tar.gz but wind up in "compile hell" which I am not good enough to negotiate yet.  Thanks anyway though guys, I do appreciate it.

---

### Post by cogadh on 2007-07-09
Which one did you install, the regular gtk freeciv client or the xaw3d client? I had problems with the xaw3d client, but the gtk client installs and runs perfectly.

---

### Post by Cornerville on 2007-07-09
I installed the regular gtk client.  I have installed several different versions and all of them have the same result.  One of the problems have had with compiliing is getting GTK+ to install.  I have installed glib, and pango which it requires, but it has problems with the glib version I installed.  It said I should remove the one I have.  I do not know how to do that.  Do you just have to look all over the system for it or is there an easier way?

Anyway, none of the debian specific versions that I have installed have worked, and, yes, I did remove the old version before I installed a new one.

---

### Post by cogadh on 2007-07-09
If you install through Synaptic or by using the "sudo apt-get install... " option that hikaricore posted, it should install all the appropriate dependencies as well as the game. 

Did you happen to install your glib from a source other than the Ubuntu repositories? 

Also, you probably shouldn't use Debian-specific versions. Even though Ubuntu is based on Debian, it is not the same as Debian and it is better to get Ubuntu-specific packages.

---

### Post by obidose on 2007-07-09
As a rule of thumb, If a game is free, It will probably run on Ubuntu.

---

### Post by Cornerville on 2007-07-09
[I][I]If you install through Synaptic or by using the "sudo apt-get install... " option that hikaricore posted, it should install all the appropriate dependencies as well as the game.

Did you happen to install your glib from a source other than the Ubuntu repositories?


[/I][/I]
I reinstalled it with apt-get with the same result.  I did not get glib from the Ubuntu repositories.  I unpacked it from a tar-ball.  I checked the install-remove utility and did not find one there.  When you enter glib into the add/remove application  search it returns with gfpt, whih I installed with no result either

---

### Post by cogadh on 2007-07-09
I think that might be your problem. Always install libraries from the repositories, otherwise you could have problems. The Add/Remove tool isn't the best tool to use (at least I've found it to be like that). If you are going to use a graphical tool, I'd use Synaptic (it's found in System > Administration > Synaptic Package Manager). 

I would suggest you remove the libraries you have installed from sources other than the Ubuntu repositories and try running the freeciv install from the repository again. It should detect which libraries you neeed and install the correct one from the repository automatically.

However, if you want to install the glibc libraries on their own, I believe they are part of the "build-essential" package and the libc6 packages.

---

### Post by Cornerville on 2007-07-09
cogadh wrote:

I think that might be your problem. Always install libraries from the repositories, otherwise you could have problems. The Add/Remove tool isn't the best tool to use (at least I've found it to be like that). If you are going to use a graphical tool, I'd use Synaptic (it's found in System > Administration > Synaptic Package Manager).

I would suggest you remove the libraries you have installed from sources other than the Ubuntu repositories and try running the freeciv install from the repository again. It should detect which libraries you neeed and install the correct one from the repository automatically.

However, if you want to install the glibc libraries on their own, I believe they are part of the "build-essential" package and the libc6 packages.



I used the Synaptic to remove & replace freeciv, the result was the same.  When you try to start a game, it grinds a long time, the gives the error message "Sorry, you will have to start a game manually"  Thanks for turning me on to that tool though, I can see how it will be very helpful in the future.  

I have already installed build-essential and went ahead and installed the glibc  packages.  Really did not help, but I have not tried to configure the tarball again.

It would really help me though, if someone would tell me how to remove a package that I did not  install from Ubuntu repositories apparently the graphical tools don't do this and I don't think apt-get will either.

I have trled Suse, Fedora, and Redhat in the past, and overall, I think Ubuntu has them beat by a mile.  I really can live without freeciv, but when I run into a wall, I like to try and climb it anyway, that is how I have learned what little I do know about Linux.  The more I learn , the more I like it, 

Thanks for the help

---

