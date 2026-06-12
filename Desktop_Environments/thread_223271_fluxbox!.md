---
title: "fluxbox!"
date: 2006-07-26
forum: Desktop Environments
---

### Post by davebradford on 2006-07-26
hi there, i made a post about a week ago regarding slow system, i was told to move to last demanding gui so i moved from gnome to fluxbox, however i find fluxbox very hard to use as i have been used to gnome now for a while, can anybody give me any tips on how to use fluxbox and get it setup? hopefully i will be able2 get it to do all the things gnome did.. fingers crossed!

---

### Post by tturrisi on 2006-07-26
What do you find hard to use about Fluxbox?  I never had any difficulty w/ it.  One needs to get accustomed to using the rt click mouse button to pull up the menu, left click on a menu item to to hold the menu & then select the desired program.

---

### Post by taurus on 2006-07-26
You can add some apps that you use all the time in ~/.fluxbox/menu.  Then, you just click on it instead of typing it from a terminal!!!

---

### Post by Riverside on 2006-07-26
> **tturrisi said:**
> What do you find hard to use about Fluxbox?  I never had any difficulty w/ it.I have been a Blackbox user (the window manager which Fluxbox is based on) since 2002, and have just migrated from SuSE 9.2 to Dapper, and also as an experiment (successful so far) from Blackbox to Gnome.  Blackbox (and Fluxbox) are *very* non-intuitive though, particularly when it comes to configuration.  The Fluxbox package obtained by running apt-get install fluxbox comes with no default menu file if I recall correctly, and creating a menu file can only be done manually using a text editor, and configuration syntax which will take the average user quite some time (days, rather than minutes or hours) to fully understand and learn.

When the original poster writes "tips on how to use fluxbox and get it setup", that is likely to be what he is referring to.

---

### Post by davebradford on 2006-07-26
thanks for the posts, the your right the reason i'm prob finding it hard to use is prob because i dont know where anything is! and everything is much more cut-down with flux, am i right in saying that you need to use a text editor to change the back ground as well!? just all seems a little long winded, ther also seems to be control panel like area/app !?

---

### Post by zba78 on 2006-07-26
You could always try menumaker ([http://menumaker.sourceforge.net/](http://menumaker.sourceforge.net/)). Once you've installed menumaker just run ```
mmaker -vf Fluxbox
``` and it should scan you r HDD and create some menu entries.

Please note that the **-f** option will overwrite any menu file that already exists.

---

### Post by taurus on 2006-07-26
> **davebradford said:**
> thanks for the posts, the your right the reason i'm prob finding it hard to use is prob because i dont know where anything is! and everything is much more cut-down with flux, am i right in saying that you need to use a text editor to change the back ground as well!? just all seems a little long winded, ther also seems to be control panel like area/app !?
You need to edit your ~/.fluxbox/menu & ~/.fluxbox/startup (background and what not) by hand...  Otherwise, try XFce4 then!

---

### Post by tturrisi on 2006-07-26
not sure if it's availabe for ubuntu, but on my debian systems w/ fluxbox I have used fluxconf: [http://packages.debian.org/stable/x11/fluxconf](http://packages.debian.org/stable/x11/fluxconf) to build menus & other tweaks.

If you want a lightweigt setup using fluxbox then just start with a base debian install & build it up with:
apt-get install x-window-system fluxbox fluxconf nedit emelfm mozilla-firefox

---

### Post by penquin on 2006-07-27
can you copy and paste the xfce menu to fluxbox menu?  How would you do that?  I have xubuntu and I need a lighter system manager so I would like to try fluxbox instead of xfce unless they use the same amount of resources.

---

### Post by h2gofast on 2006-07-27
No you will not be able to do all the things gnome did.  With fluxbox, a few things do not get started automatically, and you can't really customize your background and themes the way you do it in gnome.  You can customize but it requires you to edit config files.   You are really going to have to read the documentation at fluxbox website, and come back with questions when you screw up your configs.  It's not hard to edit and the rewards are nice on the eyes.

DO NOT uninstall gnome-desktop.  Leave it there.  If you scew fluxbox, just ctrl-alt-backspace and log into a gnome environment.


Here's a couple of snippets to get you started.  I don't think ubuntu's fluxbox gives you a menu off the bat.

cheers, h2.

cd .fluxbox
 cat menu
[begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)
[end]

from startup
# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &
fbsetbg -f /usr/share/fluxbox/styles/backgrounds/Arainyday.jpg &
gkrellm -w &
gnome-power-manager &
#rox --pinboard=MyPinboard &
# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox


from keys 
Mod1 s :ExecCommand xmms
Mod1 x :ExecCommand xterm
Mod1 f :ExecCommand /opt/swiftfox/swiftfox
Mod1 a :ExecCommand aterm -tr -trsb -shading 60 -sl 500 -bw 0 -fg white -fade 70
Mod1 k :ExecCommand konqueror
Mod1 q :ToggleDecor
Mod1 e :ExecCommand evolution
Mod1 b :ExecCommand /usr/bin/btdownloadgui.bittornado
Mod1 m :ExecCommand xmms
Mod1 r :ExecCommand rox-filer
Mod1 n :ExecCommand nautilus --no-desktop

---

### Post by nalmeth on 2006-07-28
Here is a fluxbox customization guide
[https://wiki.ubuntu.com/Fluxbox](https://wiki.ubuntu.com/Fluxbox)

If it's too much hassle, I'd just go with xfce

sudo aptitude install xubuntu-desktop

---

### Post by tturrisi on 2006-07-28
Use Synaptic to install Fluxconf!
> FluxBox configuration utility
FluxConf is a simple GTK 2.0 application allowing fast and easy configuration
of the Fluxbox window manager and its keyboard shortcuts.  This package also
includes the fluxkeys, fluxmenu and fluxbare utilities. 
Fluxmenu is a graphical frontend that you can use to build your menus.
Screenshots:
[http://devaux.fabien.free.fr/flux/](http://devaux.fabien.free.fr/flux/)

---

### Post by mooreted on 2006-07-28
Actually, once you get used to it, FluxBox is easy to use. It is frustrating at first, but once you learn to use it, it's a great window manager. 

One trick I use for the background is to edit the fluxbox menu script so the root command points to ~/background/background.jpg. Then when I want to change the background, I just copy a new pic to the ~/background folder and name it "background.jpg". Restart Flux and I have a new background. 

I also put all the programs I use every day on the top of the Fluxbox menu. I seperate my favorite programs with dashes using the "nop" command in the Fluxbox menu like so: [nop] (--------------------).

---

### Post by davebradford on 2006-07-31
[LEFT]thanks for all your advice! starting to get the hang of it now.. although i'm still seaching for a way to speed up gnome, flux is a very nice desktop.. loving the simpilcity..


[/LEFT]

---

