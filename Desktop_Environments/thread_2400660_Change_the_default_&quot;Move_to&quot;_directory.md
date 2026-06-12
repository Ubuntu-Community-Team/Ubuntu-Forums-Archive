---
title: "Change the default &quot;Move to&quot; directory"
date: 2018-09-08
forum: Desktop Environments
---

### Post by ov10fac on 2018-09-08
When using the GUI desktop and trying to move a file to a new folder (right click the file and select move to) I get an error that says the folder does not exist.  How can I change the default folder that Nautilus is looking for when I select "move to".

Thanks.

---

### Post by #&amp;thj^% on 2018-09-08
When I use a GUI for moving a File or even a Folder, I just simply click once on that particular file, then hold the mouse button down and then I use the shift Key and Drag the file/folder to where I want it.
I do know this is not what you asked for but offering as a suggestion.
Most of the time (80%) for my use I just use the terminal to "mv" "cp"
cp <source> <destination>, with -i for interactive, Will prompt you if the file you've selected will overwrite an existing file in the destination directory. This is a good option, because like the -i option in cp, you'll be given the chance to make sure you want to replace an existing file. 
EG:
```
cp -i 'Bank history' /home/me
cp: overwrite '/home/me/Bank history'? 

```
Or:
```
mv -i 'Bank history' /home/me
mv: overwrite '/home/me/Bank history'? 

```
mv <source> <destination>
Because of the changes to Nautilus and the removal of"/usr/share/nautilus/ui/nautilus-directory-view-ui.xml".

---

### Post by ajgreeny on 2018-09-08
Maybe this will help you even though it is now 6 years old.
[https://askubuntu.com/questions/166542/why-do-the-copy-to-and-move-to-context-menus-in-nautilus-only-offer-home-a](https://askubuntu.com/questions/166542/why-do-the-copy-to-and-move-to-context-menus-in-nautilus-only-offer-home-a)

I use Xubuntu with thunar file manager and have had custom actions from a right click setup in that for both "move to" and "copy to" for a long time. I have not seriously used the gnome version of Ubuntu for many years so I am not sure if something similar is available for nautilus but at a quick glance that askubuntu page appears to be like it; others may be able to help more than I can.

---

