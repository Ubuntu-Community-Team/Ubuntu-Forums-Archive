---
title: "Need help finding a file"
date: 2006-05-02
forum: Desktop Environments
---

### Post by JohnN on 2006-05-02
Hello Everyone,

I need help finding a file from the internet.
The while that I need is "libmp3lame.so". 
This is for Audacity 1.2. 
Ubunutu 5.10 is my linux distro.


Have a great day

---

### Post by jazzmuzik on 2006-05-02
Go into Synaptic and install the "liblame0" package. That package contains libmp3lame.so.0

---

### Post by nanotube on 2006-05-02
if you open up synaptic package manager, and search for "lame", you should find a package with it, and install it. that will automatically pull the necessary files. (you might have to enable the multiverse and universe repositories first, if you have not done so already. you can find repository config in the synaptic menus.)

for the future, remember, first place to look for files and apps is in the repositories. :)

---

### Post by nanotube on 2006-05-02
gaaah, jazzmuzik, you beat me to it! :mrgreen:

---

### Post by aysiu on 2006-05-02
There are two parts to this.

First, [make sure you have the proper codecs installed for MP3 encoding](https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970).

Then, when you're looking for libmp3lame.so, look for *all files*--not just libmp3lame.so. Audacity will look in /usr/lib, but it won't find libmp3lame.so *exactly*. You should select libmp3lame.so.0 instead. It works just fine.

---

### Post by Sef on 2006-05-02
Try installing mplayer.

sudo apt-get update

sudo apt-get install mplayer

---

### Post by tapeshag on 2006-05-02
I am not sure about the debian package. But Found this article which may be useful. 

[http://www.linuxquestions.org/questions/showthread.php?t=168973](http://www.linuxquestions.org/questions/showthread.php?t=168973)

Hope this helps. Can u also tell what problem are u facing exactly?

---

### Post by aysiu on 2006-05-02
[QUOTE=Sef]Try installing mplayer.

sudo apt-get update

sudo apt-get install mplayer[/QUOTE] Are you sure you're posting in the correct thread...?

---

### Post by JohnN on 2006-05-02
Do you know what folder that file would be under after I did those steps?


I looked in /usr/lib and couldn't find the file.

---

### Post by christhemonkey on 2006-05-02
I had this problem yesterday, the file i used was in /usr/lib/
and was called liblamemp3.so.0.0
The liblamemp3.so.0 didnt work for me, just gave wierd thumping noises.

To get to it in the audacity search box, you must select at the bottom all extended libraries instead of where it says liblamemp3.so only.


Oh and also you must have the liblamemp3 package installed!

---

### Post by jazzmuzik on 2006-05-02
[QUOTE=JohnN]Do you know what folder that file would be under after I did those steps?

I looked in /usr/lib and couldn't find the file.[/QUOTE]

When you install library files, they are generally readable systemwide in the /usr/lib directory. So you shouldn't need to tell a program where it is. Your program should find it itself.

But to find a file, do this:

slocate libmp3lame.so

On my system I find 

/usr/lib/libmp3lame.so.0.0.0
/usr/lib/libmp3lame.so.0

This isn't exactly the one you are looking for, but I think one will work.

---

### Post by aysiu on 2006-05-02
[QUOTE=jazzmuzik]So you shouldn't need to tell a program where it is. You program should find it itself.[/QUOTE] Yes, Audacity *should* find the library without user intervention, but that's not what actually happens.

---

### Post by jazzmuzik on 2006-05-02
[QUOTE=aysiu]Yes, Audacity *should* find the library without user intervention, but that's not what actually happens.[/QUOTE]

Ah. Bummer. Hopefully they'll fix that.

---

