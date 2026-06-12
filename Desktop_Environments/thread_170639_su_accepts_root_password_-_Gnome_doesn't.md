---
title: "su accepts root password - Gnome doesn't"
date: 2006-05-05
forum: Desktop Environments
---

### Post by Zo|oZ on 2006-05-05
I've just got Ubuntu (breezy badger) installed and I want to add some web-dev applications. From the desktop menu I select System-->Administration-->Add Applications. A dialog asks for my password, there's a pause, then a dialog said that the password was wrong. However, when I open a terminal and enter su the password is accepted.

Now I have logged out and logged in again. From the desktop menu I select System-->Administration-->Add Applications: nothing happens?

I am using the DVORAK keyboard layout - does that change things?

---

### Post by cskeide on 2006-05-05
When you're asked for a password i GNOME, enter your user password, not the root passowrd.

---

### Post by Qrk on 2006-05-05
The gnome dialog wants your user password... not the root password. Its the difference between sudo and su.

I assume you enabled the root password? (or did you do an expert install?)

---

### Post by kzutter on 2006-05-05
su is asking for root's password

gnome is asking for the user's password (as does sudo)
the gnome user must also have certain rights - the first user that you setup with should have these rights

---

### Post by Zo|oZ on 2006-05-05
Aha! 

I did do an expert install. I tried to do a lazy-bones install but it failed so I did expert install and it worked. Reading the forums here suggested turning off apci, so I ran expert pci=off and the install proceeded happily.

I selected the option for multi-user desktop 
I selected the option for shadow passwords
I set a password for the root user
I set up one user account

Now when the dialog appears I have entered my user password. No complaints from Gnome this time but nothing else happens either. It just me and the desktop picture :-(

---

### Post by Qrk on 2006-05-05
Is your normal user part of the Wheel group? Make sure that you are. This will allow them to sudo. ( you can use sudo from a terminal this way too)

I don't think you needed to do an expert install, however. Did you try using the noacpi boot code without the expert before it?

---

### Post by Zo|oZ on 2006-05-05
I opened a terminal, typed su, logged in as root, typed '/usr/bin/gnome-app-install &' and the "Add Applications" application fired up.

Perhaps I'm not in sudoers?

---

### Post by Qrk on 2006-05-05
Probably not then. Its difficult to add a user to sudoers, however. First, make sure the wheel group is in sudoers.

```
visudo /etc/suoders
```

You should see a line like this, if not add it.

%wheel ALL=(ALL) ALL

(it may be a little different, if it is, don't change it)

You can add your user to the wheel group (I believe) by running the app "users-admin" as root.

---

### Post by Zo|oZ on 2006-05-05
[QUOTE=Qrk]Is your normal user part of the Wheel group? Make sure that you are. This will allow them to sudo. ( you can use sudo from a terminal this way too)

I don't think you needed to do an expert install, however. Did you try using the noacpi boot code without the expert before it?[/QUOTE]

No, I didn't try using noacpi without expert.

Looking at  /etc/groups. It doesn't contain Wheel as a group.

I've just added it like this

wheel: x:0:root,malcolm

and I'm rebooting. 

Back up now - No change.

---

### Post by Zo|oZ on 2006-05-05
[QUOTE=Qrk]Probably not then. Its difficult to add a user to sudoers, however. First, make sure the wheel group is in sudoers.

```
visudo /etc/suoders
```

You should see a line like this, if not add it.

%wheel ALL=(ALL) ALL

(it may be a little different, if it is, don't change it)

You can add your user to the wheel group (I believe) by running the app "users-admin" as root.[/QUOTE]


I've done all that and rebooted. The problem remains, I can enter my password but it the application doesn't start. 

I'm giving up for tonight. 

thanks for your help.

---

### Post by xenmax on 2006-05-05
Zo|oZ, did you manage to successfully add your username  to sudoers list?
For me, this is the thread which helped:
[http://ubuntuforums.org/showthread.php?t=146859](http://ubuntuforums.org/showthread.php?t=146859)

Hope this helps.

---

### Post by Zo|oZ on 2006-05-05
[QUOTE=Qrk]Probably not then. Its difficult to add a user to sudoers, however. First, make sure the wheel group is in sudoers.

```
visudo /etc/suoders
```

You should see a line like this, if not add it.

%wheel ALL=(ALL) ALL

(it may be a little different, if it is, don't change it)

You can add your user to the wheel group (I believe) by running the app "users-admin" as root.[/QUOTE]

that didn't work for me. This did:

1. open terminal , type su. When asked type the root password.
2. type visudo
3. scroll to the bottom of the file. There is the line root ALL=(ALL) ALL.
4. Add beneath that line your user name and ALL=(ALL) ALL
5. Save ctrl-o (oh, not zero)
6. Exit ctrl-x

---

### Post by Zo|oZ on 2006-05-05
[QUOTE=xenmax]Zo|oZ, did you manage to successfully add your username  to sudoers list?
For me, this is the thread which helped:
[http://ubuntuforums.org/showthread.php?t=146859](http://ubuntuforums.org/showthread.php?t=146859)

Hope this helps.[/QUOTE]


missed this post - That's the trick, thanks

---

### Post by gmcle454 on 2006-05-14
> 
	
Default Re: su accepts root password - Gnome doesn't
Quote:
Originally Posted by xenmax
Zo|oZ, did you manage to successfully add your username to sudoers list?
For me, this is the thread which helped:
[http://ubuntuforums.org/showthread.php?t=146859](http://ubuntuforums.org/showthread.php?t=146859)

Hope this helps.


missed this post - That's the trick, thanks

That did the trick for me too. Thanks!

---

### Post by 3rdalbum on 2006-05-14
Same thing happened to me when I first installed Ubuntu onto my iMac. When the Ubuntu installer accepts a root password, the first normal user it creates doesn't have sudo privileges. It's a terrible bug, and since I couldn't use Vi I had to reinstall :-(

Glad to see that you got it working.

---

