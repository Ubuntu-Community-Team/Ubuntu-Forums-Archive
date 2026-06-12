---
title: "Thunderbird sync with Windows"
date: 2008-05-22
forum: Desktop Environments
---

### Post by allanlewis on 2008-05-22
Hi,

I use Mozilla Thunderbird on both Windows XP (Home, SP2) and Linux (Kubuntu Gutsy currently, will be upgrading to Kubuntu-KDE4 Hardy soon) to read my email using GMail's IMAP/SMTP access. This works fine, but I wish there was a way I could get both OSs to store the Thunderbird configuration and mailboxes in the same location. I tried this years ago with Dapper but never got it working. (I think Thunderbird just overwrote the files each time I ran it on either OS.)

If this isn't possible, is it possible to copy over the settings for an email account from one OS to the other? Basically, I'm asking if the files are in the same format and if the difference between line endings (i.e. LF or CR+LF) will mess it up.

Allan Lewis.

---

### Post by infecticide on 2008-05-22
Fortunatly for you, I have this setup and it works flawlessly!

What I've done is setup the mail in Windows the way I want it.   Then in Linux you need to open the ~/.mozilla-thunderbird/profiles.ini file and point the Path to the directory on your windows partition where your mail is setup.

Example profiles.ini:
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/media/sda1/Documents and Settings/username/Application Data/Thunderbird/Profiles/iragxn8l.default/


Some problems I've run into however are when updates occur in Linux but not in Windows.   The Windows Thunderbird refuses start stating that it couldn't update a file and gets stuck there in an endless loop.   This doesn't happen very often.

This same method can be used to link your firefox as well!

---

### Post by allanlewis on 2008-05-22
> **infecticide said:**
> Fortunatly for you, I have this setup and it works flawlessly!

What I've done is setup the mail in Windows the way I want it.   Then in Linux you need to open the ~/.mozilla-thunderbird/profiles.ini file and point the Path to the directory on your windows partition where your mail is setup.

Example profiles.ini:
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/media/sda1/Documents and Settings/username/Application Data/Thunderbird/Profiles/iragxn8l.default/


Some problems I've run into however are when updates occur in Linux but not in Windows.   The Windows Thunderbird refuses start stating that it couldn't update a file and gets stuck there in an endless loop.   This doesn't happen very often.

This same method can be used to link your firefox as well!

Thanks! Can you explain further the error you say you sometimes get? What do you do to get out of this? Do you just kill the process? And do you have any problems with Firefox using this setup?

Any other comments welcome.

---

### Post by kellemes on 2008-05-22
> **allanlewis said:**
> Hi,

I use Mozilla Thunderbird on both Windows XP (Home, SP2) and Linux (Kubuntu Gutsy currently, will be upgrading to Kubuntu-KDE4 Hardy soon) to read my email using GMail's IMAP/SMTP access. This works fine, but I wish there was a way I could get both OSs to store the Thunderbird configuration and mailboxes in the same location. I tried this years ago with Dapper but never got it working. (I think Thunderbird just overwrote the files each time I ran it on either OS.)

If this isn't possible, is it possible to copy over the settings for an email account from one OS to the other? Basically, I'm asking if the files are in the same format and if the difference between line endings (i.e. LF or CR+LF) will mess it up.

Allan Lewis.

Start Thunderbird like so .. (this works from Linux and Windows)
```
thunderbird -profilemanager
```
Create a profile that points to the profilefolder of the Thunderbird install on "the other os".

Doing this for years and it works fine..

---

