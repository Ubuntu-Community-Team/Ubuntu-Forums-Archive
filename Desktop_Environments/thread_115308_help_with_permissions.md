---
title: "help with permissions"
date: 2006-01-10
forum: Desktop Environments
---

### Post by RikkiD04 on 2006-01-10
i get this message before i log on:

"Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions."

could someone tell me how to fix that?

---

### Post by pataphysician on 2006-01-10
do these tips help?

[http://ubuntuforums.org/archive/index.php/t-91455.html](http://ubuntuforums.org/archive/index.php/t-91455.html)

---

### Post by Ampersand on 2006-01-10
from a terminal:
```
sudo chown -R username /home/username
```
(replacing username with whatever your login name is)
Then 
```
chmod 644 ~/.dmrc
```
Should fix it.

---

### Post by RikkiD04 on 2006-01-10
still getting the same message, any ideas?

---

### Post by Ampersand on 2006-01-10
Could you try opening Nautilus, enabling View - Show hidden files, then right clicking on .dmrc and going to Properties. Then under the Permissions tab, make sure it's owned by you, and the permissions are set to rw-rw-r--?

Did you do anything before this happened?

---

### Post by RikkiD04 on 2006-01-10
i'm not sure what nautilus is, could you explain?

and the last thing i did was operate kzenexplorer, which i've figured out, i guess, that this is a problem with running kde programs

---

### Post by Madpilot on 2006-01-10
Nautilus is Gnome's default file manager.

Places menu --> Home; the app that starts is Nautilus.

---

### Post by RikkiD04 on 2006-01-10
i tried to find my .dmrc file, but it's not under nautilus. could that be the problem? can it not exist?

---

### Post by pataphysician on 2006-01-10
can you see any files with names that start with a dot? if not, you may need to show hidden files (oh no...):

in nautilus, click edit-->preferences. on the first page you see, under the "view," tab, make sure you have a checkmark on, "show hidden and backup files."

if you now see the .dmrc file, right-click that and choose properties. then click on the "permissions" tab at the top. it should look like this:

file owner: {you}
file group: {you}
owner  [x]read [x]write [ ] execute
group  [x]read [ ]write [ ] execute
others [x]read [ ]write [ ] execute
special flags:
 [ ] set user id
 [ ] set group id
 [ ] sticky
text view: -rw-r--r--
number view: 644


----------------------

if you definitely don't see the file, i guess try creating a blank file with those permissions?

---

### Post by RikkiD04 on 2006-01-10
[QUOTE=pataphysician]can you see any files with names that start with a dot? if not, you may need to show hidden files (oh no...):

in nautilus, click edit-->preferences. on the first page you see, under the "view," tab, make sure you have a checkmark on, "show hidden and backup files."

if you now see the .dmrc file, right-click that and choose properties. then click on the "permissions" tab at the top. it should look like this:

file owner: {you}
file group: {you}
owner  [x]read [x]write [ ] execute
group  [x]read [ ]write [ ] execute
others [x]read [ ]write [ ] execute
special flags:
 [ ] set user id
 [ ] set group id
 [ ] sticky
text view: -rw-r--r--
number view: 644


----------------------

if you definitely don't see the file, i guess try creating a blank file with those permissions?[/QUOTE]


well i found the file, the permissions are under my username, and everything else now matches, but i still get the message. do you know why that is?

---

### Post by pataphysician on 2006-01-10
not sure what else the problem could be. ampersand suggests giving write permission to the group, as well; but mine isn't like that and i have no problems. (infact, my file is 600 -- no read or write permissions to anyone but the owner). my only other suggesstion would be to rename the current .dmrc file (to, say .dmrc.old), then creating a new one. to make a new one, click file-->new-->empty document. rename the document .dmrc. open it up and enter the lines

[Desktop]
Session=default

make sure permissions on the file are as outlined above, and you may as well give the group write permission as well. save it and reboot.

if that doesn't work, i don't know. ampersand is more well-versed here than i am. maybe they'll have some more useful ideas!

---

### Post by RikkiD04 on 2006-01-10
> **pataphysician]not sure what else the problem could be. ampersand suggests giving write permission to the group, as well said:**
> 
Session=default

make sure permissions on the file are as outlined above, and you may as well give the group write permission as well. save it and reboot.

if that doesn't work, i don't know. ampersand is more well-versed here than i am. maybe they'll have some more useful ideas!

thanks a lot for your help, it's fixed now, but from trying so many things, i have a few other problems (figures). i am so glad i came to this site though, linux users are so nice and helpful

---

### Post by eyebrowman92 on 2006-01-10
[QUOTE=Ampersand]from a terminal:
```
sudo chown -R username /home/username
```
(replacing username with whatever your login name is)
Then 
```
chmod 644 ~/.dmrc
```
Should fix it.[/QUOTE]


i had the same problem and the above solution worked for me.

---

### Post by nu2this on 2006-01-10
this is good to know if it happens to me.

---

