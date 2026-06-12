---
title: "Openbox tips &amp; tricks"
date: 2008-07-07
forum: Desktop Environments
---

### Post by Inxsible on 2008-07-07
Can some of the Openbox users share their openbox tips and tricks?

Openbox is my first WM which does not come standard with a panel. I was wondering if Openbox users install third party panels or make do without it.

Also tips about how to configure your Openbox or the tricks that you learnt along the way would be great.

I currently run Openbox on Arch and am liking it a lot so far.

---

### Post by TenPlus1 on 2008-07-07
I use fbpanel on openbox which is a really good panel that not only shows debian software already installed but lets you place plugins in the panel itself and uses very little memory...

Also I have installed obconf and obmenu to configure openbox and it's menu :)

---

### Post by Jose Catre-Vandis on 2008-07-07
Suggest you search out the Openbox Random Chat thread on the forum and have a good read

---

### Post by urukrama on 2008-07-07
I don't use any panel with Openbox. Its alt-tab dialog is good for switching between windows or seeing what you have running. The client-combined-menu is also useful for this, as are applications like skippy.

It takes a short while to get used to this, but when you give it some time you'll see the benefits of working this way. Or at least, I did.

---

### Post by Inxsible on 2008-07-08
If I am not using a panel, how would I switch to an app which is in the system tray. pidgin or skype for example?

---

### Post by atomkarinca on 2008-07-09
> **Inxsible said:**
> If I am not using a panel, how would I switch to an app which is in the system tray. pidgin or skype for example?

You can use docker or trayer to just show the tray icons. I use pypanel and it has an icon tray. I also configured the panel so that it leaves a 50-pixel space on the top left, this way I can right-click on that space :)

---

### Post by TenPlus1 on 2008-07-09
Alt+Tab switches between applications, but if you middle-click your mouse (if you have a middle button that is), a list appears of open applications too...

---

### Post by firmit on 2008-07-09
If you want a panel : lxpanel - which also is part of the LXDE DE. Check it out!

On openbox: [http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by urukrama on 2008-07-09
> **Inxsible said:**
> If I am not using a panel, how would I switch to an app which is in the system tray. pidgin or skype for example?

I use docker, which is a simple system tray that loads in the dock. I also load lal, a simple clock into the dock, as well as bbpager, a simple pager.

---

### Post by Inxsible on 2008-07-09
> **atomkarinca said:**
> You can use docker or trayer to just show the tray icons. I use pypanel and it has an icon tray. I also configured the panel so that it leaves a 50-pixel space on the top left, this way I can right-click on that space :)Thanks I will have a look at docker and trayer

> **TenPlus1 said:**
> Alt+Tab switches between applications, but if you middle-click your mouse (if you have a middle button that is), a list appears of open applications too...I know about the middle button, but it doesn't show the apps in the tray. At least not for me.

> **firmit said:**
> If you want a panel : lxpanel - which also is part of the LXDE DE. Check it out!

On openbox: [http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)I was planning on not using a panel

> **urukrama said:**
> I use docker, which is a simple system tray that loads in the dock. I also load lal, a simple clock into the dock, as well as bbpager, a simple pager.I need the docker only for the system tray. I have my clock in conky itself and as for paging, i have my keyboard shortcuts to go to different desktops. Openbox 3 also has a small graphic that comes up when you try to switch desktops.

---

