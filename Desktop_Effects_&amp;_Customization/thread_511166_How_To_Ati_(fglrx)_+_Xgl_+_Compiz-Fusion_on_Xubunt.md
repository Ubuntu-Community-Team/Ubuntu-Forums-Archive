---
title: "How To: Ati (fglrx) + Xgl + Compiz-Fusion on Xubuntu 7.04"
date: 2007-07-27
forum: Desktop Effects &amp; Customization
---

### Post by spidernik84 on 2007-07-27
So, here's a step-by-step guide for enabling **compiz-fusion on Xubuntu 7.04**, using **official Ati fglrx drivers and Xgl session**.

Credits goes to many people's work, on which this guide is almost totally based upon: to Mr. Greencastle for xgl installation, to Vorian for compiz-fusion and ati setup, and to treviño for the repositories and packages.

**Miscellaneous resources:**

>> [Video of Compiz Fusion in action]("http://www.youtube.com/watch?v=E4Fbk52Mk1w&v3")

>> [Official Compiz-Fusion Forum]("http://forums.opencompositing.org/viewforum.php?f=6")

[COLOR=Red]**Warning:**[/color]This guide is intended for Xubuntu feisty 7.04 only.  Compiz Fusion is already available in Gutsy.

[COLOR=Red]**Disclaimer:**[/color] although i never had any crash on my own machine, Compiz-fusion is still under heavy development. As for this, it's stability may be poor in certain circumstances; so, you are warned...save your work often ;D 
Seriously, using this you "may" lose important data or screw something up. Use at your own risk, i'm not to be considered responsible for any damage.


[COLOR="DarkRed"][SIZE="6"]PART 1 of 2: Installing XGL and configuring XGL-Session[/SIZE][/COLOR]

After installing Feisty, make sure your system is completely updated. Paste this into a terminal:

```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade

```

First step is getting Ati-fglrx drivers set up. To do this use the Restricted Driver Manager.

```
System >> Administration >> Restricted Drivers Manager
```

Enable your ATI driver (By clicking the little box) and let it do its thing. Once finished, reboot the computer and make sure fglrx loaded correctly. There should be an icon (small and green) in the notification area telling you that you have restricted modules loaded.

Now we need to install XGL.

```
sudo aptitude install xserver-xgl
```

Now we must create some script to get Xgl work. Open a terminal and issue the following command:

```
sudo mousepad /usr/local/bin/startxgl.sh
```

Now copy and paste this into the editor that pops up:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session xfce4-session
```

**SAVE THIS FILE!** Once its done saving, close mousepad editor and make that file executable by pasting this into a terminal:

```
sudo chmod a+x /usr/local/bin/startxgl.sh
```

Now we need to make a way to start that session from your login screen. Paste this into a terminal:

```
sudo mousepad /usr/share/xsessions/xgl.desktop
```

And paste this again into the editor:

```

[Desktop Entry]
Encoding=UTF-8
Name=Xfce with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

Now make this script executable too by pasting this into a terminal:

```
sudo chmod a+x /usr/share/xsessions/xgl.desktop
```

Xgl should now be ready to start, keep your session open, we'll test it later.


[COLOR="DarkRed"][SIZE="6"]PART 2 of 2: Installing Compiz-Fusion and configuring it for auto-start[/SIZE][/COLOR]

