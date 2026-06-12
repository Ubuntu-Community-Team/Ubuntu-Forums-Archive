---
title: "file association"
date: 2006-01-28
forum: Desktop Environments
---

### Post by pabs on 2006-01-28
This seems like it would be a fairly common questions but I am having a hell of a time finding any information on it.  

How can I can file associations in GNOME?  For instance, open all *.mpg with vlc?  Please excuse the noobiness :mad:

---

### Post by Who on 2006-01-28
Hi,
I'm not on Ubuntu now so I can't give you the exact name but it is in System-->Preferences and it is something like "File types and Programs" ....

Hope that is right!

Who

---

### Post by jrib on 2006-01-28
[QUOTE=pabs]This seems like it would be a fairly common questions but I am having a hell of a time finding any information on it.  

How can I can file associations in GNOME?  For instance, open all *.mpg with vlc?  Please excuse the noobiness :mad:[/QUOTE]

right click on a file > properties > open with

---

### Post by pabs on 2006-01-28
I know about right click and open with.  I should have clarified.  I want to be able to double-click on a movie file to open with vlc (instead of totem).  So I want to change the default player in this case.  

(If there is a text config file that deals with this, it would be a bonus to know that  :D )

---

### Post by jrib on 2006-01-28
[QUOTE=pabs]I know about right click and open with.  I should have clarified.  I want to be able to double-click on a movie file to open with vlc (instead of totem).  So I want to change the default player in this case.  

(If there is a text config file that deals with this, it would be a bonus to know that  :D )[/QUOTE]

right click > [COLOR="black"]_[SIZE="7"]PROPERTIES[/SIZE]_[/COLOR] > open with :)

[edit] If you really want to know about the text files that control it, the associations are controlled by .desktop files iirc.  That may get you started on a google search.  I don't know the details or I'd tell you more

---

### Post by pabs on 2006-01-30
thanks!  I'll look into .desktop files.  :)

---

### Post by JensKue on 2006-02-13
Wow ... took me ages now to locate this simple piece of information ...

I guess, next time I will look into the file properties first when looking for anything. But there should be something like "File associations" in "System/Preferences" as well for all the noobs like me out there :-k

---

### Post by Mikecore on 2006-02-13
This is not windows so we don't need that. You just need to spend a little time learning your new OS. ;)

---

### Post by engine on 2006-03-04
No-one's saying "make Ubuntu more like something else". It doesn't matter what system it is: when there are references in the on-line Help to a File Types and Programs preference tool, that tool should exist and be easy to find under, well, System > Preferences.

Right-click doesn't get me anywhere with my particular take on this problem, either: first thing it does (in Nautilus) is change the icon and assign a new mime-type. I was hoping the mythical Preference tool would let me set up an association, either on the basis of an extension or by reading - for example - the header line that defines the syntax type for vim.

I'll post that as a question rather than an observation, though.

---

### Post by DavidW2 on 2006-03-04
To change the default application of a filetype do this.

Open Nautilus and go to a directory with the filetype you want to associate.
Right-click on the file and select Properties, then go to the "Open With" tab and set your application.  If it is not there you can add it.  Which ever radio button is clicked is the default.

---

### Post by gsanse on 2006-03-26
I am having an issue with file association. I was using Acrobat Reader to open .pdf files. I decided to try evince for a while and used the procedure above to change the association. It worked fine. However, after a while, I decided I want to use Acrobat Reader again. This is where the problem starts. When I go to the  Open With Tab in the file properties dialog, I just cannot select any other application. Evince is there and so is Acrobat Reader, but I just cannot select Acrobat. Is anyone facing a similar problem?

---

### Post by DavidW2 on 2006-03-29
Are you clicking on the application name or the circle in front of the app?  You should click on the circle.

---

### Post by aysiu on 2006-03-29
[QUOTE=gsanse]When I go to the  Open With Tab in the file properties dialog, I just cannot select any other application. Evince is there and so is Acrobat Reader, but I just cannot select Acrobat. Is anyone facing a similar problem?[/QUOTE] Screenshot of this, please?

---

### Post by zek725 on 2007-09-29
> **DavidW2 said:**
> To change the default application of a filetype do this.

Open Nautilus and go to a directory with the filetype you want to associate.
Right-click on the file and select Properties, then go to the "Open With" tab and set your application.  If it is not there you can add it.  Which ever radio button is clicked is the default.

How do you remove the file association to a program? I had .exe open with WINE automatically and considering the security risk to that, I wish to strip off its automatic loading with WINE.

---

### Post by Wolki on 2007-09-29
> **zek725 said:**
> How do you remove the file association to a program? I had .exe open with WINE automatically and considering the security risk to that, I wish to strip off its automatic loading with WINE.

Take a look at the file "~/.local/share/applications/defaults.list". Do you have an entry for x-executable or something similar? Delete that line and save the file again.

This might not be enough, if not, see whether there's a file called wine.desktop or similar in ~/.local/share/applications/ and if yes, remove it (or move it to a backup folder). It might be best to check this from a terminal since nautilus treats .desktop files differently from other files and shows their title in your language instead of the file name.

---