### Post by sayakb on 2008-07-09
I configured Openbox with Thunar, fbpanel and ROX.
[http://ubuntuforums.org/album.php?albumid=197&pictureid=968](http://ubuntuforums.org/album.php?albumid=197&pictureid=968)
(I got rid of the top panel thingy!)
I use ROX mainly to get desktop icons (thunar doesnt give me that -- or I dont know how to configure thunar for desktop icons)
I have created ROX launchers that launch thunar with different arguments. 
Plus, fbpanel is excellent.. dint like pypanel much.
Plus, I used urukrama's blog: [http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)
:D :D :D

---

### Post by urukrama on 2008-07-09
> **LinuxIsInnovation said:**
> I use ROX mainly to get desktop icons (thunar doesnt give me that -- or I dont know how to configure thunar for desktop icons)
I have created ROX launchers that launch thunar with different arguments.

Thunar cannot draw the desktop. 

Why don't you use iDesk instead for icons on the desktop? It looks like a simpler (and possibly lighter) way of accomplishing what you want to achieve.

---

### Post by Inxsible on 2008-07-09
You can also use pcmanfm to get desktop icons if you are not into installing multiple apps.

PCManFM is a much better file manager than ROX, IMO

---

### Post by sayakb on 2008-07-09
iDesk has a backdrop/wallpaper support? Or should I have to use feh?

---

### Post by urukrama on 2008-07-09
iDesk doesn't set a wallpaper; it only places icons on the desktop. To have a wallpaper, you'd have to use Feh, hsetroot, nitrogen, or something like that.

PCManFM does set a wallpaper and icons, though. It resembles Thunar a bit in looks.

---

### Post by Inxsible on 2008-07-09
> **urukrama said:**
> iDesk doesn't set a wallpaper; it only places icons on the desktop. To have a wallpaper, you'd have to use Feh, hsetroot, nitrogen, or something like that.

PCManFM does set a wallpaper and icons, though. It resembles Thunar a bit in looks. +1 if you install the tango-icon-theme - which you may already have since you have Thunar and create a file called ~/.gtkrc-2.0 and put the following in the file```
gtk-icon-theme-name = "Tango"
``` your folders and file icons will use the tango icons. you can also use different icon themes that way..human... hicolor etc. etc.

Honestly, I dont use the desktop icon feature of pcmanfm...coz I like my desktop to be clean. and I use Feh as my wallpaper changer

---

### Post by Inxsible on 2008-07-09
If I use pcmanfm to set my wallpaper...how would I make sure that the wallpaper stays on reboot..

I currently use ```
eval `cat $HOME/.fehbg` & 
``` to recall my last wallpaper. If pcmanfm can recall the set wallpaper, then I may just get rid of feh :) coz I use Mirage as my image viewer anyway.

EDIT: I tried logging out and then logging in again and pcmanfm doesn't rbr the wallpaper. But the moment I click on the pcmanfm icon in fbpanel, the wallpaper appears. So I guess we can just add pcmanfm in the autostarts.sh file for openbox.

Another problem is that my conky stays below the wallpaper set by pcmanfm. I even tried ```
killall conky && conky &
``` but conky would still not show up if the wallpaper was set by pcmanfm

---

### Post by walkerk on 2008-07-09
Always been a fan of Pypanel... sucks it is no longer developed. I just applied the patch to buffer it like attached...

---

### Post by derrick81787 on 2008-08-19
I use Openbox with fbpanel.  I also use XFE for a file browser because it is really lightweight and comes with a simple text editor and a simple image viewer.  I use xsetbg to set the desktop background, and xscreensaver for a screensaver.

Claws-mail and Kazehakase are lightweight and functional replacements for Thunderbird and Firefox, and they are written entirely in GTK.  I installed xcalendar and edited my panel so that when I click on the clock, the calendar pops up just like it does in GNOME.  I try to use lightweight X11 programs as often as possible.  They're very lightweight and still functional.

Fbpanel is very flexible and fun to use.  For instance, I wrote a little shell script that prints what percentage of my battery is left, and I have that embedded in my panel to use as a battery monitor.  You can also use zenity to make a bunch of simple but useful tools that might be lacking compared to GNOME or KDE.  I used it to make a simple logout dialog, so when I click the logout button on my panel, a dialog pops up asking if I want to shutdown/reboot, etc.

I find that Openbox combined with a lot of other simple and lightweight tools makes for a very functional desktop.  There's no need to have huge programs that do a decent job at everything, when you can have several small ones that do their job very well.

