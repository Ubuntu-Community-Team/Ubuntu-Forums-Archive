---
title: "[SOLVED] Nimbus 0.1.0 - now what do I do with it?"
date: 2008-10-11
forum: Desktop Environments
---

### Post by fballem on 2008-10-11
I have found a link on the Sun site to Nimbus 0.1.0 at [http://dlc.sun.com/osol/jds/downloads/extras/nimbus/](http://dlc.sun.com/osol/jds/downloads/extras/nimbus/)

I have downloaded it, but I'm a relative newbie. Could someone with more experience than me have a look and tell me what to do with it. There is a readme file, on which I followed the instructions, but I'm not sure what I ended up with, or what to do with it.

Many thanks,

---

### Post by Partyboi2 on 2008-10-13
I have not tried to install it but all you should need to do is .... Open a terminal and change in the directory where the downloaded nimbus-0.1.0.tar.bz2 file is. So if its on your Desktop
```
cd ~/Desktop
``` Then install some packages you will need to compile it.
```
sudo apt-get install build-essential gnome-devel icon-naming-utils
```After they have installed, extract the nimbus file
```
tar xvjf nimbus-0.1.0.tar.bz2
```change into the newly created directory
```
cd nimbus-0.1.0
``` then 
```
./configure
``` if that is successful and returns no errors,  then
```
make
``` if that returns with no errors install it with
```
sudo make install
```

---

### Post by fballem on 2008-10-13
So now that I know what to do with this, what is produced in the make and make install commands?

The reason that I'd rather not have to go through this pain again - I'd rather just install the end result if that's doable.

Thanks,

---

### Post by WTF_Shelley on 2008-10-13
install checkinstall

sudo apt-get install checkinstall

then after 'sudo make install' nimbus, type 'sudo make checkinstall'

this will create a .deb file for you which you can reinstall later with dpkg -i nimbus.deb

---

### Post by fballem on 2008-10-19
Argh! This isn't working for me at all.

If someone tells me how, then I'll gladly repeat the process so that you can look at the output and tell me what I'm doing wrong.

The instructions that I'm trying to follow are:

```
cd ~/Desktop
sudo apt-get install build-essential gnome-devel icon-naming-utils
checkinstall
tar xvjf nimbus-.1.0.tar.bz2
cd nimbus-0.1.0	
./configure
make
sudo make install
```

As far as I can tell, two themes are created in the /usr/local/share/themes folder - dark-nimbus and nimbus. The first problem is that neither shows up in the list of themes when I try to change the Desktop background. I can solve this by copying the themes to /usr/share/themes folder.

The second problem is that a gtk-engine is required - for nimbus. I notice in the source files that the code is there, but I have no idea what it does, where the engine is placed, and how to make recognizable by ubuntu. By the way, I'm running Intrepid beta with all patches applied as of Oct-19-2008.

The source file is about 9 meg, so I don't want to upload it, but if someone wants to play with it, then please let me know and I'll send it.

Otherwise, if someone can tell me how to redirect the output from ./configure, make, and make install to a text file, then I will re-run the instructions and attach the output to another message.

Please accept my thanks in advance, particularly for your patience!

---

### Post by fballem on 2008-10-19
In addition to being able to install the theme itself, I'd also like to find a GDM theme, which I think is what is required to have a custom login screen.

If there is no existing theme, then if someone could point me to instructions for making one and then using it, then I'd like to try this as a learning exercise.

And no, I don't want much:lolflag:

Thanks,

---

### Post by Partyboi2 on 2008-10-20
> In addition to being able to install the theme itself, I'd also like to find a GDM theme, which I think is what is required to have a custom login screen. Have a look at [http://www.gnome-look.org/](http://www.gnome-look.org/) 

> If there is no existing theme, then if someone could point me to instructions for making one and then using it, then I'd like to try this as a learning exercise.
Have a look at [[COLOR=Blue]this [/COLOR]]("http://linuxowns.wordpress.com/2008/01/31/make-a-custom-login-screen/")or [[COLOR=Blue]this[/COLOR]]("http://live.gnome.org/GnomeArt/Tutorials/GdmThemes") 

> If someone tells me how, then I'll gladly repeat the process so that you can look at the output and tell me what I'm doing wrong.

The instructions that I'm trying to follow are:
This is what I did to get it to work.
```
cd ~/Desktop
sudo apt-get install build-essential gnome-devel icon-naming-utils
tar xvjf nimbus-0.1.0.tar.bz2
cd nimbus-0.1.0	
./configure --prefix=/usr
make
sudo make install
``` Then have a look in System>Pref>Appearance>theme. You should now be able to select the theme.
If you are wanting a make a deb so you can install it again later on make sure you are still in the nimbus-0.1.0 directory and type
```
sudo checkinstall --fstrans=no --install=no
``` there should know be a deb packaged called nimbus_0.1.0-1_i386.deb

---

### Post by loomsen on 2008-10-20
> **WTF_Shelley said:**
> install checkinstall

sudo apt-get install checkinstall

then after 'sudo make install' nimbus, type 'sudo make checkinstall'

this will create a .deb file for you which you can reinstall later with dpkg -i nimbus.deb

Erm... As the prepended "CHECK" suggests... You should run checkinstall right after make. This will install creating a .deb file if everything was fine, otherwise return with an error message without having sudo messed up everything.

Maybe somewhat deprecated, but I use to try shoes on prior to buying them.


*edit*

Btw, sudoing is rarely superior to doing sth as a normal user... So, you may as well install things to a local dir, 
$HOME/bin for instance. No need for sudo, unless you want to change your system.

---

### Post by fballem on 2008-10-20
Thanks - the instructions worked perfectly, including the creation of the .deb.

In order to put the ubuntu logo instead of the open solaris logo, after I untarred the source file, I copied start-here.png from usr/share/icons/gnome/24x24/places into ~/Desktop/nimbus-0.1.1/icons/24x24/places and from usr/share/icons/gnome/32x32/places into ~/Desktop/nimbus-0.1.1/icons/32x32/places before I ran the ./configure command.

Many thanks,

---