First, remove desktop effects
```
sudo aptitude remove compiz-core desktop-effects
```
add the following to your /etc/apt/sources.list
```
sudo mousepad /etc/apt/sources.list
```
**Option A: for i386**```
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```Packages at: [http://3v1n0.tuxfamily.org/dists/feisty/eyecandy]("http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/index.html")

**Option B: for amd64**```
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64

```Packages at: [http://3v1n0.tuxfamily.org/dists/feisty/eyecandy-amd64/](http://3v1n0.tuxfamily.org/dists/feisty/eyecandy-amd64/)

Add the key
```
gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg --export --armor 81836EBF | sudo apt-key add -
```
Update your system
```

sudo aptitude update
sudo aptitude upgrade

```
Now let's proceed installing Compiz-fusion:
```
sudo aptitude install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
```

Now it's time to check if we did everything right :)

Hit Ctrl+alt+backspace, you'll be taken to login screen. Click on "Session" and choose "Xfce with XGL" from the list. If asked, do not make it as the default session (in case of trouble you'll be able to restore everything without too many efforts).

Log-in, obviously crossing your fingers. If everything went right, you'll see your desktop as usual, just with an "x" cursor instead of the classic pointer. That's a good sign, xgl should have loaded correctly.

Hit "Alt+F2" and issue this command:
```
compiz --replace
```
After some seconds you'll see window decoration appear. Play around, you should notice immediately if everything worked as intended.

Now, if compiz loaded, we should **make it autostart at every log-in**.

Go to "Xfce Menu" >> "Settings" >> "Autostarted applications" and hit "Add".

Configure the command as shown below:

[[IMG]http://img50.imageshack.us/img50/9447/scrautostartfq3.th.jpg[/IMG]](http://img50.imageshack.us/my.php?image=scrautostartfq3.jpg)


This should work in most situations, for advanced commands [look at this thread]("http://forums.opencompositing.org/viewtopic.php?f=48&t=729").

**Some quick tricks:**
- Hold CTRL + ALT keys and with the left mouse button rotate the cube
- Super + E activates the Expo plugin
- Hold Super + Shift and with your mouse paint fire on your desktop
- Super + Shift + C will erase the fire paint
- Super + Tab activates the Ring Switcher plugin

Enjoy! :D

[SIZE="6"][COLOR="DarkRed"]General Troubleshooting:[/COLOR][/SIZE]

If you have trouble getting your window decorations working, and use beryl 
alt+F2
```
compiz --replace -c emerald &
```to install beryl visit [Pricy's Thread]("http://ubuntuforums.org/showthread.php?t=272104")
```
sudo apt-get install beryl beryl-manager emerald-themes
```You can configure Compiz Fusion by going to System>Preferences>CompizConfig Settings Manager
[B]
Other troubleshooting resources may be found at [/B][Vorian's original thread]("http://ubuntuforums.org/showthread.php?t=481314&highlight=xgl+ati")


BTW, I'll be here trying to help anyone. Ain't an hardcore Linux user, so i'm not gonna answer to everyone getting into trouble, not because i've got something against you all, but because probably i won't be ABLE to answer ;D :lolflag:
[SIZE="6"][COLOR="DarkRed"]
Credits:[/COLOR][/SIZE]

Again, **Huge thanks to** Mr. Greencastle for Ati-Fglrx and Xgl installation, to Vorian for compiz-fusion setup, and to treviño for compiz-fusion repositories and packages. I repeat: I just put their wonderful guides and work togheter and managed to use them on Xubuntu :P

---

### Post by ocean223 on 2007-07-27
Well, you did post a disclaimer........

Here's what I got :

Ctrl+alt+ backspace got me a blank desktop after logging in the first time. Now it gets me to a terminal to log in.
After cold start all is normal again.
Choice for "session" never appeared.

Alt+f2 gets me nothing after typing "compbiz --replace" and clicking "run"
 Am using  An ATI Radeon 9600 XT card.
At least It ain't broke.
Compbiz MAnager is there.
Maybe I'll start over..........

---

### Post by spidernik84 on 2007-07-28
> **ocean223 said:**
> Well, you did post a disclaimer........

Here's what I got :

Ctrl+alt+ backspace got me a blank desktop after logging in the first time. Now it gets me to a terminal to log in.
After cold start all is normal again.
Choice for "session" never appeared.

Alt+f2 gets me nothing after typing "compbiz --replace" and clicking "run"
 Am using  An ATI Radeon 9600 XT card.
At least It ain't broke.
Compbiz MAnager is there.
Maybe I'll start over..........
Uhm, that's weird...
Did you chmod all the files where instructed?
Maybe you could try a 
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by csthiang on 2007-07-28
I have a qn to ask...how do i get it to work in gnome instead of fxce4?

I have tried compiz --replace in gnome but it does not work...

However it work nicely in fxce4...

Thanks for the guide!

---

### Post by spidernik84 on 2007-07-28
> **csthiang said:**
> I have a qn to ask...how do i get it to work in gnome instead of fxce4?

I have tried compiz --replace in gnome but it does not work...

However it work nicely in fxce4...

Thanks for the guide!

Just modify the last line in the file /usr/local/bin/startxgl.sh this way:

original line in the file:
```

exec dbus-launch --exit-with-session xfce4-session

```

modified line:
```

exec dbus-launch --exit-with-session gnome-session

```

I recommend you to have a look at Vorian's original guide [here]("http://ubuntuforums.org/showthread.php?t=481314").

Cheers :P

---

### Post by csthiang on 2007-07-28
> **spidernik84 said:**
> Just modify the last line in the file /usr/local/bin/startxgl.sh this way:

original line in the file:
```

exec dbus-launch --exit-with-session xfce4-session

```

modified line:
```

exec dbus-launch --exit-with-session gnome-session

```

I recommend you to have a look at Vorian's original guide [here]("http://ubuntuforums.org/showthread.php?t=481314").

Cheers :P

got it work...sweet! cheers !

However, I now have problems using ATI powerplay  using aticonfig... it says error: unable to obtain powerplay information.

---

### Post by spidernik84 on 2007-07-28
> **csthiang said:**
> 
However, I now have problems using ATI powerplay  using aticonfig... it says error: unable to obtain powerplay information.
Here's what i've found googling around:

> DISPLAY=:0 aticonfig –lsp
DISPLAY=:0 aticonfig –set-powerstate=3
DISPLAY=:0 aticonfig –set-powerstate=1
Hitting those command should do the trick while running xgl.

---

### Post by csthiang on 2007-07-29
> **spidernik84 said:**
> Here's what i've found googling around:


Hitting those command should do the trick while running xgl.

sorry about the qns i have, but this is what I get when executing the commands:
> 
sudo DISPLAY=:0 aticonfig –lsp

sudo: DISPLAY=:0: command not found


---

### Post by spidernik84 on 2007-07-29
> **csthiang said:**
> sorry about the qns i have, but this is what I get when executing the commands:
Uhm, actually i didn't have any chance to test them (no mobility radeon here :(). Here's an illuminating [thread]("http://ubuntuforums.org/archive/index.php/t-390418.html").

---

### Post by csthiang on 2007-07-29
> **spidernik84 said:**
> Uhm, actually i didn't have any chance to test them (no mobility radeon here :(). Here's an illuminating [thread]("http://ubuntuforums.org/archive/index.php/t-390418.html").

Thanks for those commands, got it working by removing sudo in front of it...lol

---

### Post by FunkyMunky on 2007-08-05
THANKS ALOT MAN *kiss kiss hug hug*. ihave been struggling with fglrx + desktop effects for very long without any success. i thought that i was stuck with boring desktop untill i get an nvidia card :)

anyway, just a little problem. my keyboard layout has changed to us from si (slovenian). how do i fix that?

---

### Post by spidernik84 on 2007-08-06
Sorry for the later answer, i was outside Italy :P for holidays
> **FunkyMunky said:**
> THANKS ALOT MAN *kiss kiss hug hug*

Errr...i'd rather go with an handshake :D
> 
anyway, just a little problem. my keyboard layout has changed to us from si (slovenian). how do i fix that?
I solved through 
main menu >> settings >> keyboard settings >> layouts

and there adding the layout i needed!

Cheers ;)

---

### Post by FunkyMunky on 2007-08-06
alright it works perfectly now :)

ok a handshake will do ;)