- Derrick

---

### Post by picpak on 2008-08-19
This PPA might come in handy for somebody:

[https://launchpad.net/~k-belding/+archive](https://launchpad.net/~k-belding/+archive)

It has Nitrogen, sakura and tint2, some of the most commonly used apps with Openbox.

---

### Post by cardiel on 2008-09-19
> **walkerk said:**
> Always been a fan of Pypanel... sucks it is no longer developed. I just applied the patch to buffer it like attached...

can you share your pypanelrc??

---

### Post by Piraja on 2009-02-09
One quite easy way to change the wallpaper in Openbox is to use MC alias Midnight Commander, a command line file manager, and Feh. You can browse your image directory with it, and when you double-click on an image name, Feh opens up. Then you can right-click on the image and get a menu dialog, with a "file" entry that brings up the options for setting a background. I found this tip in a weblog, don't remember the exact source.

```
sudo apt-get install mc
mc
```

Voilà!

---

### Post by |{urse on 2009-06-13
i have tons of stuff here but i will try to list a few good things.


in order to get your urxvt (unicode, rxvt supporting full unicode and text colorizing) terminal embedded into your openbox background. This tutorial worked on gutsy, hardy and intrepid. I havent tried it on jaunty yet so if anyone tries it pls post findings.

> sudo apt-get install rxvt-unicode[http://wiki.archlinux.org/index.php/Openbox#Urxvt_in_the_background](http://wiki.archlinux.org/index.php/Openbox#Urxvt_in_the_background)
 *this looks great with even a modest bash.rc*
 *mine requires figlet (a fun little ascii art generator)* 

heres my bash.rc
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# Set some colors
BLACK='\e[0;30m'
BLUE='\e[0;34m'
GREEN='\e[0;32m'
CYAN='\e[0;36m'
RED='\e[0;31m'
PURPLE='\e[0;35m'
BROWN='\e[0;33m'
LIGHTGRAY='\e[0;37m'
DARKGRAY='\e[1;30m'
LIGHTBLUE='\e[1;34m'
LIGHTGREEN='\e[1;32m'
LIGHTCYAN='\e[1;36m'
LIGHTRED='\e[1;31m'
LIGHTPURPLE='\e[1;35m'
YELLOW='\e[1;33m'
WHITE='\e[1;37m'
NC='\e[0m'              # No Color

# don't put duplicate lines in the history. See bash(1) for more options
export EDITOR=/usr/bin/vim    # the one and only editor
export HISTFILESIZE=300000    # save 300000 commands
export HISTCONTROL=ignoredups    # no duplicate lines in the history.
export HISTSIZE=100000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize
shopt -s histappend
export PROMPT_COMMAND='history -a'


# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval `dircolors -b`
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi


. /home/will/.aliases
. /home/will/.functions

# export PATH=/opt/openoffice.org3/program:/home/will/bin:$PATH


#[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

if [ -z "$debian_chroot" -a -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# A color and a non-color prompt:    
#PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w \$ '

# Comment in the above and uncomment this below for a color prompt
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\] \$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
    ;;
*)
    ;;
esac

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc).
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi


# This line was appended by KDE
# Make sure our customised gtkrc file is loaded.
export GTK2_RC_FILES=$HOME/.gtkrc-2.0

#------------------------------------------
#------WELCOME MESSAGE---------------------
# customize this first message with a message of your choice.
# this will display the username, date, time, a calendar, the amount of users, and the up time.
clear
# Gotta love ASCII art with figlet
figlet -f lean "" $USER;
echo -e ""
echo -ne "Today is "; date
echo -e ""; cal ;
echo "";

#------------------------------------------
#------ENCRYPTION/DECRYPTION--------------
# requires gpg
# the proper way to use these functions is simply to enter "encrypt filename" or "decrypt filename"
encrypt ()
{
gpg -ac --no-options "$1"
}

