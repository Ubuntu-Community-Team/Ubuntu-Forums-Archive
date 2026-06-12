---
title: "xrdp and Gnome Session"
date: 2020-11-12
forum: Desktop Environments
---

### Post by giobaxx on 2020-11-12
I'm trying to configure an xrdp connection and just to have an user experience more similar possible to the local session i'm following this post:

[https://askubuntu.com/questions/1233088/xrdp-desktop-looks-different-when-connecting-remotely](https://askubuntu.com/questions/1233088/xrdp-desktop-looks-different-when-connecting-remotely)

that says to add these lines

> [I][B]cat <<EOF > ~/.xsessionrc
 echo export GNOME_SHELL_SESSION_MODE=ubuntu
export XDG_CURRENT_DESKTOP=ubuntu:GNOME
export XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/etc/xdg
 EOF[/B][/I]

at the top of the files : [B][I]/etc/xrdp/startwm.sh

[/I][/B][COLOR=#242729][FONT=Arial]This will create a file called *.xsessionrc*. This file is kind of login script will load your desktop configuration into the remote session.[/FONT][/COLOR]
In this post there is the link to the full guide that is really good : [http://c-nergy.be/blog/?p=14093](http://c-nergy.be/blog/?p=14093)

It is a very good but i don't why sometimes it does not work. If i add to a complete new systems it works, but if i try to add these lines by a copy and paste to a system that is already in production, where i tried a different configuration sometimes it does not work.

In the old configuration i added these lines:

> 
[LIST=1]
[*]***echo 'gnome-session' > ~/.xsession***
[*]***chmod +x ~/.xsession***
[/LIST]


in same file :[B][I]/etc/xrdp/startwm.sh
[/I][/B]
And i'm not able to understand how it works.  It thought that after the first remote login,it create a configuration that cannot be changed? there a way to reset?

This because same ***startwm.sh , ***copied with scp works in a Computer and not to another one.

I'm Confused

A.

---

### Post by ActionParsnip on 2020-11-12
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)
Could use VNC. If it's over the Web then use the SSH tunnel as stated.

---

### Post by giobaxx on 2020-11-13
Thanks for you reply, but unfortunately we are forced to try to use xrdp to get remote Connection from a Windows Client. And basically it works, at least most of the time.

Sometimes, the modification to the ***startwm.sh*** are not applied and i really don't know why!! i've checked file permission, owner...but nothing.

Maybe the method copy and past leave some strange character that made this line not readble by the system? From what i have understood this should  happend  when the  ***startwm.sh ***is not able to create the .xsessionrc on the home of the user, but why?

I really don't know.

A.

I really don't know.

---

### Post by ActionParsnip on 2020-11-13
Could try a sleep command in the startwm.sh command to let the system get settled, just a second or so may help

---

