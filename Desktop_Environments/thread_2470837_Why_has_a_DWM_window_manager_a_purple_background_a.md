---
title: "Why has a DWM window manager a purple background and a white cursor?"
date: 2022-01-13
forum: Desktop Environments
---

### Post by undefinednone on 2022-01-13
I just installed DWM by compiling it from the most recent source code from [https://git.suckless.org/dwm](https://git.suckless.org/dwm).
I also setup a ```
/usr/share/xsessions/dwm.desktop
```. That way I was able to select DWM in my Gnome Display Manager.

The problem is that even though I have not changed the default colors my background is now purple and my cursor is white.
How can I get rid of the background and the white cursor? Could gdm be the problem?

For reference I wrote and used this script to install DWM:

```

#!/bin/sh

set -e

# install dependencies
sudo apt update
sudo apt install build-essential libx11-dev libxinerama-dev sharutils libxft-dev

# obtain the source
mkdir -p "$HOME/src"
cd "$HOME/src"
git clone https://git.suckless.org/dwm

# install it
cd dwm
sudo make clean install

# make it visible for the display manager
(cat | sudo tee /usr/share/xsessions/dwm.desktop > /dev/null) << _EOF_
[Desktop Entry]
Name=DWM
Exec=/usr/local/bin/dwm
_EOF_

```

Please help me what causes this weird behavior.

EDIT: I now know that dwm just uses the background image from the display manager which explains the purple background.
However, I still don't know where to change the white cursor.

---

### Post by TheFu on 2022-01-13
Just a guess, but don't use gdm? Look at lightdm.
I use fvwm myself. dwm was just a little too bare for me.
I've looked at the suckless stuff a few times over the years, but never went all-in.

---

### Post by undefinednone on 2022-01-15
Thanks for the suggestion. I had also figured that gdm might not be ideal as it is meant for the DE gnome.

Now I use lightdm with the gtk greeter (I like the way how I can configure it better than the default unity greeter).

The background of both the lightdm display manager and my dwm could be set in the gtk greeter configuration as well as the cursor theme and size.
To keep the cursor theme and size in dwm I also added an [~/.Xresources]("https://github.com/undefined-None/dotfiles/blob/main/xorg/Xresources") file which is loaded by my [~/.xprofile]("https://github.com/undefined-None/dotfiles/blob/main/xorg/xprofile") with xrdb.

My configuration for lightdm and the gtk greeter that solved my issues can be found [here]("https://github.com/undefined-None/dotfiles/tree/main/lightdm") (in case it helps someone to configure his lightdm).

---

### Post by undefinednone on 2022-01-15
> **TheFu said:**
> 
I use fvwm myself. dwm was just a little too bare for me.
I've looked at the suckless stuff a few times over the years, but never went all-in.

I can understand that. I use DWM mostly for programming where I have everything I need and not more.
I just really like tiling window managers.

---