decrypt ()
{
gpg --no-options "$1"
}
#------------------------------------------
#------Extraction of compressed files--------------
# from ARCH Wiki

extract () {
  if [ -f $1 ] ; then
      case $1 in
          *.tar.bz2)   tar xvjf $1    ;;
          *.tar.gz)    tar xvzf $1    ;;
          *.bz2)       bunzip2 $1     ;;
          *.rar)       rar x $1       ;;
          *.gz)        gunzip $1      ;;
          *.tar)       tar xvf $1     ;;
          *.tbz2)      tar xvjf $1    ;;
          *.tgz)       tar xvzf $1    ;;
          *.zip)       unzip $1       ;;
          *.Z)         uncompress $1  ;;
          *.7z)        7z x $1        ;;
          *)           echo "don't know how to extract '$1'..." ;;
      esac
  else
      echo "'$1' is not a valid file!"
  fi
} 
```If youre using devilspie, that method doesnt work correctly unless you are using nautilus to draw the desktop.  

wbar! wbar can be a static iconbar or a mac-style bar with full zooming, fully aesthecially customizeable but uses a ridiculously low amount of system resources compared to other open source docks like AWN or Kino-dock . I'ts only dependency is imlib2. 

first youll need to install imblib2 and sh ./configure make && sudo make install configure wbar from source.

> sudo apt-get install libimlib2> sudo apt-get install libimlib2-devget the source for wbar

 > [http://wbar.googlecode.com/files/wbar-1.3.3.tbz2](http://wbar.googlecode.com/files/wbar-1.3.3.tbz2)
or a deb (i havent personally tried it so your mileage may vary)

> [http://wbar.googlecode.com/files/wbar_1.3.3_i386.deb](http://wbar.googlecode.com/files/wbar_1.3.3_i386.deb)wbarconf a small configuration utility for wbar.

> sudo apt-get install wbarconfthen after you have installed all that run wbarconf to set position (can also be done under obconf) configure shortcus.

Setting up your autostart.sh

> sudo nano /home/username/.config/openbox/autostart.shheres mine for example

```
# Run the system-wide support stuff
. $GLOBALAUTOSTART

# Programs to launch at startup
#hsetroot ~/wallpaper.png &
#xcompmgr -c -t-5 -l-5 -r4.2 -o.55 &

# Programs that will run after Openbox has started

gnome-volume-manager & 
gnome-appearance-properties %F
#sudo network-manager &
# nm-applet & 
wicd-client &
sudo firestarter --start-hidden &
tint &
stalonetray &
gvolwheel &
conky &
wbar -pos bot-left -nanim 1
```so far as panels there are quite a few out there and there are tons of trays to choose from, some people like pypanel some like tint2 some like trayer others prefer stalonetray.

heres my .stalonetrayrc
nano /home/user/.stalonetrayrc
```
# background <color> # color can be specified as an HTML hex triplet or
# as a name from rgb.txt, note that '#' must be quoted
background "#54524e"

# decorations <decspec> # set trays window decorations; possible values for
# decspec are: all, title, border, none
decorations none

# display <display name> # as usual

# dbg_level <int> # controls the amount of debug info (for this setting to
# have effect, stalonetray sources must have been
# configured and compiled with --enable-debug)
# dbg_level 0

# fuzzy_edges [<level>] # enable fuzzy edges and set fuzziness level. level
# can be from 0 (disabled) to 3; this setting works
# with tinting and/or transparent and/or pixmap
# backgrounds (NEW in 0.7)
fuzzy_edges 0

# geometry <geometry> # tray's geometry in standard X notation
geometry 1280x24-0+0

# grow_gravity <gravity> # one of N, S, E, W, NW, NE, SW, SE; tray will grow
# in the direction opposite to one specified by
# grow_gravity; if horizontal or vertical
# direction is not specified, tray will not grow in
# that direction
grow_gravity NW

# icon_gravity <gravity> # icon placement gravity, one of NW, NE, SW, SE
icon_gravity NE

