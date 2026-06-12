---
title: "login background colour"
date: 2013-01-19
forum: Desktop Environments
---

### Post by Pletched on 2013-01-19
Similar to this thread ([http://ubuntuforums.org/showthread.php?t=1871801](http://ubuntuforums.org/showthread.php?t=1871801)) is there a variable to change to a solid colour as opposed to changing to another wallpaper.

present 
```
## background of the greeter
bg=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png


```
to something like```
bg=
bgc=rgb(255,255,255)
```

---

### Post by Petro Dawg on 2013-01-19
you could just link to a solid color .png file

---

### Post by Pletched on 2013-01-19
I suppose I could. I should have made it clear. I don't want to use a wallpaper file unless it's absolutely necessary. 

Sorry about that.

---

### Post by Pletched on 2013-01-19
I decided to go with a file, but it's not changing.

Here's my default.conf.
```
[base]
## uncomment and set autologin username to enable autologin
# autologin=dgod

## uncomment and set timeout to enable timeout autologin,
## the value should >=5
# timeout=10

## default session or desktop used when no systemwide config
session=/usr/bin/startlubuntu

## uncomment and set to set numlock on your keyboard
# numlock=0

## set this if you don't want to put xauth file at ~/.Xauthority
# xauth_path=/tmp

## greeter used to welcome the user
greeter=/usr/lib/lxdm/lxdm-greeter-gtk

[server]
## arg used to start xserver, not fully function
# arg=/usr/bin/X -background vt1

[display]
## gtk theme used by greeter
gtk_theme=Clearlooks

## background of the greeter
#bg=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png
bg=/home/pletch/.config/login.png

## if show bottom pane
bottom_pane=1

## if show language select control
lang=1

## if show keyboard layout select control
keyboard=0

## the theme of greeter
theme=Lubuntu

[input]

[userlist]
## if disable the user list control at greeter
disable=0

## whitelist user
white=

## blacklist user
black=


```

---

### Post by Pletched on 2013-01-19
From this thread ([http://ubuntuforums.org/showthread.php?t=2085657](http://ubuntuforums.org/showthread.php?t=2085657)) I found out that the file I'm searching for is in a different place. Which is here /etc/lightdm/lightdm-gtk-greeter.conf.

I can pick a colour via html-hex notation (I don't know the name for it) e.g. #ffffff, but the file I'm using will not show; lightdm will show black background.

---

