---
title: "Entire Ubuntu menu, task bar have dissappeared!!"
date: 2008-06-13
forum: Desktop Environments
---

### Post by spraveenitpro on 2008-06-13
Hi 

My Entire Menu bar consisting of 'places,system,preferences' and the task bar have disappeared. I am unable to launch any program or do anything. Alt-f2 also does not work.

praveen.

---

### Post by abhiroopb on 2008-06-13
right click on the desktop, select "terminal" type in the following:

```

gnome-panel

```

More information: [http://ubuntuforums.org/showthread.php?t=156602](http://ubuntuforums.org/showthread.php?t=156602)

---

### Post by spraveenitpro on 2008-06-14
Thank You, it worked!!!

---

### Post by alktlkbck on 2008-06-14
I need some help


I delete a file from desktop and lost panels

I have try 


sudo apt-get update
sudo apt-get install --reinstall gnome-panel



gnome-panel




rm -rt .gnome .gnome2 .gconf .gonfd .metacity




can only get to a terminal  ctrl+alt+f1to get back to desktop ctrl+alt+f7

---

### Post by rhardie on 2008-06-23
I just tried these things and none of them work.  Upon attempting to re-install gnome-penel, I receive error code:

"Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against the package should be filed.

The following information may hale to resolve the situaiton:

The following packages have unmet dependencies:
  gnome-panel: Depends" gnome-control-center (>=1:2.8.2-3) but it is not going to be installed
E: Broken packages"

My gnome was working just fine until, in the flicker of an eye, it just have me with wall paper on the screen and no task bar.

---

### Post by rainwalker on 2008-06-23
Try installing the "gnome-control-center" package, and then reinstall gnome-panel

---

### Post by rhardie on 2008-06-23
I did attempt the gnome-control-center and it too failed to load due to dependencies.

Hmmmmm.  Maybe I can power the sytem down, go watch a movie have a few vodka shots and like magic it will fix itself.  Naaaaaa.  Probably not.  But the, maybe I won't really care by that time. ;-)

---

### Post by rhardie on 2008-06-23
I did attempt the gnome-control-center and it too failed to load due to dependencies.

Hmmmmm.  Maybe I can power the sytem down, go watch a movie have a few vodka shots and like magic it will fix itself.  Naaaaaa.  Probably not.  But the, maybe I won't really care by that time. ;-)

Hey, that actually did work once!

---

### Post by &#24859; am best on 2009-03-09
I'm having the same problem too and did the guides that have been written above me but nothing is working! ](*,)

i tried turning off the compiz but it only gives me this error:

```
window manager error : unable to open X display
```

Help please T_T 

Don't tell me i have to reinstall my Linux Mint :(

FYI: I have to open the Terminal by Ctr+Alt+F1 'cause opening Terminal using the right-click mouse won't work either T_T

---

### Post by UbuntuNerd on 2009-03-09
can you guys try my solution Im almost sure it will work:
first copy this code to a piece of paper
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
make sure you leave spaces where spaces are in the code or it won't work.
next hit (Ctrl+Alt+f1) to get to the terminal. log in and enter your password, then enter the first line of the code follow by enter then the second line follow by enter then the third. hit (alt f7) to get back to your desktop to see if it work

---

### Post by &#24859; am best on 2009-03-09
@UbuntuNerd

Apparently it doesn't work for me :(

---

### Post by UbuntuNerd on 2009-03-09
> **&#24859 said:**
> @UbuntuNerd

Apparently it doesn't work for me :(
I know Linux Mint is similar to Ubuntu but I don't know that the code I provided will work for you. I know for sure it works in Ubuntu, and usually if this code didn't restore your panels(task bar) the next think I usually try is reinstalling the desktop "not the whole OS"
in Ubuntu's case this will be the code in a terminal:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by mister_p_1998 on 2009-03-10
Yeah,
my three-year-old did that I leave my machine on all day, and he was "Typing like Daddy" and hit the del key!
I now use a screen saver that locks the keyboard!

---

### Post by &#24859; am best on 2009-03-10
I've asked for help in the mint forum and one of the members suggested this:

> ```
su
```

```
cd /etc/X11
```

```
ls
```

Now, do you have a backup xorg.conf? If so you do this:

```
mv xorg.conf xorg.conf.wacom
```

```
mv xorg.conf.backup xorg.conf
```

```
init 6
```

But sadly the su command doesn't work in the terminal from ctr+alt+f1... and it says init 6 has to be root. 

this sucks, all i did was just installing wacom bamboo fun and one day, KABOOM! My mint desktop turns out this way :(

---