# icon_size <int> # specifies dimensions of typical icon slot
icon_size 27

# ignore_icon_resize [<bool>] # ignore icon attempts to resize their windows
# (NEW in 0.7)
ignore_icon_resize true

# max_width <int> # specifies maximal tray's width (0 = no limit)
max_width 110

# max_height <int> # specifies maximal tray's height (0 = no limit)
max_height 27

# no_shrink [<bool>] # disables shrink-back mode (NEW in 0.7)
no_shrink true

# parent_bg [<bool>] # whether to use pseudo-transparency
# (looks better when reparented into smth like FvwmButtons)
parent_bg false

# pixmap_bg <path_to_xpm> # use pixmap from specified xpm file for (tiled) background
# pixmap_bg /home/user/.stalonetraybg.xpm

# respect_icon_hints [<bool>] # try to respect icon hints (NEW in 0.7)
respect_icon_hints true

# skip_taskbar [<bool>] # hide tray`s window from the taskbar
skip_taskbar true

# sticky [<bool>] # make a tray`s window sticky across the
# desktops/pages
sticky true

# tint_color <color> # set tinting color (NEW in 0.7)
tint_color grey

# tint_level <level> # set tinting level; level ranges from 0 (disabled)
# to 255 (NEW in 0.7)
tint_level 255

# transparent [<bool>] # whether to use root-transparency (background
# image must be set with Esetroot or compatible utility)
transparent false

# vertical [<bool>] # whether to use vertical layout (horisontal layout
# is used by default)
vertical false

# window_layer <layer> # set the EWMH-compatible window layer; one of:
# bootom, normal, top
window_layer bottom

# window_type <type> # set the EWMH-compatible window type; one of:
# dock, normal, toolbar, utility
window_type dock

# withdrawn [<bool>] # start withdrawn (NEW in 0.7, prior to that
# withdrawn mode was default!)
withdrawn false

# xsync [<bool>] # whether to operate on X server synchronously (SLOOOOW)
xsync false
```another nerdy thing is skippy, its kind of like expose for mac. 
[https://launchpad.net/~k-belding/+archive/ppa/+build/751448]("https://launchpad.net/%7Ek-belding/+archive/ppa/+build/751448")

if you want 3d desktop switching.
[http://sourceforge.net/project/showfiles.php?group_id=59688](http://sourceforge.net/project/showfiles.php?group_id=59688)

heres the only tray volume control applet that worked well enough for me.
[http://sourceforge.net/projects/gvolwheel/](http://sourceforge.net/projects/gvolwheel/)

---

### Post by 37fleetwood on 2009-06-13
HI, I posted some open box questions that are similar to the ones asked in this thread. I have a Puppy Linux "Puplet" which uses Openbox, and have been so impressed with it I wanted to learn a bit more about just how flexible Openbox is.
Boxpup is brilliant, it uses Rox for the pinboard etc the latest uses Thunar as the file manager. it uses Wbar and Tint for launcher and taskbar. anyway you should check it out if you like Openbox. 4.13 I believe is the newest version but I'll post the threads for all of them as there is great information in them.

Boxpup:
[http://www.murga-linux.com/puppy/viewtopic.php?search_id=1264736300&t=32792](http://www.murga-linux.com/puppy/viewtopic.php?search_id=1264736300&t=32792)

Boxpup 4.1.2:
[http://www.murga-linux.com/puppy/viewtopic.php?search_id=1264736300&t=35767](http://www.murga-linux.com/puppy/viewtopic.php?search_id=1264736300&t=35767)

Boxpup 413:
[http://www.murga-linux.com/puppy/viewtopic.php?search_id=1264736300&t=41378](http://www.murga-linux.com/puppy/viewtopic.php?search_id=1264736300&t=41378)

here is a screencap of my Boxpup:
[IMG]http://i14.photobucket.com/albums/a315/hotshot66/puppy/newBoxpup-1.jpg[/IMG]

---

