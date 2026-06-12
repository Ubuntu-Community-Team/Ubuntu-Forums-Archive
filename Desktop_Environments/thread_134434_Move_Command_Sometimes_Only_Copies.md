---
title: "Move Command Sometimes Only Copies"
date: 2006-02-21
forum: Desktop Environments
---

### Post by pablofanques on 2006-02-21
Trying to move files/directories from a USB hard drive to an internal hard drive.  Sometimes cutting and pasting directories from the USB drive onto the internal drive works as it should.  Other times the directories are only copied (a copy gets left behind on the USB drive)  

  I tried changing permissions on the directories being moved (enabled read, write, and execute for the owner)  No dice.  

Appreciate any help.

---

### Post by taurus on 2006-02-21
Why not do it from a terminal instead of the cutting and pasting...

mv -R /media/usb/* ~/temp/

---

### Post by pablofanques on 2006-02-21
[QUOTE=taurus]Why not do it from a terminal instead of the cutting and pasting...

mv -R /media/usb/* ~/temp/[/QUOTE]

Tried it from the terminal. Got many [COLOR="Red"]cannot overwrite directory[/COLOR] errors.  Tried [COLOR="DarkGreen"]mv -f ...[/COLOR] to force it; with same errors.  Tried [COLOR="DarkGreen"]mv -R ...[/COLOR] and still got errors.  I am moving the files one by one* in Nautilus because it's kind of urgent.

* for some reason *this* works.

---

### Post by taurus on 2006-02-22
Who is the owner of those files/directories?  If root is the owner, then a regular user cannot move them without permission, sudo!!!  ;)

---

### Post by pablofanques on 2006-02-22
[QUOTE=taurus]Who is the owner of those files/directories?  If root is the owner, then a regular user cannot move them without permission, sudo!!!  ;)[/QUOTE]

I think permissions might be the culprit.  When I right-click Properties and go to the Permissions tab I think that only effects the directory I right-clicked on.  Is there any way to apply ownership rules to all subdirectories/files in GNOME?  Alternatively, there any way to sudo without going through the terminal?

---

### Post by kaamos on 2006-02-22
"sudo nautilus" gets you a file manager as root.

---

### Post by pablofanques on 2006-02-22
I tried all of the following

[COLOR="DarkGreen"]chmod -R 777 my\ docs/

chmod -R u=rwx my\ docs/

sudo chmod -R u=rwx my\ docs/

sudo chmod -R 777[/COLOR]

I'm still attempting the actual moving through GNOME.  I noticed that the "moving" files" dialog disappears before it gets past the halfway mark.  I suspect that some kind of error is occuring but there isn't any error dialog popping up.  Is it possible that error displaying is switched off somewhere? *Sigh* I never thought moving files would be a such a mission...

---

### Post by taurus on 2006-02-22
You can change all the permissions you want but as long as you are not the owner of those files/directories, you cannot move them except coyping them!    So, change the owner first and then move them...

chown -R <UserID> "my docs"

---

### Post by pablofanques on 2006-02-23
[QUOTE=taurus]You can change all the permissions you want but as long as you are not the owner of those files/directories, you cannot move them except coyping them!    So, change the owner first and then move them...

chown -R <UserID> "my docs"[/QUOTE]


Tried [COLOR="SeaGreen"]chown -R[/COLOR] and followed it with [COLOR="SeaGreen"]chmod -R 777[/COLOR] without success.  

I don't get this.  I'm trying to move a directory on the USB drive called "School" onto the internal drive.  If I cut and paste then a copy the directory and all subdirectories and subfiles gets left behind on the USB drive.  On the other hand, If I create a copy of "School" on the USB drive and move the copy, that works as it should.  I'm even able to delete "School"  

How can I have the permission to delete a directory but not to move it?  Isn't move just a compound operation (copy+delete)?

Appreciate the help, taurus

---

### Post by pablofanques on 2006-02-24
In the process of trying to solve my problem I have made a minor discovery.  I created a directory called [COLOR="DarkGreen"]temp[/COLOR] and in it I place a file called [COLOR="DarkGreen"]file#[/COLOR].  I then created another directory called [COLOR="DarkGreen"]temp[/COLOR] somewhere else with a file called [COLOR="DarkGreen"]file#[/COLOR] in it as well.  When I try to move one temp directory to the other in GNOME or via the terminal, I receive no error, but the move does not take place.  When I remove the [COLOR="DarkGreen"]#[/COLOR] from [COLOR="DarkGreen"]file#[/COLOR] the move works perfectly.

The conclusion I draw from this is that if you have a directory which contains a file with a # in the filename and you try to overwrite another directory of the same name which also contains a file with a # in the filename then the move operation doesn't work.

---

