---
title: "Emacs in separate window - jaunty server"
date: 2009-05-01
forum: General Help
---

### Post by yasheshb on 2009-05-01
hello.

  i just did a fresh install of amd64 ubuntu jaunty server (from the dvd) and installed emacs from the dvd using the synaptic package manager.

  to invoke emacs i use

$ emacs 
in the terminal window and this brings up emacs in the terminal window itself. in my earlier distributions (FC6) i used to get emacs in a separate window. any quick fix ?

thx a bunch.

yashesh

---

### Post by yasheshb on 2009-05-01
did some more debugging..

on the menu

"Applications - Accessories - Emacs 22 (client) "

it invokes the following command

"/usr/bin/emacsclient.emacs22 -a emacs22"

i tried the same on the bash shell terminal

root@bfc33:/usr/bin# /usr/bin/emacsclient.emacs22 -a emacs22
/usr/bin/emacsclient.emacs22: file name or argument required
Try `/usr/bin/emacsclient.emacs22 --help' for more information
root@bfc33:/usr/bin# 


this is strange since the installation created the shortcut wrongly it seems.. anyone see this before ?

thx.


yashesh

---

### Post by yasheshb on 2009-05-04
[FONT=Arial][SIZE=1]did some more debugging (before that i did a fresh install since i had installed the nvidia accelerated drivers 180 to get the resolution to 1440x900).

i reinstalled jaunty server amd 64. did not install nvidia drivers and running on a basic 800 x 600 resolution.

i then installed only Emacs (via the synaptic package manager). it again created a menu item Emacs 22 (client). 

i then tried to invoke both emacs from the terminal

$ emacs

and from the menu - Applications - Accessories - Emacs 22 (client)

the one in command line brings up emacs in the terminal instead of a seperate window and the one
from menu has no response.

i did some more reading - 
[http://www.linuxselfhelp.com/HOWTO/XWindow-User-HOWTO-4.html](http://www.linuxselfhelp.com/HOWTO/XWindow-User-HOWTO-4.html)
[http://linux.about.com/od/emacs_doc/a/emacsdoc119.htm](http://linux.about.com/od/emacs_doc/a/emacsdoc119.htm)
[http://riddell.us/tutorial/emacs/emacs.html](http://riddell.us/tutorial/emacs/emacs.html)

and it looks like i have to install emacs-snapshot-gtk[FONT=monospace] ?

thoughts ? help ? feedback ? this is really tough behaviour on the emacs install since this is the only s/w installed after a 2 hour reinstall and that also breaks down. Maybe a bug in the emacs on the dvd image ?

thx and appreciate any help.

yashesh



[/FONT][/SIZE][/FONT]

---

### Post by yasheshb on 2009-05-07
fixed 

i uninstalled emacs and then installed emacs GTK and it works fine. there are a bunch of emacs in my system though

```

root@bfc33:/usr/bin# ls -l /usr/bin/emacs*
lrwxrwxrwx 1 root root      23 2009-05-05 16:11 /usr/bin/emacs -> /etc/alternatives/emacs
lrwxrwxrwx 1 root root      25 2009-05-05 16:11 /usr/bin/emacs22 -> /etc/alternatives/emacs22
-rwxr-xr-x 1 root root 8996768 2008-09-06 03:18 /usr/bin/emacs22-gtk
lrwxrwxrwx 1 root root      29 2009-05-05 16:11 /usr/bin/emacsclient -> /etc/alternatives/emacsclient
-rwxr-xr-x 1 root root   19104 2008-09-06 03:18 /usr/bin/emacsclient.emacs22
root@bfc33:/usr/bin# 

```

somehow it works but this is not a clean emacs install on ubuntu for sure.

---

