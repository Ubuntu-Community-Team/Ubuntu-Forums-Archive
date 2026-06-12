---
title: "Switching Email Clients.. (TB to Evo)"
date: 2006-09-27
forum: Desktop Environments
---

### Post by yawnster on 2006-09-27
Howdy guys/gals,

Ive been using Thunderbird since I managed to move my SMTP account over from my Windows partition.. However looking at Evolution I feel its a far better solution for my needs.. The calendar and tasking features are what I have been craving but havent found with Thunderbird as yet..

Just wondering if anyone knew of a guide to transfer a Thunderbird profile over to Evolution? 

Thanks alot guys/gals.. Yawnster

---

### Post by yawnster on 2006-09-28
Im not sure on the rules on bumping.. But here goes..

Yawnster

PS.. I searched for this problem multiple times with no success.. :(

---

### Post by dcstar on 2006-09-29
> **yawnster said:**
> Im not sure on the rules on bumping.. But here goes..

Yawnster

PS.. I searched for this problem multiple times with no success.. :(

As far as I'm aware Thunderbird uses the same "mbox" format files as Evolution, so it may just be a case of copying them to the appropriate places in your .evolution folder.

---

### Post by gvgerman on 2006-09-29
I've made the switch over the past couple days.

First, make a new mail "account" in Evo.  I don't know if it is possible to import the profile. You'll have to do some digging for this.  If you have specific server ports, use Evo help to learn how to specify the port (easy instructions therein).

Evolution can import all the data files from Tbird, i.e.- cal, task, & email (cal & task if you are using the Lighting extension for Tbird).  Copy your Tbird data source files to a new folder in a Fat32 partition.  Then use import in Evolution pointing at each file (singularly; i.e.- import 1 file at a time) from the Fat32 partition folder.  Note that for the email data files, the *.msf extensions are not data; the file w/o the extension is the data file.  Also note (if using Lighting) the calendar data file can be imported in 2 ways: 1 for tasks a second time for the calendar data.  If you are using Lighting you'll have to import the calendar data twice; Evo will ask if you want to import the data as calendar information or task information.

Evo notes the Win file extension and translates the data to the appropriate Evo format.

If you have tons of mail folders in your Tbird "archive", you'll have to import each one one-at-a-time into Evo.  If this is the case, you might want to consider consolidating some of the folders in Tbird before you copy them to the Fat32 partition.

Everything went smoothly for me.

---

### Post by gvgerman on 2006-09-29
Re-read your orig post and note you are now using Tbird in Ubuntu.

Therefore, copy the Tbird data files to a new folder at Home. 

You'll need to copy the data files to a folder as the Ubuntu Tbird files are likely in a hidden folder and Evo has no option to point to hidden folders / files during the import process (at least that I could find).

Hope this helps.

---

### Post by yawnster on 2006-09-30
Aha, thanks for the excellent advice.. Worked a treat..

Just for anyone thats wondering, contacts can be switched by exporting them in ldif files and then importing them for each address book you have..

Thanks again gvgerman and dcstar

---

