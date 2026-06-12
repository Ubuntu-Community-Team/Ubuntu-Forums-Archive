---
title: "Show apps icons management"
date: 2020-09-14
forum: Desktop Environments
---

### Post by HC48 on 2020-09-14
Hello, I know this has already been treated in this forum but the thread is closed and I need more information. the title of the thread is: Add/Delete (manage) icons from show apps
I am not experienced enough to fully understand the advice given and not good with the terminal so please bear with me.:)

The initial question was : **So, anyone knows how to manage those icons from "show apps" ?** when uninstalled apps icons remain in the show apps launcher. 
I have the same problem ie. I have unwanted icons on the show apps launcher and can't get rid of them. They are apps installed with wine, when I uninstalled and reinstalled Adobe Digital Editions I got extra icons when I was testing different versions so have several of the same app. I have two icons for discord and 2 for ADE DRM removal app. I used play on linux for ADE and the logitech store for discord. When discord occasionally offers to update a new version on opening I don't know how to so I uninstall and reinstall with the logitech store which works fine.

We are told:

"If it behaves like Wine on my XUbuntu 18.04, then it creates  .desktop-files in ~/.local/share/applications/wine/Programs when a  Windows setup program makes the calls to create a menu-item in Windows.  Deleting or moving them outside ~/.local/share/applications should  remove them. Alternatively you could open the ones you don't want in an  editor and add a line saying 'Hidden=yes' or 'NotShowIn=Gnome'."

I'm afraid I don't understand how to do any of this.

How do I get to " **.desktop-files in ~/.local/share/applications/wine/Programs** ", in the folders manager or in a terminal?

Which editor do I use for the second method :'** Alternatively you could open the ones you don't want in an  editor and add a line saying 'Hidden=yes' or 'NotShowIn=Gnome'.**" ?( I think this way would be easier for me...)

Would this work in ubuntu 18.04?

This is not a serious problem in itself but I am curious to have a solution.
Thank you.

---

### Post by webaake on 2020-09-14
I do wine and 18.04 too, but I do not have any files in ~/.local/share/applications/wine/Programs. What you can do is to search for for the relevant *.desktop files iin the terminal like so:

locate *.desktop

There might be many files, some might even be in /usr/share/applications and/or in /home/"Your_user"/.local/share/applications/ (Change "your_user to your actual user name)

All files in   /usr/share/applications can only be removed or edited with admin rights. The editor from terminal is called nano. So, to edit *.dektop files in your home dir type:

nano /home/"Your_user"/.local/share/applications/the_relevant_file.desktop

To study and learn more type from terminal:

man nano

which will show all commands within the ditor nano. nano is a very useful tool in the Linux world, and it can accomplish more than most graphical editors more effectively.

Learn more about the "desktop"-file specs and syntax.

Have fun learning! :) :)
[https://specifications.freedesktop.org/desktop-entry-spec/latest/index.html](https://specifications.freedesktop.org/desktop-entry-spec/latest/index.html)

---

### Post by HC48 on 2020-09-14
Thank you weebaake. I will look into this. have a nice day. :)

---

