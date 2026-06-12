---
title: "Evolution: contacts"
date: 2005-11-22
forum: Desktop Environments
---

### Post by dpack on 2005-11-22
I'm not seeing an "Evolution" thread to post this to so I figured this would be good enough. When I ran Windows I used ThunderBird for email. I exported my contacts out as an LDIF file and then imported into Evolution. Cool deal. Now, as I make changes to my contacts in Evolution I want to be able to export my contacts out for backup purposes. I only see an Import feature and no export feature. I have Google searched it and have found plenty of people asking the same question but no one answering it. I am running Evolution 2.4.1 and did find a "evolution-addressbook-export" command listed on the Net, but when I sudo that it doesn't recognize the command. How can I export my Evolution contacts?

---

### Post by cstudent on 2005-11-22
I haven't yet completely made the switch to Breezy. I'm planning on switching my main computer to it over the holiday weekend. Evolution in Hoary doesn't have an export feature. If all you want to do is backup your Evolution files you can open Nautilus and under the View menu (I believe) tell it you want to view hidden files. Find the .Evolution directory and you should be able to find your email and contact files which you can copy for a backup.

Bill

---

### Post by dcstar on 2005-11-22
[QUOTE=dpack]I'm not seeing an "Evolution" thread to post this to so I figured this would be good enough. When I ran Windows I used ThunderBird for email. I exported my contacts out as an LDIF file and then imported into Evolution. Cool deal. Now, as I make changes to my contacts in Evolution I want to be able to export my contacts out for backup purposes. I only see an Import feature and no export feature. I have Google searched it and have found plenty of people asking the same question but no one answering it. I am running Evolution 2.4.1 and did find a "evolution-addressbook-export" command listed on the Net, but when I sudo that it doesn't recognize the command. How can I export my Evolution contacts?[/QUOTE]
Try: **/usr/lib/evolution/2.4/evolution-addressbook-export**

(It isn't in a binary path directory)

---

### Post by dpack on 2005-11-22
I checked out **/home/.evolution/addressbook/local/system** and the **addressbook.db** and **addressbook.db.summary** are listed. I copied them out to the desktop. I then cleared my contacts in Evolution and then tried restoring them one or the other and then both but neither scenerio restored my Contacts when I opened Evolution back up.

So then I pulled up Terminal and tried **sudo /usr/lib/evolution/2.4/evolution-addressbook-export** after visually verifying the evolution-addressbook-export file existed in the path specified and got the following results: **(evolution:12522): evolution-addressbook-tools-WARNING **: Couldn't load addressbook (null)**

Any Ideas?

---

### Post by Zimmer on 2005-11-22
Don't know what you have done wrong. because I just upgraded to Breezy and in order to get my previous contacts I had saved the .db and .db.summary files.
I opened Evolution and created a Contact list with one name and then renamed the resulting .db files by tagging the extension with the word 'orig' and copied in my old .db and .db.summary files. It worked...
I even imported my old calendar by copying in the relevant .ics file.

check the file permissions and the extensions..
Use openoffice to open copies of the  .db files and check that there is some contact info there..just in case you managed to overwrite (longshot, I know)
Sorry can't be more help..

Zimm

---

### Post by dpack on 2005-11-22
Okay boys and girls. I found an easy way to export my contacts out of Evolution that is much easier than fighting with the attempts above that I never got to work. This way is fool proof and works every time.

1. Open Evolution and go to the Contacts section.
2. Press Ctrl+A to select all of your contacts.
3. Right-click on any one of the contacts and select **Save as VCard**
4. Pick where you want to save the **list.vcf** file and save.

You're done! ALL of your contacts are saved nice and tidy into that single VCF file. I cleared my contacts from Evolution and then imported that VCF file and, poof, there they all were.

I hope other people find this useful. Thanks for the assistance people!

David

---

### Post by cstudent on 2005-11-22
Excellent. Thanks for passing that on.

Bill

---

### Post by dcstar on 2005-11-23
[QUOTE=dpack]I checked out **/home/.evolution/addressbook/local/system** and the **addressbook.db** and **addressbook.db.summary** are listed. I copied them out to the desktop. I then cleared my contacts in Evolution and then tried restoring them one or the other and then both but neither scenerio restored my Contacts when I opened Evolution back up.

So then I pulled up Terminal and tried **sudo /usr/lib/evolution/2.4/evolution-addressbook-export** after visually verifying the evolution-addressbook-export file existed in the path specified and got the following results: **(evolution:12522): evolution-addressbook-tools-WARNING **: Couldn't load addressbook (null)**

Any Ideas?[/QUOTE]
Yes, **DON'T** use sudo - you are running a user based process.

---

### Post by dpack on 2005-11-23
[QUOTE=dcstar]Yes, **DON'T** use sudo - you are running a user based process.[/QUOTE]

Thanks, but I'm not using that process now. I found a better and easier way for everyone to do it. See my post above.

Thanks!

---

### Post by z_diver on 2006-11-18
> **dpack said:**
> Thanks, but I'm not using that process now. I found a better and easier way for everyone to do it. See my post above.

Thanks!
I know I'm a couple of years late but after having problems with my Personal addressbook I came across this thread and by right clicking the addressbook you can save as VCF straight away.  Still works great.  

This is the most simple and effective way to backup contacts in Evo.  Why don't they create a link to this feature under File > Export > Save contacts as VCF file?  Everyone looks there. It's a no-brainer!!!

---

