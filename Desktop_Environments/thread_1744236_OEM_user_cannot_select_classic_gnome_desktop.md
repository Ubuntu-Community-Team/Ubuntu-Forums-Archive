---
title: "OEM user cannot select classic gnome desktop"
date: 2011-04-30
forum: Desktop Environments
---

### Post by bcz on 2011-04-30
I upgraded a machine with only default OEM user from 10.10 to 11.04 and my extremely useful gnome desktop was trashed by the upgrade.

If I logout, the login screen does not give me a choice of login shells.

What options do I have to ressurect a more useful shell than the default toy for untrained office staff and game players

Why do people do things like this  (Rhetorical question)

---

### Post by bcz on 2011-04-30
Progress so far...

Prepare system for shipping...  DO NOT DO THIS  it possibly wipes out all data in /home/oem with no warning

Reboot and setup user account

Still no choice of GUI shells on login

Use synaptic to install gnome

In parallel try to make default shell usable for program development

---

### Post by bcz on 2011-04-30
Finally

Go to login preferences  (whatever it is called under 11.04 default desktop)

Unlock logins

Select "Ubuntu Classic"

Logout and login

Classic login desktop appears.

Now setup all old links as they were before trashed by 11.04 installation

Copy all files from /home/oem to /home/userAC

Get thunderbird from repositories

Reinstall thunderbird and setup email accounts

Likely some of the above are only necessary because I replaced the oem account with a user account.

---

### Post by Krytarik on 2011-04-30
Although you managed it already anyway, when you were at the login screen initially, did you mind to click at the username? Only then the "Session" options are getting revealed, and obviously only if you need to enter a password to log in.

---

### Post by bcz on 2011-04-30
Kytarik

Clicking on username did not give me these options.


I get one big problem....

All the files in the /home/oem directory have disappeared,  so it might be a case of recover from last backup.  Not what I expected.  My love for Ubuntu is fast disipating.  To delete user data on an upgrade is not acceptable.

---

### Post by Krytarik on 2011-04-30
> **bcz said:**
> 
All the files in the /home/oem directory have disappeared,  so it might be a case of recover from last backup.  Not what I expected.  My love for Ubuntu is fast disipating.  To delete user data on an upgrade is not acceptable.
Didn't you say that moved those files/dirs over to the new user, in post #3? So, they were definitely still there after the upgrade.

---

### Post by bcz on 2011-04-30
Kryatik

When I boot into the user account with the gnome classic shell there is no sign of any files in the /home/oem directory except for an empty file called fh.log

"sudo chmod 0777 /home/oem/*"  does not help.

fh.log has root ownership and might be left over from my testing

I planned to move them, but none were there.

So my post was premature and overly optimistic.

I suspect "prepare system for shipping" was when the data disappeared, rather than the upgrade process itself.  One would expect a warning that the oem data was going to be removed.  It is not an "rm *" which explicitely asks all files to be wiped.

---

### Post by Krytarik on 2011-04-30
> **bcz said:**
> 
I suspect "prepare system for shipping" was when the data disappeared
It seems so, since you are referring to the user as an OEM* user, and those options sound like resetting anything. So, the user data is indeed gone for good.

* I honestly don't know what it is. Is it a special option you can choose upon installation?
(no need to elaborate, if you are too depressed to do so)

---

### Post by mafitzpatrick on 2011-04-30
Just FYI I don't get the desktop login options when logging in either. Switching requires logging in going to system settings & changing the default. 

Haven't figured out why, but I don't need to change desktop...well...ever. :)

---

### Post by Krytarik on 2011-04-30
> **mafitzpatrick said:**
> Just FYI I don't get the desktop login options when logging in either. Switching requires logging in going to system settings & changing the default. 

Have you maybe disabled the password query at login?
And do you click at your username before searching for the "Session" options?

---

### Post by mcduck on 2011-05-01
> **Krytarik said:**
> It seems so, since you are referring to the user as an OEM* user, and those options sound like resetting anything. So, the user data is indeed gone for good.

