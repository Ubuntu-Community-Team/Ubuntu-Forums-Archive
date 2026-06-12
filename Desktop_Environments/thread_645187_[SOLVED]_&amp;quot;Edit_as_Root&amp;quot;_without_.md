---
title: "[SOLVED] &amp;quot;Edit as Root&amp;quot; without Kate"
date: 2007-12-19
forum: Desktop Environments
---

### Post by growingtedium on 2007-12-19
I just noticed the "Edit as Root" option (KDE), which would be very helpful if it worked.  When I try to use it, I get "command not found".  I assume this is because I've removed Kate in favor of Kedit, but I imagine there is a config file somewhere that specifies what "Edit as Root" does - I just don't know where.  Any ideas?

---

### Post by jscudder on 2007-12-19
You can use Kate as 'Root' from the command line by typing 'su kate filename.txt'  where filename.txt is the file you wish to edit.  You will be prompted for your password.

An alternate method is to create a Root-Kate menu or desktop application link.  Create a new application link to kate and select 'Advanced Options' in the link Properties.  There you have the option to run kate 'as a different user'.  Run it as 'root'.  You will be prompted for the root password before the application is run.

---

### Post by growingtedium on 2007-12-19
I generally use something like ```
 sudo nano /path/file
``` but it would be convienient if I could use the GUI to open su Kedit directly from Konqueror.  What I'd like to do is change the "Edit as Root" option to run with Kedit rather than Kate.  

I might be able to create a link or script so that when it attempts to run Kate, the request is forwarded to Kedit...  This would have been handy to have working this morning when I was wading through all my old menu.lst's trying to patch my comptuer back together after the kernel update.

---

### Post by growingtedium on 2007-12-20
EUREKA!  I figured there would be a config file somewhere.  I entered
```
sudo nano /usr/share/apps/konqueror/servicemenus/edit-as-root.desktop
```
and replaced kwrite with kedit.  Piece of cake.

While I was trying to fix this I found an alternate root [[COLOR="Blue"]toolbar addon[/COLOR]]("http://www.kde-apps.org/content/show.php/Root+Actions+Servicemenu?content=48411") from kde-apps that would have worked.

---

### Post by adam.skinner on 2007-12-20
You'll probably want to change this ti kdesu or gksu instead of sudo.

---

