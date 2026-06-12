---
title: "server-installation - enlightenment only??"
date: 2005-11-23
forum: Desktop Environments
---

### Post by mboto on 2005-11-23
hi there,

i want to make a server-expert installation
then i want to add a window manager - enlightenment e17.

what packages do i need to get an ubuntu with just enlightenment as desktop enviroment (with entrance etc. (later adding some gnome and kde programms) working???


in my search i found only howtos for an already running system - so as i m quite a newbie i found no answer  for this. cant be that difficult i think

studpid question maybe - but i dont know better.
thanks for any help
greets

---

### Post by Peter76 on 2005-11-23
Hi there, you have to do an server install ( don't know about the expert, shouldn't be nescessary I think ) which gives you a really clean and bare system to go from. Then, after your first login:

sudo vi /etc/apt/sources.list and uncomment the universe and backports repositories;
sudo apt-get update
sudo apt-get upgrade ( to bring your system up to date )
sudo apt-get install gdm x-window-system-core (and any other packages you want )

Then check this thread for enlightenment 17:

[http://ubuntuforums.org/showthread.php?t=79155](http://ubuntuforums.org/showthread.php?t=79155)

good luck

---

### Post by mboto on 2005-11-23
correct me if i m wrong. 
but wouldn t gdm mean that the gnome login manager would be installed.
with enlightenment as login manager entrace would be my choice.
i understand this to be two packages:
1. gdm - the gnome login manager
2. x-window-system-core

so if i m right than number 2 would be the only package needed to get a desktop enviroment running???

in another thread ([http://www.ubuntuforums.org/showthread.php?t=90954](http://www.ubuntuforums.org/showthread.php?t=90954)) i found x-window-system instead of x-window-system-core - so which one of these is right

thanks for your help so far.

---

### Post by Peter76 on 2005-11-23
I don't know anything about enlightenment, so if it has it's own login manager, definitely use that.
The option for sure is x-window-system-core. This is the base for any graphical desktop environment ( afaik ), but apt-get will solve all dependencies for you ( still don't know about this enlightenment thing ). Give it a try and post any problems, see if I ( or the rest here ) can do
Good luck

---

### Post by mboto on 2005-11-24
seems to work until one point:

what i made
- i made a server installation
- sudo nano /etc/apt/sources.list
added the line: 
deb [http://soulmachine.net/breezy](http://soulmachine.net/breezy) unstable/ 
- saved the file
- sudo nano /etc/apt/preferences
added (actually this is an new - means empty- file): 
Package: enlightenment
Pin: version 0.16.999*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999*
Pin-Priority: 999
- saved the file
- sudo wget soulmachine.net/public.key
- sudo apt-key add public.key

- sudo apt-get update
- sudo apt-get upgrade
- sudo apt-get install x-window-system-core
when the blue screen where the resolution can be choosed appeared i just said okay and changed nothing - so only the options that were already marked were chosen
- sudo apt-get install enlightenment
- sudo apt-get install enlightenment-data
- sudo apt-get eutils
- sudo apt-get entrance

until then everything seemed to work fine
but then when i type 
- startx
the screen goes black and after a few seconds my monitar goes to standby (like no computer is on)
after restarting it got even worse - after booting the screen again goes black - even before i can type anything. don t know what could be causing this.

any help would be great...

---

### Post by Peter76 on 2005-11-28
give "sudo dpkg-reconfigure xserver-xorg" a try..

---

### Post by Bone Down on 2006-02-15
any update on this?
I have gone as far as this and now I am booting into e16, but there are no icons, no menus, etc.

Any idea where I go from here? I am looking forward to getting this up and running, I like what i have seen about it so far on the net, and the basic desktop looks promising, I just need to find a good howto for server - e16 install so that I can hopefully get at the least xterm and firefox to show up, and maybe go from there...

even the evolution www is not all that helpful.

---

### Post by wmvdg123 on 2006-02-18
Hi mboto,
Have you created an xsession file?
sudo nano /home/(your username)/.xession

Write:
exec enlightenment

and save it.
Try xstart, if it dosen't work then you have a configuration problem with xorg.
Wayne

---

### Post by dlai on 2006-02-18
Actually i just did excactly what you wanted.... It it by far the easiest to install x-window-system-core, and then go through the CVS install method [http://www.ubuntuforums.org/showthread.php?t=97199&highlight=e17+cvs]("http://www.ubuntuforums.org/showthread.php?t=97199&highlight=e17+cvs")
after that you ```
nano .xsession
```
and write ```
exec /opt/e17/bin/enlightenment
```
to make entrance your login manager ```
update-rc.d entrance start 99 2 3 4 5 . stop 01 0 1 6 .
```

I have found one problem though... It is not possible to log in through the "Default" session which I might think disables the ability to change in the menus? Could anyone tell me if that is true... If the menu structure that is created in the .e/e/applications... is only possible to change through the "Default" session???:-k

---

### Post by hizaguchi on 2006-02-20
Heh, I gave this a try yesterday (using the Easy E17 compiling method) and it worked great except for my one dumb move... I didn't install a terminal before I booted into E, so I couldn't apt-get one.  Took me forever to figure out that ctrl-alt-F1 would get me to one. :-D

edit: Looking back now, I think if I had used the "run" button in E, and specified that eterm was in /opt/e17, I could have saved myself alot of trouble.  Doh.

---

### Post by dlai on 2006-02-28
Eap's have a problem being created when using entrance as display manager...
problems with the way entrance handles "something"(I have no idea what) persist... when using other display manager it seems alright

---