---

### Post by macaholic on 2007-08-07
Hi, I have tried this and I have the newest ATI driver from there site and i followed these instructions to install xgl. My issue is that when I hit options at the login screen to switch sessions Ubuntu freezes (although I can still move the mouse) and I have to restart the computer. Any ideas?
Thanks in advance.

---

### Post by FunkyMunky on 2007-08-07
ok another stupid question...

when i go to fullscreen in gqview, panels are still visible. how do i fix that?
here's a screenie:
[http://s8.photobucket.com/albums/a13/Safcol/?action=view&current=fulscreen.png](http://s8.photobucket.com/albums/a13/Safcol/?action=view&current=fulscreen.png)

---

### Post by kiwiboyus on 2007-08-17
I have followed Part 2 of this guide to install compiz-fusion on my laptop. I am running Linux Mint 3.0 w/gnome and compiz-fusion seems to be running correctly except for one thing. I have an update showing up for beryl-plugins that fails to install. Since I am now running compiz-fusion I don't actually need anything associated with beryl installed anymore right? Can I just uninstall beryl?

---

### Post by [Alsharifi] on 2007-08-26
hey im on fiesty and i followed this hot to step by step.


every thing seems to have workked correctly,i get the correct choose of sessions,i choose the xgl one.its takes me to a black screen with the "X" and nothing happenes after that,even if i press alt+f2. then i get an error message that i didnt copy and then i get back to the login screen?

haha i know sounds pretty crazy,anyone help?

---

### Post by smallcaps on 2007-08-31
hiya,

i am having problems installing the key for the repositories for tuxfamily.org. when i try the following command:

> ~$ gpg --keyserver subkeys.pgp.net --recv-keys DD800CD9
gpg: requesting key DD800CD9 from hkp server subkeys.pgp.net

i get:
> 
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


i have cheked my network settings and everything seems to be fine. could the server be down or the key has changed?

thanks!

---

### Post by FearTheSmurf on 2007-09-06
Hi all 
Im falling down early in this guide at the** sudo mousepad /usr/local/bin/startxgl.sh ** command all i get back is this

**sudo: mousepad: command not found** any ideas?

---

### Post by misse- on 2007-09-06
Yeah, you don't have mousepad installed. If you're not using xubuntu you can try ```
sudo gedit 
```or ```
sudo kate
```

Otherwise you can always install mousepad via

```
sudo apt-get install mousepad
```

or use a terminal based texteditor like nano

```
sudo nano /path/to/file
```

---

### Post by FearTheSmurf on 2007-09-06
Thanks thats done it these effects are well good:guitar:

---

### Post by JpMaxMan on 2007-09-20
Well, this was totally working, and then it just stopped.  Is anyone aware of an update that would have broken this?  I'm using ubuntu / feisty w/ Automatix.

---

