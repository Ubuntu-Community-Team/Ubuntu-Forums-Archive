---
title: "Guide to a guest session on login screen"
date: 2010-10-20
forum: Desktop Environments
---

### Post by kainalu on 2010-10-20
Moderators - I don't know where I learned how to do this, and couldn't find it, so I decided to post here. If this is a dupe, or the wrong place for this, please moderate accordingly.


I learned how to do this on the 'net somewhere. This HowTo will help you create an account on the login screen that will log in the same guest-session seen in the user menu. The advantage of this is that it will be an easily accessible guest account, while not preserving any files or changes on logout, and a higher security model for the account. Confirmed to work on 10.04 - 10.10, but the directions are for 10.10

1. Under an existing administrator account, go to the menu entry System --> administration --> Users and Groups

2. Click Add. you may need to provide a password at this point. Name your new user anything you would like, except guest. The account cannot be called guest, but visitor does nicely. encryption of the account is not needed. This account will be a "booster" account to guest-session 

3. On the next screen, enter a password, and make sure that you click the check box "Don't ask for password on login", Click OK to finish

4. As an extra precaution, click Advanced settings, when back on the Users and Groups screen, and on the User Privileges tab, uncheck Monitor System Logs.

5. Exit the Users and groups menu, and then log out and into your new account

6. Once there, make a folder called GuestManager, and in that folder, make a plain text file called Guestmanager.sh, with this code in it :

```

#!/bin/bash

# Launches the guest session
/usr/share/gdm/guest-session/guest-session-launch
# Logs the user when done
/usr/bin/gnome-session-save --logout

```

7. Save that and then right click on it, go to properties, and then go to the permissions tab. On this tab, click "allow executing file as program", and then close that window.

8. Open the menu entry System --> Preferences --> Startup Applications, and once there, turn off all the startup applications, and then click add. Fill in the name and comment as GustManager, and for the command, enter /home/visitor/GuestManager/GuestManager.sh, where visitor would be the name you picked for the account in step 2. click add, then close

9. Delete all applets and extra toolbars (might want to leave the main gnome menu), and set the background to black or something else bland, and log out. Since this account is just a "booster" none of these toolbars and such will be needed, so removing them saves memory and load time.

10. ENJOY!

---

### Post by DeFrancoj on 2011-04-26
Nice tip; sorry I didn't think of it first. Do you know if any persistent customization of the guest desktop is possible?

---

### Post by kainalu on 2011-05-03
Yes, My guest desktop is customized. I made the following changes, and therefore know they work :

-- adding plugins to firefox or Chrome. Install like normal
-- changing system themes and wallpapers, sounds, and cursors
-- setting up proxy settings for nannyware
-- changing and adding startup programs
-- Gnome-do and Docky, with plugins, and customization.

1. Log in as Guest user.

2. Make all your changes, just the way you want the desktop.

3. switch to a privileged (your) user account by using CTRL + F7 (or F8 F9, etc)

4. Open a terminal window and type 

```

cd /tmp/
ls guest-home
sudo find ./ -type d -iname "guest-home*" -exec cp {} /etc/skel_guest \;

```

5. Now you need to modify the startup script.

```

sudo gedit /usr/share/gdm/guest-session/guest-session-setup.sh

```

Look for ```
 cp -rT /etc/skel/ "$HOME" 
``` (for me it was line 47) and change to ```
 cp -rT /etc/skel_guest/ "$HOME" 
```

Save, and you are all set with your log in. If you need any additional help, please reply. I check once a week. Also, this gentleman has made a very nice guide, and a script, if it helps. I haven't tried it, because my changes were simple, and didn't need it, but it looks good.

[http://ubuntuforums.org/showthread.php?t=1566078](http://ubuntuforums.org/showthread.php?t=1566078)

---

### Post by youknowit on 2011-06-18
I am using Natty (11.04). Thanks for the tip.
It worked for me when I changed the Guestmanager.sh as follows:

#/usr/share/gdm/guest-session/guest-session-launch ##comment out this line
# Use this instead:
/usr/bin/guest-session

---

### Post by kainalu on 2012-04-02
Thank you for the additional information for Natty!

---

