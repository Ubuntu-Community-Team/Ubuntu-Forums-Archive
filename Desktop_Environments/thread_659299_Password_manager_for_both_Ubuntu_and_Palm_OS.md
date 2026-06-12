---
title: "Password manager for both Ubuntu and Palm OS?"
date: 2008-01-05
forum: Desktop Environments
---

### Post by beachedwhale on 2008-01-05
On Windows, I've used Turbo Passwords to manage a password database on both Windows and Palm OS.  Its simple enough... there's a Palm OS app and a Windows app.  You can view/edit/delete your passwords on either device, and sync to make the databases the same.  It stores more than just passwords, also account info, credt cards, whatever you want.  Both sides encrypt, but that's not a required feature because I have separate encryption software on both sides (TrueCrypt for Windows/Linux and Teal Lock for Palm OS).  I want to move further to Ubuntu but I'll really miss Turbo Passwords... its a terrific product.

How can I do this in Ubuntu 7.10?

The KeyRing plugin of jpilot is awful and has no import feature.  I don't ask for much except to be able to import a properly arranged .CSV file.  I have too much existing data to enter it all by hand.  Maybe I could use it if someone knows how to import.

I looked into KeyPassX, but the Palm OS app it uses is KeyRing, and it has some kind of converter from KeyPass to KeyRing.  I need to be able to sync both ways, and seamlessly.

Any ideas?

---

### Post by beachedwhale on 2008-01-05
I've done more searching, still nothing.  I find lots of great apps that run either on Linux or on Palm OS, but not both.  You'd think it'd be obvious for anyone writing a Palm OS app to write a desktop app as well -- I can edit my tasks, calendar entries, notes, contacts and emails on both and by default, so why not passwords?

To be fair, such software is almost nonexistent on Windows as well.  Turbo Passwords is the only one I had been able to find, and now I just found a second one called SplashID. But, neither have Linux versions of the desktop apps.

---

### Post by simoncifer on 2008-04-14
I know it's probably too late, since your post was in January.  But since I just spent a weekend looking for a solution for the same problem also, I hope others can use what I find out and don't have to waste too much of their time:

Basically, there is no complete package that could sync passwords stored on Linux Desktop with passwords stored on PalmOS.

The only possible way I find out is to install "Keyring for Palm OS" on your Palm Pilot, then use one of the software listed under "conduits" on "Keyring for Palm OS" webpage to edit a copy of the database file ("Keys-Gtkr.pdb"), then copy this new version of the database file back to Palm Pilot's RAM.

It seems that there is a converter to get a KeePassX database to "Keyring for Palm OS" database, as listed under "conduits".  It seems to be an open-source Java program called "KKConvert".  And since KeePassX is in the Ubuntu repository, it can be installed via apt-get or synaptic.

I haven't tried that, I just used one of the Java programs to open "Keys-Gtkr.pdb" to see if it works.

Another way is that if your Palm Pilot support Java, maybe there is a Java password manager package out there. like KeePassX/"KeePass for J2ME" or "MobileKnox and DesktopKnox".  I don't know about those, I haven't tried those myself, since my palm doesn't support Java.

---

