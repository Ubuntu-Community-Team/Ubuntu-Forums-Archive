---
title: "Does Thunar have gksudo like Nautilus"
date: 2006-07-06
forum: Desktop Environments
---

### Post by Georgie-o on 2006-07-06
I've switched to Xubuntu and would like to know if Thunar has a command to open as root similar to gksudo in nautilus?

Thanks

---

### Post by Georgie-o on 2006-07-06
oops, dumb question, just use gksudo thunar...

---

### Post by tenjin1 on 2007-02-04
thanks...
yes I didn't think of that either...
worked for me

now I'm trying to find a way to change the backgrounds like nautilus....

---

### Post by aysiu on 2007-02-04
```
gksudo thunar
``` works fine for me.

What do you mean by "change the backgrounds like Nautilus"?

---

### Post by tenjin1 on 2007-02-04
> **aysiu said:**
> 
What do you mean by "change the backgrounds like Nautilus"?

Hi aysiu-

What I meant by that was...
In Nautilus...in Edit -> Backgounds and Emblems
you can drag-and-drop a Pattern to the Nautilus window to change the background. I was just wondering if there was a way to do this in Thunar in the Custom Actions?

Thunar is great! I am interested in more Custom Action commands to use, still searching for more of them. I stumbled upon the plugins for Thunar..but really wasn't interested in them. If you could point me to anymore Custom Action commands for Thunar that would be great! :)  

Thanks in advance.

---

### Post by aysiu on 2007-02-04
I did a little bit of Googling around. I don't think you can have a background image in Thunar.

---

### Post by tenjin1 on 2007-02-04
Yes seems your right (hence xfce minimalistic)

now I'm trying to install the Thunar Archive Plugin from [http://foo-projects.org/~benny/projects/thunar-archive-plugin/index.html]("http://foo-projects.org/~benny/projects/thunar-archive-plugin/index.html")
....which gives you the right-click "extract here" for archives....also gives you the right-click "create archive" option. In the middle of installing this plugin now...trying to find my Thunar directory, I'm using Edgy. If you find or install before me please let me know and I'll do the same if I do find out..have to leave the computer for a while. 

Cya

---

### Post by tenjin1 on 2007-02-04
Ok...done.

I now have the right-click archive abilities. I had to compile from source since I am using Gnome; otherwise if I was using XFCE, I could have apt-get'd all of it from XFCE repos.

I used the install instructions from [http://http://foo-projects.org/~benny/projects/thunar-archive-plugin/index.html]("http://http://foo-projects.org/~benny/projects/thunar-archive-plugin/index.html")

```
download the tar ball from [http://www.gnomefiles.org/app.php?soft_id=1352]("http://www.gnomefiles.org/app.php?soft_id=1352")

```

cd to the download directory the tarball is in, then...
```
tar xvzf thunar-*
```

cd to thunar-archive-plugin-0.2.4 directory that the tarball creates

then, I had to 
```
sudo apt-get install libthunar-vfs-1-dev
```
because when installing it complained of depenancies, hence not using XFCE

then still in thunar-archive-plugin-0.2.4 directory
```
./configure --prefix=/usr/lib/thunarx-1
```

```
make
```

```
make install
```

now check in usr/lib/thunarx-1 and make sure two files are in that directory
thunar-archive-plugin.so and thunar-archive-plugin.la

(If not they are probably in the newly created /lib/thunarx-1 directory....which would be:
/usr/lib/thunarx-1/lib/thunarx-1)
if they are copy the 2 files to /usr/lib/thunarx-1

Restart thunar and you will have the "extract here" and "create archive" on right-click menu

---

### Post by tenjin1 on 2007-02-04
> **tenjin1 said:**
> Ok...done.

I now have the right-click archive abilities. I had to compile from source since I am using Gnome; otherwise if I was using XFCE, I could have apt-get'd all of it from XFCE repos.

I used the install instructions from [http://http://foo-projects.org/~benny/projects/thunar-archive-plugin/index.html]("http://http://foo-projects.org/~benny/projects/thunar-archive-plugin/index.html")

```
download the tar ball from [http://www.gnomefiles.org/app.php?soft_id=1352]("http://www.gnomefiles.org/app.php?soft_id=1352")

```

cd to the download directory the tarball is in, then...
```
tar xvzf thunar-*
```

cd to thunar-archive-plugin-0.2.4 directory that the tarball creates

then, I had to 
```
sudo apt-get install libthunar-vfs-1-dev
```
because when installing it complained of depenancies, hence not using XFCE

then still in thunar-archive-plugin-0.2.4 directory
```
./configure --prefix=/usr/lib/thunarx-1
```

```
make
```

```
make install
```

now check in usr/lib/thunarx-1 and make sure two files are in that directory
thunar-archive-plugin.so and thunar-archive-plugin.la

(If not they are probably in the newly created /lib/thunarx-1 directory....which would be:
/usr/lib/thunarx-1/lib/thunarx-1)
if they are copy the 2 files to /usr/lib/thunarx-1

Restart thunar and you will have the "extract here" and "create archive" on right-click menu

Hi aysiu

Should this be in a new thread??? Could you test for me before making new thread???

---

