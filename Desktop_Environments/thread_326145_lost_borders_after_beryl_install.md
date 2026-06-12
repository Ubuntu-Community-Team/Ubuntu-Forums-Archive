---
title: "lost borders after beryl install"
date: 2006-12-27
forum: Desktop Environments
---

### Post by STREETURCHINE on 2006-12-27
hi .merry xmas all.
i installed beryl on to my edgy 6.10 today it seems to be working ecept for the loss of the borders around all the windows.
i opened terminall and was going to type metacity(this works in dapper dont know about edgy but worth a try)
but i cant even type in terminal,the page shows up but no rex@rex-desktop ~$ 
and no flashing black square thingie


resolved this problem reinstalled edgy 6.10,that fixes the little blighter
 (tried to fix on my own but broke xserver so that was it):confused:

---

### Post by pandu.rs on 2006-12-27
install compiz-themer if u dont have it already,

open compiz themer then select 'Edit' at the bottom the window, then goto 'Shadows/Titlebar' tab and then select of the two choices for 'titlebar object layout' option.

you shld get ur titlebars now (i dont remember if a restart of X was required)..

---

### Post by STREETURCHINE on 2006-12-28
when i start beryl from terminal it say's that i have no xgl ,i thought i installed it but obviously not.
now i cant seem to bew able to connect to the repository that alows me to down load the xserver xgl
 i have the emerald theme manager so i dont need the compiz theme manager do I ?

 still have no borders ,but i have a transparent cube,i  have flames working ,and teleport when i maximize pages again.
still cant use terminal when beryl is running?

---

### Post by STREETURCHINE on 2006-12-29
<=shamless bump+>

---

### Post by psycho78 on 2006-12-29
i have the same problem, but starting beryl with  sudo beryl in gnome-terminal helps.... so this must be a problem with access rights????:-k

---

### Post by psycho78 on 2006-12-29
> i have the same problem, but starting beryl with sudo beryl in gnome-terminal helps.... so this must be a problem with access rights????:-k

Does nobody have an idea what could be the matter? Why do I have to sudo beryl... it worked before without sudo, all I did was updating regularly with these repos: 
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb [http://beryl.limitless.lupine.me.uk](http://beryl.limitless.lupine.me.uk) edgy main
with manually installed nvidia driver ..... there seem to be several installations where these things happen... searching through the forum I found many tips but no solution yet...
I wonder if it is dangerous to start beryl with sudo rights?

---

### Post by STREETURCHINE on 2006-12-29
yes i can start it with terminal from here but as soon as i start beryl i can no longer use terminal.

---

### Post by psycho78 on 2006-12-30
Have you tried to start beryl with these options?:
beryl --use-cow -- --force-aiglx
I am diggin' in the dark .... yesterday I tried opensuse just for fun... it was much easier to setup "Desktop Effekts..."  simply putting the nvidia repositories to yast, install the drivers, restart X and you're set.... 
I wish this would be this easy in ubuntu, because I don't have the intention to switch to another distribution only because of these eyecandy things... :)

---

### Post by OokieWonderslug on 2007-02-28
When I try to run beryl I get this message:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x4b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

libGL warning: 3D driver claims to not support visual 0x4b
Reloading options

And lose the titlebar and access to my other desktops. Any idea what's going on?
I'm using Kubuntu 6.10 and have the Intel i8xx video.

---

