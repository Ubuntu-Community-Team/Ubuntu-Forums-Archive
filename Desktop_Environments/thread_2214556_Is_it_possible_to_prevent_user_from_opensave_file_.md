---
title: "Is it possible to prevent user from open/save file dialog in Ubuntu 12.04 LTS"
date: 2014-04-01
forum: Desktop Environments
---

### Post by dech_dragon on 2014-04-01
I've a number of kiosk computer implemented my company's  application which use firefox as front end user interface. All the users  have to do is just staying on firefox to do their job. However when  they click on firefox's "File" Menu and click open or save page as, the  file dialog show up so they can explore the file system including my  back end application files and mapped network drive which I seriously  want to hide for security reason. I've found methods to hide those in  nautilus using the .hidden file but it doesn't work in file/save dialog.


  As I'm very new to Linux, I created user accounts for them as  standard users and I think all user has read access to file system by  default (and should they need it to make operating system and  application run properly?) Then can't I take read permission out from  them? Please correct me if I'm wrong. 
  
So can i just prevent users from open file dialog? An approach i can  think now is that are there any file system or library file that handle  those file/save dialog? so that i can edit permission of them and the  users will get permission denied dialog instead. 

  
If not possible, any suggestion to hide file system and mapped  network folder in file dialog? Please help every suggestion will be  appreciated. Thanks in advance.

---

### Post by deadflowr on 2014-04-02
Make the folders and files you want unviewable with restricted permissions
something like
```
sudo chmod -R 700 <foldernamehere>
```
which will make the folder viewable, writable, and executable for the owner, but no one else.
But this is a very basic means.

More here
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

As a sidenote, I would only do this to files and folders you already own, and not ones owned by the system(root-owned).
That can cause problems.

---

### Post by dech_dragon on 2014-04-02
Thanks deadflowr, I understand that I can modify the permission of files  I want to restrict users access. However the problem is that the users  have to have read access permission in order to make my application run  properly but I want to close the "door" which allow user to see the  files (and structure of directory). And the "door" I mean now is the  file dialog (and save dialog) that show up when users click some menu on  firefox such as "open" or "save page as". So that why I need some ways  to disable these dialog or to hide file system in dialog.

As I'm very new to Linux, please correct me if there are things I'm misunderstand.

---

### Post by buzzingrobot on 2014-04-02
Search "Addons" in Firefox for "kiosk".  I saw a few extensions that might be useful.  Here's one: [https://addons.mozilla.org/en-US/firefox/addon/r-kiosk/](https://addons.mozilla.org/en-US/firefox/addon/r-kiosk/).

If your users must log on, consider segregating the files they need to access into one directory, creating one group for all your users, and giving the group and the individual users read access only to that directory.  You'll need to delve into permissions, groups, etc., but I believe it's doable.

---

### Post by SeijiSensei on 2014-04-02
If you right-click on a tool bar like the top menu, you'll see that you can disable the menu entirely by unchecking the "Menu Bar" box.  As long as users cannot modify the settings in your Firefox profile, they won't be able to get the menu back.

Type "about:config" into the Firefox address bar and search for "toolbar".  You'll see a number of relevant settings.

That won't stop an informed user, though, since browsers also support the file:// URL.  For instance, enter this URL into the address bar: file:///etc/passwd.  (I tried using [noparse][url][/noparse] tags, vBulletin apparently disables links like these.)

So you probably also want to disable the address bar as well.

Presumably the kiosk shows a main page with links to others.  Just make that front page the default home page in Firefox.  I'd probably also use some Javascript to revert to the front page after reaching a maximum idle time.

---

### Post by dech_dragon on 2014-04-04
Many Thanks to buzzingrobot, the "r-kiosk" Addon is very useful and partially answer what I'm looking for. However if users open pages that contain pdf content, firefox still show up pdf tool bar with a save button. Again, it open up file dialog and allows users to explore filesystem and mapped network drive that I need to hide. So I'm still looking for some ways to permanently disable the file dialog.

For example, in the case below
[http://ubuntuforums.org/showthread.php?t=1363852](http://ubuntuforums.org/showthread.php?t=1363852)
they remove the file: /usr/lib/gtk-2.0/2.10.0/printbackends/libprintbackend-file.so to disable "print to file" function.

And another case
[https://answers.launchpad.net/ubuntu/+source/nautilus/+question/186540](https://answers.launchpad.net/ubuntu/+source/nautilus/+question/186540)
they edit permission of the folder: /usr/lib/gvfs/gvfsd-smb-browse to prevent users from clicking "Browse Network" button in Nautilus.

Then my question is "are there something like that ?" , "Are there any file system or library file that handle  those file/save  dialog ?" 
So that i can edit permission of that files and the  users will get  permission denied dialog instead.

=========================================================================

Also thanks to SeijiSensei, that's valuable suggestion. I'll do more research about that.

---

### Post by buzzingrobot on 2014-04-04
You could compile Firefox from source, commenting out/removing the dialogues that trigger the file system access.

---

### Post by dech_dragon on 2014-04-19
After all, deadflowr's answer is correct.  But I did a slight difference, something like

sudo chmod -R 773 <foldernamehere> 

Removing the read permission from the directory prevents users to list  the contents of a directory. As a result, users cannot "see" the  contents manually via file dialogue or nautilus but the application  still can "read" them properly. 

Sorry deadflowr, I misunderstood at first because  I'm not familiar with linux permission. Thanks everyone here for your help :)

---

