---
title: "&quot;open with&quot; change"
date: 2007-05-07
forum: Desktop Environments
---

### Post by jimbo99 on 2007-05-07
I've tried to get this answered in #ubuntu but all I get is a mute response.

Under Edgy when I tried to change the default "open with" for .pdf files I was stuck. I couldn't seem to make the change.  I'd right click on the file.  I'd choose properties.  I'd select the "open with" tab.  I'd see two options "Adobe Reader" and "Document Viewer".  I'd TRY to select the "Adobe Reader" option to set it as the default but it would not change for me.  Nothing I could do would force it to change.

I did a "run" and entered gksu nautilus.  Then I traversed to the file.  Then I went through the above procedure and saw that I could change the default "open with" for .pdf documents.

The big problem here is that doing it with gksu only changes it for the root account.  It won't change it for all accounts.

I need some help here.  How do I force this to change to allow me, my regular account, to change the default "open with" for this type of file?

I've searched for answers to this before but found none.

I appreciate any help in advance.

---

### Post by jimbo99 on 2007-05-07
Oh, I forgot a few things.

First, this is not an Edgy install.  I bought a new 320gig drive and installed Feisty on it when it came out.  So this is a question in response to Feisty.  Even so, I still have my Edgy install which was upgraded to Feisty via the upgrade feature.  It also had/has the same problem.

Again, any help would be appreciated.

---

### Post by jimbo99 on 2007-05-08
OK, I found a solution tho why the issue exists is beyond me.

I was looking at another error regarding adding an application to the database for "open with" choices.  That error led me to someone that had a similar problem.  He spoke of a directory under my user home folder called:


.local


That directory had a series of other folders.

When I tried to change into the .local folder I received the message that permission was denied.

I then changed the permissions to that folder and the subfolders and then tried to change the default "open with".

This worked.

I can only wonder why I don't have rights to my own .local folder when only this account has accessed that folder.

---

