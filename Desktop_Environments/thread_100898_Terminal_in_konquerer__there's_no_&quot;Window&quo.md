---
title: "Terminal in konquerer ? there's no &quot;Window&quot; menu!"
date: 2005-12-08
forum: Desktop Environments
---

### Post by robanicek on 2005-12-08
In the KDE Helpcenter and also in the Konquerer manual it says that there is the posibility of emulating a terminal in konquerer that would follow the file navigation in the file manager. Sounds like a great feature and there's even a picture of it in the manual (help:/konqueror/commandline.html) , but in my konquerer there's no Window menu!? Is it another version? I'm using Konquerer 3.4.3 (KDE 3.4.3) ...

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=robanicek]In the KDE Helpcenter and also in the Konquerer manual it says that there is the posibility of emulating a terminal in konquerer that would follow the file navigation in the file manager. Sounds like a great feature and there's even a picture of it in the manual (help:/konqueror/commandline.html) , but in my konquerer there's no Window menu!? Is it another version? I'm using Konquerer 3.4.3 (KDE 3.4.3) ...[/QUOTE]
Try browsing to a file URL (like /home/robanicek, maybe?) and press CTRL+E or go to Tools -> Execute a Command.

---

### Post by robanicek on 2005-12-08
[QUOTE=cwaldbieser]Try browsing to a file URL (like /home/robanicek, maybe?) and press CTRL+E or go to Tools -> Execute a Command.[/QUOTE]

Yes, that works, but it's just a command line no terminal.

Finally I got a twaek:
 Editing the toolbar I could add the "Show Terminal Emulator" Button. 

But I still find it very strange that there's no Window menu in the top of my Konqueror!! ... and I didn't mess around with it before, not even know how to add or remove menus in the top ...

---

### Post by MartinG on 2005-12-08
For some reason the Kubuntu maintainers seem to have left out the Window menu. I did a quick-and-dirty cut-and-paste from an old config file, as follows.

BACK UP and then edit /home/<yourname>/.kde/share/apps/konqueror/konq-kubuntu.rc, and insert the following between the Settings and Help sections (make sure you study the file structure and get it in the right place!):

<Menu append="settings_merge" name="window" >
   <text>&amp;Window</text>
   <Action name="splitviewh" /> 
   <Action name="splitviewv" />
   <Action name="removeview" />
   <Separator/>
   <Action name="newtab" />
   <Action name="duplicatecurrenttab" />
   <Action name="breakoffcurrenttab" />
   <Action name="removecurrenttab" />
   <Separator/>
   <Action name="tab_move_left" />
   <Action name="tab_move_right" />
   <Separator/>
   <ActionList name="toggleview" />
  </Menu>

If you exit and kill all instances of Konqueror and restart it you should have a Window menu.  As for the terminal emulator, I find it worthwhile to add a button to a toolbar (Settings -> Configure toolbars).

---

