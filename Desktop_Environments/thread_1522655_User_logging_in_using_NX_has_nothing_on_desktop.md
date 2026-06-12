---
title: "User logging in using NX has nothing on desktop"
date: 2010-07-02
forum: Desktop Environments
---

### Post by lsutiger on 2010-07-02
I am running a remote login server where I have multiple users. I am using No Machine NX for the remote login software. I also used Ubuntu Tweak and did some editing in gconf-editor in order to lockdown the machine. In the end the user has some files on their desktop they can view and one panel with a logoff button. This system has been in place for about 2 years now and running pretty smoothly.

I am not sure if this is an NX problem or Gnome problem.

I have just one user, all of a sudden, that has nothing on the desktop and no panel when they login. The system was set for each user to have their /home folder as their desktop folder.

I am not sure where to start trouble shooting this. I have looked a quite at few of the gconf.xml fiels for the user, but do not see anything out of the ordinary (comparing to other user's gconf.xml files) 

Could some guru on here point me in the right direction?

---

### Post by lsutiger on 2010-07-06
bump

---

### Post by lsutiger on 2010-07-11
Bump

---

### Post by Dart00 on 2010-07-11
Make him/her a new account and see if it happens again? Also did you check to make sure his/her files are still on the network/server?

---

### Post by lsutiger on 2010-07-12
Thanx for the reply Dart00. 

I was trying to avoid recreating the account. All of the files for the user are on the server in the correct place.

The fact that the panel doesn't even show up tells me it is something to do with the user settings being corrupt. Which setting, I have no idea! ](*,)

Also it does not matter which computer the user is logs in from. I tried from several different locations including ones from outside the network.

---

### Post by Dart00 on 2010-07-13
Hmmm...maybe something broke in gconf? Im not really sure but maybe if you could get a terminal, dump all there gconf values as a backup, dump another "working" set from another user account, unset all of theres and restore the dump from the working acount then log out and back in?

---

### Post by lsutiger on 2010-07-13
Thanx for that input...will try tomorrow.

---

### Post by Dart00 on 2010-07-14
Oh ya.....The gconf values I think youd be interested in our under /apps/Panel. Thats all the gconf data that contains data about the users panel setup. If anything missing or even the panel folder is missing....your panel would not work or even be there at all.

And while i got some time here are some helpfull commands:

Backup Panel Configuration:
gconftool-2 --dump /apps/panel > Gnome_Panel.xml

Wipe Out Panel Configuration: (WARNING: DATA LOSS!!!!)
gconftool-2 --unset "/apps/panel"

Restore (Or overwrite if it was never unset) Panel Configuration:
gconftool-2 --load Gnome_Panel.xml

There may be ways of wiping out your panel configuration and having gnome rebuild it but i just use these commands.

I wrote a very very nice GUI backup and restore script that I used in the Win2-7 Pack ([http://gnome-look.org/content/show.php/Win2-7+Pack?content=113264](http://gnome-look.org/content/show.php/Win2-7+Pack?content=113264)) that works great and it backs up a lot more then just the panel.

---

