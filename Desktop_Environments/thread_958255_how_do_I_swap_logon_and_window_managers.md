---
title: "how do I swap logon and window managers?"
date: 2008-10-25
forum: Desktop Environments
---

### Post by ginjabunny on 2008-10-25
I have been having a play on an old laptop (JVC mini note) which is 1GHz cpu and 256MB ram, I have tried a few distros and desktops, I tried Mint XFCE but it was very sluggish, then I tried Fluxbox but didn't like it much, so I started looking around for a something else.

I have decided to use LXDE which is really fast, so I installed a minimal CLI system from 8.04 Alternate CD then installed XDM and LXDE which is great but other things aren't working like the sound (which was working with Mint XFCE) even after recompiling the Alsa drivers.

So my plan is to install full blown 8.04 desktop with GDM/Gnome then install XDM/LXDE and switch over. 
I think I change the Login Manager in "/etc/X11/default-display-manager"  
but I think I must be a bit dim today as I can't find out how to change it so it would start LXDE instead of Gnome, lots of talk of xinitrc but I don't seem to have one?

Any ideas?

---

### Post by celticbhoy on 2008-10-25
why not use ubuntulight it uses LXDE

---

### Post by celticbhoy on 2008-10-25
BTW to do it your way select session from login, LXDE and login when asked make default

---

### Post by ginjabunny on 2008-10-25
cheers for the reply, but I wanted to get rid of GDM as well because it uses a big chuck of ram, also I wanted to keep it proper Ubuntu (less complications) if possible.

I solved it but still don't know how to do it manually, I just used synaptic to install XDM and LXDE and it did it all for me and they are now the defaults, It complained a bit on first run but seemed to sort itself out and everything seems ok now then I changed XDM to remove the logo. So I now have LXDE but still have all the default apps to use if I want, so I might put on some lightweight ones like Abiword, Gnumeric and Gpaint,

System monitor now says it is using 128MB instead of 230MB which leaves lots of room to run stuff.

I would still like to know how I would switch it back to Gnome if I needed to, it must be just editing or replacing a file somewhere, but what?

---

### Post by urukrama on 2008-10-25
If you only have problems with the sound on a command-line install, that might be fixable. The sound might still be muted (it is by default on a command-line install, if I remember correctly). Type "alsamixer" in a terminal and unmute the appropriate channels with the key "M".

If you want to login using Gnome without a session manager such as GDM, you can do so by editing your .xinitrc file. If you don't have a .xinitrc file, you can create one in your home directory. See [here]("https://wiki.ubuntu.com/CustomXSession") for more info.

If you want to use Gnome, a command-line install with gnome-core will also be a lot faster than a full ubuntu install. Xfce4 might be an even better choice.

When you install an additional session manager, it should ask you which one you want to use as default, if I remember correctly. Alternatively, you can use the following command:

> sudo dpkg-reconfigure gdm

(Replace GDM with the session manager you are using.)

Another light session manager is Slim.

---

### Post by ginjabunny on 2008-10-27
thanks for that, so if I create a .initrc file in the user profile I can specify the window manager of choice per user, but I still don't know how you change the system default one?

---

### Post by urukrama on 2008-10-27
The system-wide xinitrc file is as far as I know in /etc/X11/xinit/ (though the man page says it should be found in the /usr/lib/X11/xinit directory).

The man page to xinit (*man xinit*) and startx (*man startx*) might also be useful. They are quite detailed

I am not sure, though, why you need the system-wide xinitrc file. Why don't you use the ~/.xinitrc file?

---

