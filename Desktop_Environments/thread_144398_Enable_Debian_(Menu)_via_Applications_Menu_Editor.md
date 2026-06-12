---
title: "Enable Debian (Menu) via Applications Menu Editor"
date: 2006-03-14
forum: Desktop Environments
---

### Post by justaguynpc on 2006-03-14
I am confused ...................

After a clean Breezy install, I am unable to enable Debian via the (Smeg) Applications Menu Editor.  The option looks to be available, however, I am unable to engage the option by placing a check-mark in the box preceding it.

During my last install, presumably after experimenting with many desktop window managers, I found "debian" residing on my Applications menu.  I believe it may have been a "artifact", but it was something that I miss at this point.

After extensive search, I have found no resolution.  I have in the meantime installed menu / menuxdg / pdmenu via synaptic without result.  

Any suggestions?[ATTACH]7049[/ATTACH]

Many Thanks!  :confused

---

### Post by jobezone on 2006-03-14
Install the packages **menu-xdg** and **menu** and it should appear.
EDIT:Nevermind, you did that already! I don't know...

Have you tried running the update-menus command?
And does running pdmenu in the console show the debian menu (in the console)?

---

### Post by justaguynpc on 2006-03-14
[QUOTE=jobezone]Install the packages **menu-xdg** and **menu** and it should appear.
EDIT:Nevermind, you did that already! I don't know...

Have you tried running the update-menus command?
And does running pdmenu in the console show the debian menu (in the console)?[/QUOTE]
Ran update-menu ----- no love
Ran pdmenu via console, it had no bearing on enabling Debian menu.

Debian, when correctly enabled on Applications, results in a sub-menu with applications I am sure are default in the ubuntu install.  This "sub-menu" lists applications not found in the existing applications menu.

Thanks for trying though, appreciate it!

justaguy

---

### Post by justaguynpc on 2006-03-14
I guess I should add that the applications menu editor works normally for any other additions.

justaguy

---

### Post by jobezone on 2006-03-14
1 - I forgot to say, but the exact command should be done using sudo, such as:
```
sudo update-menus
```
2 - And what do you mean that the pdmenu menu had "no bearing on enabling Debian menu"? Is it empty (pdmenu menu)? Or is pdmenu fully populated with application entries? Anyway, even if it is, it doesn't solve the problem of you not having the Debian menu on your aplications menu.

3 - Have you tried creating a new user, log in as that user, and see if the debian menu appears with that user?

4 - If so, that means it's a problem with only your own user. You could be drastic, and delete your complete gnome configuration (by deleting the hidden directories .gnome .gnome2 .gconf and .gconfd in your home directory)

5 - Before trying to install the debian menu, did you use the menu editor? If so, it could be a bug of the editor ubuntu uses, perhaps.

---

### Post by justaguynpc on 2006-03-15
pdmenu: (via command line) gave me a Main Menu which included the following options: (in the CLI)

                       Debian Menus...
                       Change your password
                       Directory listing
                       Change directory
                       Whose online?

                        Exit

Otherwise, nothing has changed in my application menu to furthur my quest for a Debian option.  Are you familiar with the Debian menu, and it's cooresponding submenu of applications which resides on the application menu?

No, I have not created a new user, mainly because I am not that familiar with the most efficient method  removing all the residual files I may be left with when I remove that user from my system.  I guess I will have to investigate the ease of removing this temporary user.

No, I am not going down the road delete my gnome config, I guess it boils down to the fact that this simple addition of the Debian menu isn't THAT important!  :)

I guess I have to continue my investigation.  I am still not sure if I am expressing myself clearly enough about this whole issue. I do recall it was pinned to the installation of one of the other window managers I was experimenting with.  I guess I will start there.

Should you ran across anything .............. please feel free to pass it on, it would be appreciated.

Thanks again jobezone

justaguy

---

