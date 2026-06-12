---
title: "How to change command behind an icon in the launch bar?"
date: 2013-09-27
forum: Desktop Environments
---

### Post by Bao_Niu on 2013-09-27
Currently I have an icon sitting in my launch bar, with corresponding command:
[COLOR=#0000cd]Dia
[/COLOR]
I want to change the launching command to:
[COLOR=#0000cd]LIBOVERLAY_SCROLLBAR=0 dia[/COLOR]

and preserve the icon.
so each time when I click on the same icon it will launch Dia with the new command.
Is it possible to do this? And how? Many thanks.

---

### Post by deadflowr on 2013-09-27
If it's a regular application you can:
first open gedit.
Then, for ease of use, open the file manager and then
go to the folder /usr/share/applications
Find the application, and then drag it into the gedit window.
Edit the command line "Exec="

At this point, I also add something like My in front of the program name
"Name=My Program"
Then open the file menu option and go to save as(not save)
And save the file in /home/username/.local/share/applications.

Then open the dash and search for the program.
When found, add it to the launcher and it should stay there, regardless of what happens from then on.

---

### Post by Bucky Ball on 2013-09-27
Right click launch bar>Add New Item>Launcher>set up your launcher with a name, an icon pic if you want one, and command.

Test it. Delete the old icon with 'dia' as the command.

---

### Post by mc4man on 2013-09-27
Locate the .desktop associated with Dia, open in a text editor, (root if  in below address). Find the Exec= line & edit to - 
```
Exec=env LIBOVERLAY_SCROLLBAR=0 dia %F
```
May need to log out/in to affect  in launcher

Likely will be found in /usr/share/applications/dia.desktop

---

