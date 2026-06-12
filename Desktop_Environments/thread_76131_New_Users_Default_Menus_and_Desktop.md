---
title: "New Users Default Menus and Desktop"
date: 2005-10-14
forum: Desktop Environments
---

### Post by pedrohalbritter on 2005-10-14
Hello, good mornig for all.

I am a studant from a college in Brazil and in our lab we are starting to admin a LTSP network and I am encharged to built it and make it work. Actually the network is fine. And the point I cant move on is that I have to customize the menus and desktop for the new users, we want to previne then to change  the sys configurations and somethings like this. 

[COLOR="Blue"]The point is, I would like to know how to customize desktop and menus and make then as default for new users accounts wen they are created.[/COLOR]

I have found some others admins with exactly the same question of mine in Ubuntu (here) and also in Fedora. I must belive that is not an unsolveble question!! How do the admins to create and manage their user accounts in this way???

I am not in Breezy yet (stil downloading...)  and I use the webmin manager to creat and manage the accounts (due quota and squid, in soon)

Thanks a lot!
Pedro

---

### Post by Alexander Kirillov on 2005-10-14
[QUOTE=pedrohalbritter]Hello, good mornig for all.

I am a studant from a college in Brazil and in our lab we are starting to admin a LTSP network and I am encharged to built it and make it work. Actually the network is fine. And the point I cant move on is that I have to customize the menus and desktop for the new users, we want to previne then to change  the sys configurations and somethings like this. 

[COLOR="Blue"]The point is, I would like to know how to customize desktop and menus and make then as default for new users accounts wen they are created.[/COLOR]

I have found some others admins with exactly the same question of mine in Ubuntu (here) and also in Fedora. I must belive that is not an unsolveble question!! How do the admins to create and manage their user accounts in this way???

I am not in Breezy yet (stil downloading...)  and I use the webmin manager to creat and manage the accounts (due quota and squid, in soon)

Thanks a lot!
Pedro[/QUOTE]

[http://gnome.org/learn/admin-guide/2.6/ch02.html](http://gnome.org/learn/admin-guide/2.6/ch02.html)

---

### Post by Wolki on 2005-10-14
[QUOTE=pedrohalbritter]
[COLOR="Blue"]The point is, I would like to know how to customize desktop and menus and make then as default for new users accounts wen they are created.[/COLOR][/QUOTE]

You can put the configuration files (and directories and stuff) you want each user to have automatically into the /etc/skel directory.

---

### Post by pedrohalbritter on 2005-10-14
Hi Wolki and Alexander, thanks for answering my question.

Wolki, actually I have tried rename the home-directory of a configurated user (with the Semg menu editor) as /etc/skel and it didnt work.... the new user created after that  had the same face as the original skel. Did I make something wrong?

What are the files whose contains these menu informations?

Bytheway, Smeg only edit the first menu? The second and tird ones are more dangerous for unnexperienced users..... can I edit then also?

Alexander I will read carefully the documentation yo gave me, thanks a lot! And as soon as possible I feedback you about it.

Thanks a lot you both! Have a great weekend!
Pedro

---

### Post by SpectralDesign on 2005-10-28
I haven't figured out how to detach Places & Systems from the menu bar -- I have a son who is learning disabled but wants to use the computer so I just removed the entire menu altogether, after I copied some of the game launchers to his desktop.

I also used gconf-editor (inside go to apps -> nautilus for these changes) to take the mounted volumes, trashcan, etc... off the desktop.) so he has a rather safe playground... All I need now is to set the user quota to ensure he doesn't fill up the disk with endless copies of launchers or something :)

- Oh, and I also need to learn how to disable the right-click-on-desktop menu....

---

### Post by mweichert on 2005-11-28
I'm trying interested in this as well... and think that you guys have answered all of my questions, except one. How do I disable the user from shutting down X by using CTRL-ALT-Backspace or from switching to the console using CTRL-ALT-F[123456].

I've found a gconf key that disables the user from using gnome-terminal or the 'run' command from the applications menu, so once I find the answer to this question I'll finally have a handle on all of those bad boys! :D

---

