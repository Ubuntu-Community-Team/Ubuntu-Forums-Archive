---
title: "icon for running program on taskbar"
date: 2005-11-03
forum: Desktop Environments
---

### Post by mttolmie on 2005-11-03
My program shows some sort of empty text document and the name of the file it is operating on in the taskbar when running.  I mean the bar in which you click to open and minimize things.
I have created an new mimetype application/squeak and associated it with *.image files and a squeak.desktop pointing at an icon. This icon shows in the file browser for file of type image.
The executable (called squeak) that operates on the image file is located in /usr/local/bin. It shows as mime type application/x-executable. It has some sort of Diamond shaped icon in properties but that is not what shows on the taskbar.
I have searched with Google, i have looked at 20 pages of thiss forum and I am still stuck. Maybe i am using the wrong terminology:)

---

### Post by hajk on 2005-11-03
I'm not quite sure what you're trying to do here... In my own setup I added Squeak to the Applications menu under Programming, using one of those "mousy" icons for visual effect. It is possible to have this icon also appear on the upper bar (right click, Add to Panel). 

You can do all of this with Applications/System Tools/Applications Menu Editor.
Make a new entry under Programming. The crucial line here is the command: /usr/bin/squeak <image-file>, where <image-file> should be the image (with full path) you want to start from the taskbar (in my case it is /home/henk/prog/squeak/henk-univ.image). Then click on the empty icon space, and you'll be presented with a choice of icons, among which is a Squeak icon. After you've done all of this, then you can quit the editor, and you'll see a nice Squeak item on the Applications/Programming menu.

Now for the last bit: right click on the item, and select Add this launcher to panel... that's it! It worked for me.:smile:

Also this: you can always right click on an image (or changes) file, then select Properties and choose an icon for this type of file, same as above.

---

### Post by mttolmie on 2005-11-03
I have a launcher in the panel with a squeak icon, same in applications.

What I do not have is the following: when I minimize a running squeak image, it sits there between an minimized inbox, psi, gFTP and what have you: this minimized squeak image is not represented by a squeak icon but by a file icon and it is hard to recognize that i  already have a squeak running.  It is this icon that I need to change.

---

### Post by hajk on 2005-11-03
I see, when I minimize a running Squeak it moves to the bottom panel and it does have a little "mouse" icon... Have you tried right clicking on the image file in a Nautilus window, then choosing Properties and link the file with Squeak and an accompanying icon?

There is one other thing: you have the squeak binary in /usr/local/bin, so you have probably not installed the deb at ftp.squeak.org? Temporarily add to /etc/apt/sources.list the repository:

deb [ftp://ftp.squeak.org/debian/](ftp://ftp.squeak.org/debian/) unstable main
 
then installing the required squeak packages would set everything up properly...

---

### Post by mttolmie on 2005-11-03
I was unaware of the deb and the repository: I will follow that advice, thanks.

My images came from various places and my vm from the squeak unix website: so no benefit of an official install:(

---

### Post by hajk on 2005-11-03
OK, if you make that change you'll want to save any classes of your own in "file out" form (the files are just text files with .st suffix). After the new install, you can just load these files back into a new image by selecting "open file list'' and highlighting each of these files in turn followed by choosing "install into new changeset'' in the menu under the middle mouse button.

Good luck!

---

