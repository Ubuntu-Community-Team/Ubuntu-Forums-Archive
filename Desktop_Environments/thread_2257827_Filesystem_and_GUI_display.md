---
title: "Filesystem and GUI display"
date: 2014-12-22
forum: Desktop Environments
---

### Post by renbri on 2014-12-22
I'm trying to fully comprehend the ubuntu filesystem and I'm puzzled by the display in front of me.


In the left half ofthe screen I have the GUI image of a folder(file? subdirectory?) from the /usr directory. Across the title bar are the names usr  share  applications, and the first few icons are:
Access Prompt    Account authentication    Account update tool    Activity Log Manager    Additional Drivers    AisleRiot Patience    Amazon    Appearance    AptURL    Archive Manager   Backups …

In the right half ofthe screen I have the terminal showing the results of the command:
ls/usr/share/applications, and the first few items are:
activity-log-manager.desktop  
apport-gtk.desktop
apturl.desktop
bamf-2.index
baobab.desktop
…
Now, I thought that maybe the terminal listing would show a few “hidden” or system files that the GUI didn't, but I didn't expect the two to be so radically different when both were supposed to represent the same directory, namely /usr/share/applications.


Can someone pleaseenlighten me ?

---

### Post by grahammechanical on 2014-12-22
Can we please be clear about what you are doing? You have the file manager open to /usr/share/applications/. Is that correct? And in that folder you see lots of icons representing applications, such as Access Prompt; Account Authentication; Account Update Tool, and so on. Well I also see that stuff.

Now when I open the terminal and run this command

```
[COLOR=#000000]ls/usr/share/applications[/COLOR]
```[COLOR=#000000]

I get this result

[/COLOR]> ls/usr/share/applications
bash: ls/usr/share/applications: No such file or directory




[COLOR=#000000]So you have not posted the correct version of the command that you used. Now when I run this series of commands

```
cd ..
cd ..
cd /usr/share/applications
ls
```

I get a long list of all the applications in the /usr/share/applications folder.directory. Here is a sample

[/COLOR]> activity-log-manager.desktop       gcr-viewer.desktop                   gnome-sound-panel.desktop             nautilus.desktop                     ubuntu-software-center.desktop
alacarte.desktop                   gedit.desktop                        gnome-sudoku.desktop                  nautilus-folder-handler.desktop      unity-activity-log-manager-panel.desktop
apport-gtk.desktop                 gkbd-keyboard-display.desktop        gnome-system-log.desktop              nautilus-home.desktop                unity-appearance-panel.desktop




[COLOR=#000000]I do not think that there are any hidden files in /usr/share/applications/. We can edit the preferences of the File Manager to always show hidden files. It is Edit/Preferences and tick Show hidden and backup files.

To show hidden files in the terminal run

```
ls -a
```

or 

```
 ls --all
```

Try this

```
ls -a /usr/share/applications/
```

Does that give you what you want?

Regards.

[/COLOR]

---

### Post by deadflowr on 2014-12-22
> [COLOR=#000000]I didn't expect the two to be so radically different when both were supposed to represent the same directory[/COLOR]

Are they though? 
Count the content inside the directory from the output from the terminal, and then count the output from what you see in the file manager.
They'll match, I'm pretty sure.

The real difference is that the file manager treats .desktop labeled files different than other files, where as it displays the Name given for the file, and whatever icon has been set.
These two things are actually set inside the file.
Here's a typical instance (This one for Eye of Gnome- thew picture viewer app):
```
[Desktop Entry]
Name=Image Viewer
Comment=Browse and rotate images
TryExec=eog
Exec=eog %U
Icon=eog
StartupNotify=true
Terminal=false
Type=Application
Categories=GNOME;GTK;Graphics;RasterGraphics;Viewer;

```
[I've edited out some of the output, but what is above is most typical for all apps, in one way or another]

Now the name of the file is eog.desktop, but if you look for it in the file manager you won't find it, but rather you would find the Name that is listed inside the file "Image Viewer"
And as for why the Icon name seems to simple --just eog(for eye of gnome) well that is because the icon pack you are using has an icon for eog. It the icon pack you used did not have an icon for eog, then you'd have a generic icon in place; usually something gray and mundane.
Of the entries in this file, the three that are of most importance though, are the Name, the Exec, and the Type. A desktop file must have all three to be functional. Everything else is purely optional, albeit also helpful. The most important other the Name would be Exec, which as you might tell, is the command for the application to run. Type tells the system what kind of desktop file it is, in this case an Application .desktop file. As opposed to something like a Link Type, which would work differently.

I feel like I've ramble on a bit, but I hope this helps you a little in understanding what you see, and why it looks different between the two.

---

### Post by renbri on 2014-12-23
Yes, grahammechanical, my reporting was erroneous but only because I don't do a very good job of composing a message and posting it in the forum. The spacing seems to go awry and, although I try editing it in the message box, I still tend to end up with wrong spaces here and there. As with most email type communication, one tends to stifle the frustration and let it pass because most of the time the recipient will figure out what was meant. Of course, when the subject is of this kind, such an attitude just won't do. (Got any tips on cutting and pasting?)
What I actually typed had a space between the ls and the /usr  so it worked fine. The answer to my concealed problem is explained below. 
Thanks anyway.

---

### Post by renbri on 2014-12-23
You've done it again, deadflowr. As you say, the number of files in each display is the same (143 in my case).
In my mind that seems to confirm that they do indeed describe the very same directory; they simply represent it in different ways -decidedly different! Yes?
I shall now study your post and see if I can learn what it all means. Talk about jumping in at the deep end. I've only learned two commands so far (You don't do online courses I suppose?).
Seasons greetings to all

---

