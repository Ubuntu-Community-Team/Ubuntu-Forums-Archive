---
title: "Fileassociations don't stick"
date: 2009-11-14
forum: Desktop Environments
---

### Post by SergeiFranco on 2009-11-14
Kubuntu Karmic (64bit, KDE 4.3.2).
System Settings->File Associations->Change order/remove applications for any file type, press apply, it all reverts back to "default" (I guess the order the applications were installed).

All I want is to make amarok default for mp3.
Is there a way to change it manually?

Thanks.

---

### Post by Zorael on 2009-11-15
System-wide application details are stored in /usr/share/applications/. There (or in its subdirectories) you'll find .desktop files for every single application that's integrated into your desktop environment.

When the system generates the menu with all the applications, it parses those files and reads their names, comments, executable paths etc, and then combines it all into menu entries. Likewise when it's generating mime cache and filetype handling.

Now, when you perform changes to the menu when logged in as a user, it obviously can't write to /usr because of privileges. So instead it writes an override into ~/.local/share/applications with the settings you want it to have.

[list][*]To make user-specific changes manually, you copy a /usr/share/applications/application.desktop file to ~/.local/share/applications/application.desktop, and then edit it. Then run 'kbuildsycoca4'.
[*]To make system-wide changes manually, just edit the /usr/share/applications/application.desktop file, and then do 'kbuildsycoca4'.[/list]

Now, as for mimetype *ordering*, as in "which application should be the default for MP3 files", that's saved in ~/.local/share/applications/mimeapps.list. In it, you'll see a header named '[Added Associations]', under which there'll be mimetype entries listing application .desktop files in the order in which files of that mimetype should be opened. Ergo;
```
[Added Associations]
audio/mpeg=kde4-amarok.desktop;smplayer.desktop;audacity.desktop;
```
Amarok > SMPlayer > Audacity.

If you want to remove an application entirely, you can either make entries in that mimeapps.list for the mimetypes you don't want the application to open and omitting the its .desktop file, or you can make user-specific/system-wide changes to the application's .desktop file itself, and remove the mentioning of that mimetype. Don't forget to kbuildsycoca4. For instance, I always remove the smplayer_enqueue.desktop file entirely, since I never use the "Enqueue in SMPlayer" entry.

If the settings aren't sticking, perhaps you've managed to change ownership or privileges of that mimeapps.list file, or perhaps of the whole ~/.local/share/applications directory? This would happen, for instance, if you ran an application with sudo and then tried to change filetype settings. Like, 'sudo dolphin', right click file, edit filetypes, save.

(Never run graphical applications with sudo; *always* use kdesudo, else stuff like this happens)

---

### Post by SergeiFranco on 2009-11-15
Thanks for that, here what I have:

```
sergei@sergei:~$ cat ~/.local/share/applications/mimeapps.list
[Added Associations]
audio/mp3=kde4-amarok.desktop;vlc.desktop;kde4-kmplayer.desktop;soundconverter.desktop;smplayer_enqueue.desktop;audacity.desktop;totem.desktop;gnome-mplayer.desktop;kde4-kaffeine.desktop;mplayer.desktop;smplayer.desktop;
```

```
sergei@sergei:~$ ls ~/.local/share/applications -lad
drwx------ 3 sergei sergei 4096 2009-11-15 13:11 /home/sergei/.local/share/applications
sergei@sergei:~$ ls ~/.local/share/applications -la
total 80                                           
drwx------  3 sergei sergei 4096 2009-11-15 13:11 .
drwx------ 13 sergei sergei 4096 2009-11-01 21:38 ..
-rw-------  1 sergei sergei  279 2009-06-03 20:07 adept_manager.desktop
-rw-------  1 sergei sergei  280 2007-04-22 15:10 amsn.desktop         
-rw-------  1 sergei sergei  245 2008-08-27 22:13 defaults.list        
-rw-------  1 sergei sergei  432 2009-02-07 13:17 Google-googleearth.desktop
-rw-------  1 sergei sergei  520 2009-06-27 21:22 kde4-kpackagekit.desktop  
-rw-------  1 sergei sergei  657 2007-09-27 20:44 kde-kaffeine.desktop      
-rw-------  1 sergei sergei  383 2009-01-23 23:29 kde-kfaxview.desktop      
-rw-------  1 sergei sergei  293 2008-03-01 16:24 kde-kwrite.desktop        
-rw-------  1 sergei sergei  195 2008-01-25 00:46 ksnapshot.desktop         
-rw-------  1 sergei sergei 2244 2009-11-15 13:11 mimeapps.list             
-rw-------  1 sergei sergei  351 2008-10-27 21:10 mozilla-thunderbird.desktop
-rw-------  1 sergei sergei 1041 2007-09-27 20:44 mplayer.desktop            
-rw-------  1 sergei sergei  314 2008-11-30 10:34 qtparted.desktop           
-rw-------  1 sergei sergei  577 2007-10-22 22:31 thunderbird.desktop        
-rw-------  1 sergei sergei 1788 2007-09-27 20:44 totem.desktop              
-rw-------  1 sergei sergei  985 2009-06-27 21:18 vlc.desktop                
drwxr-xr-x  3 sergei sergei 4096 2007-05-19 01:20 wine
```
permissions seem to be fine (unless it has to be 0755 ?)

It looks like ~/.local/share/applications/mimeapps.list is completely ignored
EDIT: I just noticed I don't have kde4-amarok.desktop!
I tried ln -s /usr/share/applications/kde4/amarok.desktop ~/.local/share/applications/kde4-amarok.desktop

didn't work...

---

### Post by Zorael on 2009-11-16
This is increasingly weird. And the permissions of both ~/.local and ~/.local/share is okay, too?

Does this happen if you create a new (temporary) user and log in as him/her/it?

---

### Post by mrboojive on 2009-11-16
Something else you could try is going into the .desktop file for Amarok and finding the line that starts with "InitialPreference=" and changing the value to 9. The "InitialPreference" property determines which app is chosen to be the default (i.e., the one with the highest InitialPreference is the default). If the .desktop file for Amarok doesn't have that property, then just add a line that says "InitialPreference=9"

---

### Post by SergeiFranco on 2009-11-18
Permissions seem to be fine, InitialPreference did not do anything.
What also is peculiar that new user had right order (amarok first), but also "read only".

I am not sure if it is relic from upgrade or what, but it drives me nuts.

---

### Post by mrboojive on 2009-11-18
You might try resetting the menus for your user. That should also reset all of the file associations. Right click on the K Menu and select "Menu Editor." Then do "Edit" > "Restore to System Menu."

---

### Post by SergeiFranco on 2009-11-18
That did work, it put Amarok on top :).
But it is still "read only" :( .

---

### Post by mrboojive on 2009-11-18
What do you mean by "read only"?

---

### Post by SergeiFranco on 2009-11-19
Well, if I try to change order, it will revert as soon as I click apply.

---

