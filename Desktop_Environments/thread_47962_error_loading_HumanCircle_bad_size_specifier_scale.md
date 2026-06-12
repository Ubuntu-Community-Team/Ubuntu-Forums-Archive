---
title: "error loading HumanCircle bad size specifier scale"
date: 2005-07-10
forum: Desktop Environments
---

### Post by brian g on 2005-07-10
when gnome loads, i get the error "error loading HumanCircle bad size specifier scale".
it's a diolog box and i click OK or some such.
then it continues to load gnomes default login screen with no mouse support and i have no way to get the cursor to the User field. 

i've read in [another thread](http://ubuntuforums.org/showthread.php?t=25413)  that i need to *sudo apt-get install xfce4* 
whatever that is..

how can i get to a command line to *sudo apt-get install xfce4* if gnome is basicly unresponsive?
is there a way to start my computer to a command line without is starting gnome?
then i could just *sudo apt-get install xfce4* right?

basicly i just want to get my computer back to the way it was before i started getting this error.

brian g
total linux noob coming to you live from knopix..  ](*,)

---

### Post by crashtest on 2005-07-10
[QUOTE=brian g]when gnome loads, i get the error "error loading HumanCircle bad size specifier scale".
it's a diolog box and i click OK or some such.
then it continues to load gnomes default login screen with no mouse support and i have no way to get the cursor to the User field. 

i've read in [another thread](http://ubuntuforums.org/showthread.php?t=25413)  that i need to *sudo apt-get install xfce4* 
whatever that is..

how can i get to a command line to *sudo apt-get install xfce4* if gnome is basicly unresponsive?
is there a way to start my computer to a command line without is starting gnome?
then i could just *sudo apt-get install xfce4* right?

basicly i just want to get my computer back to the way it was before i started getting this error.

brian g
total linux noob coming to you live from knopix..  ](*,)[/QUOTE]

Press Ctrl-Alt-F1 to open a text mode login screen.  Actually, ctrl-alt-F1 thru F6 will open text screens, ctrl-alt-f7 will return you to your graphical screen.

---

### Post by brian g on 2005-07-11
[QUOTE=crashtest]Press Ctrl-Alt-F1 to open a text mode login screen.  Actually, ctrl-alt-F1 thru F6 will open text screens, ctrl-alt-f7 will return you to your graphical screen.[/QUOTE]
ctrl+alt+F1 F2 F3 etc don't work at the login screen
i can only get to the sessions menu and the menu that gives me the option to restart, shut down, etc... via keyboard commands.

what do i do once i DO get to a command prompt?
how do i fix the problem?

---

### Post by brian g on 2005-07-11
ok i did get ctrl+alt+F1, F2...
but when i went to sudo apt-get install xfce4 it couldn't get the files it needed 
it built some branch thing but couldn't download the required packages or something like that.

i tried to ping my website and it wouldn't ping.
so i'm assuming that the network junk hasn't loaded.

now what do i do?


i should just reinstall ubuntu but i have my pgp (gpg?) stuff set up and i dont want to revoke my key and create a new one. and i have no idea how to back that stuff up. 

 :roll:

---

### Post by troublemaker on 2005-10-14
From another Ubunto form (and in another language) comes this solution
> 
Goes on a console (appuyes on [ Ctrl]-[Alt]-[F1 ] for example) and replaces the line
Code:

 GtkTheme=Human

by the name of another theme being in the repertory/usr/share/gdm/themes ("HumanCircle "for example) in the file"/etc/gdm/gdm.conf "with a text editor (nano, vim, etc) and revivals gdm with this order:
Code:

 sudo/etc/init.d/gdm restart

.


---

