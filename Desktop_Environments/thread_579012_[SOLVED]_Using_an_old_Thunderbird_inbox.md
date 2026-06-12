---
title: "[SOLVED] Using an old Thunderbird inbox"
date: 2007-10-17
forum: Desktop Environments
---

### Post by CRCarl on 2007-10-17
All - 
   I have an old backup of an IMAP connected inbox from a job a couple of years ago. The path in the backup is \home\<me>\.thunderbird\lkdflsko9.default\ImapMail\<servername>\bunch of folders, including the 900MB mailbox file, INBOX. I created a new account in my existing Thunderbird profile, copied lkdflsko9.default\ImapMail\<servername>\bunch of folders into my working .thunderbird folder then changed the Local Directory path in the Thunderbird GUI. I thought that would do it, but no dice the Inbox is empty. 

   Any ideas on how to get to that data?

Thanks, 

Craig

---

### Post by TeaSwigger on 2007-10-17
Hello Craig, questions for your questions I'm afraid. Was this from a linux or windows install? 

Have you tried every folder? Tried installing an account you know works in order to ensure you have the method right?

---

### Post by CRCarl on 2007-10-18
Sorry - 
    Ubuntu 7.04 on AMD 64, Thunderbird 2.0.0.6.  I've moved other folders around to test the idea, those worked. 

Craig

---

### Post by TeaSwigger on 2007-10-18
Gah, can't seem to keep track of anything these days.

So let's see. First off be sure to only work with a copy so the the original old backup isn't altered until you're sure it's all set.

Thunderbird saves each accounts' mail boxes to two files in the bottom most directory (profile.folder/Mail/account) ; one has no extension and the other has .msf. The extension-less one contains the emails, in .mbox format. Worse comes to worse, look for something to import or convert email from the .mbox format files.

Again, was this old mailbox from a windows install or a linux install? If it came from windows, there are path changes to make in a file, prefs.js.

Has this old backup been added to your ~/.thunderbird/profiles.ini file? Take a peek at that file it's pretty simple.

Do you already have a folder with a .default suffix? If so try removing the other and see if that changes anything.

Geez I did a ton of searching a while back when I moved mine into linux, and succeeded in making it work, but you know I've forgotten most of it.

PS check the ubuntuzilla sub forum here, some great folks there are very knowledgeable about tbird.

---

### Post by Whiffle on 2007-10-18
I have a thunderbird addon that does this, although I can't find a download link for it.

ImportExportTools(Mboximport Enhanced) 1.3.0.1

if you can find a copy of that its easy to import them.

---

### Post by CRCarl on 2007-10-19
Looks like it used to be here - [https://nic-nac-project.de/~kaosmos/index-en.html](https://nic-nac-project.de/~kaosmos/index-en.html) but the site seems to be dead. 

Craig

---

### Post by TeaSwigger on 2007-10-19
Craig, maybe try Sylpheed-Claws-gtk2 - it does import mbox files and is in the repos. Can export the emails for Tbird from there or use Sylpheed-Claws if you want, it's a good email app itself.

---

### Post by CRCarl on 2007-10-19
I got it. I created a fake account then copied the old INBOX file over the new, empty one. Restarted Thunderbird, right clicked on the new Inbox, selected 'reindex' and it worked!

Thanks all

Craig

---

### Post by TeaSwigger on 2007-10-19
Wonderful Craig, and thanks for posting the results! If you would, mark the thread solved (see the thread tools link near top) to help others searching for mail box probs. :)

---

### Post by flx2000 on 2007-10-19
I had the same problem and I resolved it when I discovered my new Thunderbird was using ~/.mozilla-thunderbird instead of ~/.thunderbird folder.
Just moved (renamed) the old one to get it working with my usual profiles.

---