* I honestly don't know what it is. Is it a special option you can choose upon installation?
(no need to elaborate, if you are too depressed to do so)

Yes, the OEM user account is what's used when you do an OEM install of Ubuntu. It's not supposed to be used as an actual user account but instead only to add OEM customizations and such to the system during the install. Afterwards you are supposed to run the "*sudo oem-config-prepare*"-command to finish the installation and remove the OEM account, thus preparing the system for the end user. (The next time the system is started it asks for the user details and creates the actual user account for the system's owner).

It really is something only intended for OEM manufacturers selling computers with Ubuntu preinstalled, there's no reason for any home user to do it. And if you do it, you must finish the OEM install properly as, like I said, the OEM account is only intended as a temporary account which will be removed afterwards.

---

### Post by Krytarik on 2011-05-01
Cool, great explanation, thanks mcduck!

---

### Post by bcz on 2011-05-01
Kytarik

When installing an earlier Ubuntu release, maybe 2+ years ago, there was an option which I tried  (Forget how it was described, but as I tried it likely it was relevant to me).  The result was that I was not asked to setup a user account, but the system automatically booted to user "oem".  On the desktop was an icon entitled "Prepare system for shipping".  I just continued to use the system with no problems until now.

All nicely explained by mcduck.  Had I noticed I would not have bothered to type above.

With 11.04 likely the options to select a desktop on the login screen dont appear.  As stated the login options can be changed from the system settings which are found by clicking the power button icon and ignoring the shutdown/restart options, rather than from the classic gnome menu line.  Intuitive to some maybe, but I could not find the system settings when I looked for them.

Looks like 10.04 also does not allow desktop selection from the login screen with latest patches applied.

Well web search shows login screen with options to change the window manager.  As I had none, I assumed it was because the oem user was special and prepared my system for shipping so I would get a standard user account.  I did consider doing a backup, but decided that Ubuntu was rock solid, so it was unnecessary !!!!

I do think that I should have been warned that all data in /home/oem/* was going to be deleted.  My thread to this effect appears to have been moderated, so hopefully someone will change this area shortly.

I do feel that the default 11.04 desktop is retrograde so far as serious programming is concerned,  Until now  (11.04) gnome as a desktop gave me everything I wanted.  Not sure that others will find the 11.04 desktop deficient.  Time will tell

---

### Post by Krytarik on 2011-05-01
I want to clear up that session option matter a little:

1.) There is a system-wide default setting, that comes into effect if the user who is about to log in didn't ever log in before. Those setting can be changed through the tool "Login Screen" (command: "gdmsetup") from inside the system, and is stored in the file "/etc/gdm/custom.conf".

2.) The user can change his session option at the login screen, after clicking at or entering his username, but before entering his password. Those option menu is called "Session" and is located in the middle of the bottom panel. What was chosen there at the last login is stored in the file "~/.dmrc" in the users home directory. If the password query at login is disabled, the user, of course, isn't able to choose an option. If you were indeed not able to choose an option there, that may have been because of the users OEM status, I don't know.

[IMG]http://img59.imageshack.us/img59/8084/loginoptions.png[/IMG]

---

### Post by bcz on 2011-05-01
Nice post Krytarik

It would be useful if this option always appeared, rather than only the first time a user logs in.

In my case, until I logged in to 11.04, I was unaware that the desktop would be simplified to the extent that I wished it had been left the way it was.  In earlier releases  (10.04 with latest patches) the option is always available.

Had this not been changed in 11.04,  I would not have lost all my work since the last backup.

Looks like all my serious development work was backed up.

I will set this thread as solved.  Thanks for all the feedback

---

### Post by Krytarik on 2011-05-01
> **bcz said:**
> 
It would be useful if this option always appeared, rather than only the first time a user logs in.

Just to clarify, at least for usual users those option is *always* available; whether they see it is another question.

Glad that you didn't lose too much precious data!

---

