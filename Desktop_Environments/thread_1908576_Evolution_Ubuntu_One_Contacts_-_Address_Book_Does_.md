---
title: "Evolution Ubuntu One Contacts - Address Book Does Not Exist"
date: 2012-01-13
forum: Desktop Environments
---

### Post by whatdoyamean on 2012-01-13
Hi All,
just wanted to post a fix. After many hours of searching the web, multiple re-installs of certain apps etc this is what resolved my issue with evolution.[I][COLOR=Red]

Read edit at bottom of page. Not fully resolved.[/COLOR][/I]

I am running:

[LIST]
[*]Ubuntu 10.10(maverick)
[*]Kernel 2.6.35-31-generic
[*]Gnome 2.32.0
[*]Evolution 2.30.3
[*]Evolution-couchdb 0.5.0-0ubuntu1
[*]Couchdb 1.0.1-0ubuntu3
[*]Desktopcouch 0.6.9b-0ubuntu1.1
[/LIST]

I followed the procedure to copy all contacts to Ubuntu One from my Personal Contacts. Got a few errors which were normal ( could not add contact ) but most were transferred.

Then Evo spat the dummy. Got the message, evolution address book has unexpectedly quit? Then Evo would shutdown.

Restart Evo, then try to access Ubuntu One contacts and I would get the error message: The address book does not exist?

I would check _./local/share/desktop-couch/couchdb.html_. Open this file in Mozilla. There was data in the _contacts.couch_ database. Tried deleting this and recreating it. No difference. Tried numerous things, reinstall couchdb, reinstall evolution-couchdb. Doing these things did not resolve the issue.

Tried the reset contacts database as per: [https://wiki.ubuntu.com/UbuntuOne/ResetCouch](https://wiki.ubuntu.com/UbuntuOne/ResetCouch)
This did not work. Delete local went ok but could not delete the remote db. Error was does not exist/could not be found or need to input a URL?

After this it did temporarily work, so I thought just add one contact at a time (maybe the mass transfer of contacts - 656 of them - is corrupting the contacts.couch or couchdb?) When I got to 10. The same thing occurred. The pressure is building by this stage.

But then mysteriously, I find these contacts have been synced to my Ubuntu One account online? But I cannot access it locally through Evolution. Remove, reboot, re-install Evo. Still no go.

I found the following link: [_http://www.freedesktop.org/wiki/Specifications/desktopcouch/Documentation/Troubleshooting_]("http://www.freedesktop.org/wiki/Specifications/desktopcouch/Documentation/Troubleshooting")
 I verified that Avahi was running in processes. There was no instance of Desktopcouch User Authentication in >System>Preferences>Passwords and Encryption Keys>Passwords.
I did the following and the thorn in my side was finally removed(which is also contained in the link above)! (NOTE: I had no _beam.smp_ service running, only _beam)_

**Killing and restarting desktopcouch**

 To re-start desktopcouch from scratch, do the following, in a terminal window: 

[LIST=1]
[*]_killall beam.smp_ - this will kill any existing desktopcouch processes. (Note: **do not** do this with sudo!) If this says beam.smp: no process found, then do _killall beam_ instead.
[*]_rm ~/.config/desktop-couch/desktop-couchdb.ini_ - this will remove the desktopcouch configuration file, which will then be re-generated. (This will *not* lose any data stored in desktopcouch, do not worry.)
[*]_dbus-send --session --dest=org.desktopcouch.CouchDB --print-reply --type=method_call / org.desktopcouch.CouchDB.getPort_ - this should restart desktopcouch. You can ignore messages printed by this command
[*]_xdg-open file:///home/YOURUSERNAME/.local/share/desktop-couch/couchdb.html_ - open the bookmark file, which should then correctly take you to your desktopcouch web interface
[/LIST]
I hope this helps someone out there resolve their headache sooner that what it took me to resolve.

But it now works and is stable. Go Ubuntu!:P

[I][COLOR=Red]Guys, I have come across one more thing.

I cannot edit or delete contacts from the local Ubuntu One Contacts list. 

I can add more contacts by copying them from Personal Contacts to Ubuntu One, and they do get propogated to the online contact listing.

Any edits/additions performed online get propogated back to the local database.

If anyone could offer any advice to get full stable functionality would be much appreciated. Hopefully this will get resolved properly with future updates?[/COLOR][/I]

---

