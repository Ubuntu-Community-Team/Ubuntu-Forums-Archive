---
title: "After installing gnome desktop, desktop disappeared (ubuntu 13.10)"
date: 2014-01-30
forum: Desktop Environments
---

### Post by Alberto_Costa on 2014-01-30
Hi all.
I need your help in order to get out a mess I've got in. After installing successfully Ubuntu 13.10, I wanted to install some missing codecs in order to open mp3 and mp4 files. I found the solution in a website page which as well was explaning how to change the desktop interface installing gnome desktop. I should have never done it. I'm unexperienced and I've no skills in dealing with operative systems.
I entered this command line:

sudo apt-get install gnome-shell ubuntu-gnome-desktop

consequently, the background changed to black and icons disappeared.
I have no clues about how to get rid of this gnome and restore Unity which served me so well in at least three happy years of using Ubuntu without issues.
Sorry for my broken English.
I hope you could help me, and I beg you not to scold me too much for my imprudence.
Thanks a lot
Alberto Costa

---

### Post by egeezer on 2014-01-31
It may be possible for you to access your original Unity desktop without a big fuss. Try the following:

Hold down Control and the left Alt key and press F1 - this will give you a console; run
```
sudo shutdown -r now
```
This will restart the computer.  In all likelihood it will boot to the login page.  Above the blank for the password will be a symbol, either an Ubuntu logo or a blank (on the upper right-hand corner of the password line).  Click on it, and it will show the options for the desktop you want to use.  Choose the original one, sign in, and you should be back in business.
Multiple desktops on Ubuntu are chosen at login; I believe that is what you set up with that installation command.

---

### Post by GratefulDean on 2014-01-31
> **egeezer said:**
> It may be possible for you to access your original Unity desktop without a big fuss. Try the following:

Hold down Control and the left Alt key and press F1 - this will give you a console; run
```
sudo shutdown -r now
```
This will restart the computer.  In all likelihood it will boot to the login page.  Above the blank for the password will be a symbol, either an Ubuntu logo or a blank (on the upper right-hand corner of the password line).  Click on it, and it will show the options for the desktop you want to use.  Choose the original one, sign in, and you should be back in business.
Multiple desktops on Ubuntu are chosen at login; I believe that is what you set up with that installation command.


I ran into this issue as well just a few hours ago.  I upgraded from 12.04 to 13.10, did my app-get updates then installed both Gnome and Cinnamon.  Now my Ubuntu desktop is black and I can't put any wallpaper on it.  (I don't keep icons on the desktop but I assume had I any they would be gone too.)  Gnome and cinnamon both seem fine. (well, regular Gnome and Cinnimon anyway, the rest launch to almost blank screens).  I tried your suggested solution and all it did was put the Ubuntu desktop back to default. 

I should add, 10.14, Maverick Meerkat, was my first foray into Linux. I had to kill it and not pick it up again until I acquired a second laptop that I could use Ubuntu, or any flavor of Linux, on.  That was 12.04, Precise Pangolin.  The problem is, *any* time I tried to change the look or add another desktop environment things get buggered. It makes me sad. :(

---

### Post by deadflowr on 2014-01-31
Can't you just log out and change the desktop back to unity?

Does ctrl+alt+backspace still work?
or ctrl+alt+del?
or the logout option in the user settings control in the panel.

---

### Post by GratefulDean on 2014-01-31
> **deadflowr said:**
> Can't you just log out and change the desktop back to unity?

Does ctrl+alt+backspace still work?
or ctrl+alt+del?
or the logout option in the user settings control in the panel.

Unfortunately no, neither does rebooting.  And by Unity, I assume you mean Ubuntu.  

The options I am given are:
[LIST]
[*]Cinnamon
[*]Cinnamon (Software Rendering)
[*]Gnome
[*]Gnome Classic
[*]Gnome Flashback
[*]Gnome Flashback (no effects)
[*]Ubuntu (Default)
[/LIST]

---

### Post by deadflowr on 2014-01-31
Does selecting Ubuntu(unity) cause a login loop?

---

### Post by Alberto_Costa on 2014-02-01
> **egeezer said:**
> It may be possible for you to access your original Unity desktop without a big fuss. Try the following:  Hold down Control and the left Alt key and press F1 - this will give you a console; run ```
sudo shutdown -r now
``` This will restart the computer.  In all likelihood it will boot to the login page.  Above the blank for the password will be a symbol, either an Ubuntu logo or a blank (on the upper right-hand corner of the password line).  Click on it, and it will show the options for the desktop you want to use.  Choose the original one, sign in, and you should be back in business. Multiple desktops on Ubuntu are chosen at login; I believe that is what you set up with that installation command.
Thank you for trying to help me. Unfortunately I did as you suggested, but I found only one option, that is Ubuntu desktop, which leads me in the same situation I'm stuck in (desktop and wallpaper disappeared.).
I'm very grateful for your help, for I'm not willing to adventure me in a reinstallation, first of all because the one installation I did I were helped by a friend who as well found it very hard to succeed in it because of problems with partitioning (he had to wipe out a partion made from hp in order to go on with the installation). I'm using an HP Pavillion dv6 laptop.
Alberto

---

### Post by GratefulDean on 2014-02-01
> **deadflowr said:**
> Does selecting Ubuntu(unity) cause a login loop?

What would a login loop look like?

---

### Post by deadflowr on 2014-02-01
> **GratefulDean said:**
> What would a login loop look like?

You login and then it seems to load only to go back to the login screen.

---

