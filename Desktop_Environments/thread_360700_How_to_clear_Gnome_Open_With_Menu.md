---
title: "How to clear Gnome Open With Menu"
date: 2007-02-13
forum: Desktop Environments
---

### Post by kdawg on 2007-02-13
I recently uninstalled a lot of applications and they still show up in the "Open with" menu in Nautilus.  How do I reset the list?

---

### Post by balloons on 2007-03-10
Right click on the file, select  properties. Click the open with tab. Add and remove as desired

---

### Post by emgator on 2007-03-26
I tried this, but the remove button is greyed-out... any other ideas?

Thanks!

---

### Post by kdawg on 2007-03-26
Yeah that works if you want to remove a link to a program that actually can open that file.  My problem is that I uninstalled a lot of programs, and I have no files that are associated with thhose programs anymore, so now I want the entries out of the list.  There must be a file somewhere with the entries in it that I can edit and delete.

An example I can think of would be that I run Ubuntu and installed Kubuntu-desktop.  Then after uninstalling kubuntu, the the open with dialog still has kubuntu programs listed in it that do not exist anymore, I want them gone.  Thanks!!

---

### Post by ComplexNumber on 2007-03-26
i suspect that those applications that can't be removed are in this directory, and are associated with various mime types:
**/usr/share/applications**

each of those applications in that directory is associated with a particular mime-type. for example, gnochm(a chm file reader) is associated with the chm file type. 
you will also notice that those file types that are associated with applications in the above directory cannot be removed by simply removing from the 'properties' -> 'Open With' tab.
if you have a look at the contents of each of the files in the above directory, you can see what mimetypes they are associated with.


another example is gl-chess. this is the contents of gl-chess in the above directory:
```
 [Desktop Entry]
Encoding=UTF-8
Type=Application
Name=glChess
GenericName=3D Chess Game
GenericName[pt_BR]=Jogo de Xadrez 3D
GenericName[de]=3D Schach
Icon=glchess
Exec=glchess
Terminal=false
Categories=Application;Game;BoardGame;
** MimeType=application/x-chess-pgn**;
```you can see that its associated with pgn files, and the association won't be able to be removed from the  Open With tab by simply choosing to delete it.

i would sugest that to remove the association with a particular application, go to the above directory and find the application that you wish to remove. then edit that file to remove the mime type association. for  example, if you wish to remove 'Exaile' from the Open With for mp3 files, go and find Exaile in the above directory, and remove "mp3" from the list of Mimetypes in that file.

---

### Post by emgator on 2007-03-26
Thanks, ComplexNumber!

I uninstalled DemocracyTV, but it had left its shell integration intact. I deleted the file "democracyplayer.desktop" from /usr/share/applications/ and that cured the problem.

---

### Post by kdawg on 2007-03-28
Thanks!! Works great for me as well, except for one thing......

The open with menu still has some entries in it from programs that I have installed with wine and later uninstalled, these do not  have a .desktop entry in /usr/share/applications, and the files do not exist anymore in my ~/.wine directory (I removed wine and deleted the ~/.wine folder and all of its contents), so where is it getting the data from and how do I get rid of it?

---

### Post by tho on 2007-03-28
> **kdawg said:**
> Thanks!! Works great for me as well, except for one thing......

The open with menu still has some entries in it from programs that I have installed with wine and later uninstalled, these do not  have a .desktop entry in /usr/share/applications, and the files do not exist anymore in my ~/.wine directory (I removed wine and deleted the ~/.wine folder and all of its contents), so where is it getting the data from and how do I get rid of it?

Not sure where they are stored, but try 'find $HOME -name *.desktop'. That should give a clue as to where they are hiding.

---

