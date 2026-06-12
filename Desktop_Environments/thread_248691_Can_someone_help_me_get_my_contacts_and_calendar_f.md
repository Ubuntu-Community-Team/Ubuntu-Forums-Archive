---
title: "Can someone help me get my contacts and calendar from outlook to evolution?"
date: 2006-09-01
forum: Desktop Environments
---

### Post by Aggienator on 2006-09-01
Can any one help? I have searched and googled. I have tried outport, but end up with very scrambled addresses! I have tried exporting to a comma separated text file, then importing to evolution, but the importer hangs and doesn't respond :sad: . I really want to move full time to Linux, but the hundreds of contacts in Outlook is a major deterrent.

My evolution version is 2.6.1 and Outlook 2003

Thanks for any assistance

---

### Post by Scunizi on 2006-09-17
I have the same issue but I'm using Outlook 2000.  The general rule is go from outlook to thunderbird then to evolution after exporting the data from thunderbird.  I'll be trying that again shortly.  The other issue is with the Catagories.  I have apx 15 catagories and none of them are mapped in either thunderbird or evolution.  Quite a pain.](*,)

Edit: If only evolution had a data mapping portion then we could use a TAB delimited format from just about anything!

---

### Post by Aggienator on 2006-09-18
> **Scunizi said:**
> I have the same issue but I'm using Outlook 2000.  The general rule is go from outlook to thunderbird then to evolution after exporting the data from thunderbird.  I'll be trying that again shortly.  The other issue is with the Catagories.  I have apx 15 catagories and none of them are mapped in either thunderbird or evolution.  Quite a pain.](*,)

Edit: If only evolution had a data mapping portion then we could use a TAB delimited format from just about anything!

Does Thuderbird manage teh full contact data (apart from categories) or does it only do the email address?

---

### Post by tlayton_at_work on 2006-09-18
I used the "readpst" package in the Ubuntu repositories.  It's a command line tool so you'll need to check the man page.

Worked like a champ on my Outlook XP .pst file for both Evolution and KMail/Kontact.

---

### Post by Scunizi on 2006-09-18
Great tip.  It's the first time I've ever seen that program mentioned.  I gave it a try using

mark@mark-desktop:~/Desktop/Outlook$ readpst -qwr Outlook.pst
debug_fp is NULL
cannot open PST file. Error
debug_fp is NULL
Error opening File

and also

mark@mark-desktop:~/Desktop/Outlook$ readpst -qwr Outlook.pst
debug_fp is NULL
cannot open PST file. Error
debug_fp is NULL
Error opening File
mark@mark-desktop:~/Desktop/Outlook$ readpst -qor ~/mark/Desktop/Outlook Outlook.pst

You can see that nothing happened.  Any ideas?  

Does it need to run sudo.  I also just copied my PST file directly from the NTFS partition (a little over 500mb) and checked the permissions.  Everything looked ok.

---

### Post by Scunizi on 2006-09-18
Sorry for the double post.  I tried again realizing I was using the captial "o" for Outlook instead of a small "o" and things began to happen.:-\" 

  The only thing I did different is to ad -cv to the commands which sets the method of output for the contacts. The "v" is for vCard type.  I found this command by typing readpst -h.  

When I import into Evolution it recognizes it as a vCard and buzzes and whurs.  When done I looked at the contacts and Yuck! what a mess. Nothing was put into the right fields.  Maybe it's just because I'm using Outlook 2000 instead of something newer... or older.  There've gotta be differences between some of the Outlook PST files.

---

### Post by danderson3 on 2006-09-18
check out 
[http://www.scheduleworld.com](http://www.scheduleworld.com)
and
[http://engtech.wordpress.com/2006/08/11/the-holy-grail-of-synchronization-how-to-synchronize-microsoft-outlook-multiple-locations-google-calendar-gmail-ipod-and-mobile-phone-with-funambol-scheduleworld/](http://engtech.wordpress.com/2006/08/11/the-holy-grail-of-synchronization-how-to-synchronize-microsoft-outlook-multiple-locations-google-calendar-gmail-ipod-and-mobile-phone-with-funambol-scheduleworld/)

---

### Post by la3875 on 2006-09-23
I had no problems recently with my contacts, but I still can't figure out the correct steps for getting my Outlook calendar into the Evolution calendar. Like Scunizi, if a simple step for this task can be found, I'll be completely hooked! :???:

---

### Post by Aggienator on 2006-09-23
> **la3875 said:**
> I had no problems recently with my contacts, but I still can't figure out the correct steps for getting my Outlook calendar into the Evolution calendar. Like Scunizi, if a simple step for this task can be found, I'll be completely hooked! :???:

In the end I bought Progression Desktop which does seem to have done the job OK.

---

### Post by la3875 on 2006-09-29
Are you happy with that solution and was it fairly painless? THanks for posting.

---

### Post by Aggienator on 2006-09-29
> **la3875 said:**
> Are you happy with that solution and was it fairly painless? THanks for posting.

It's a bit of a "sledgehammer to crack a nut" in that it offers to move all sorts of desktop setting as well as Outlook. It did work for me, though it took three attempts to generate the necessary file in Windows, not really sure why, first two attempts ran for ages and produced only a .part. Third time ran really smoothly and quickly produced what was needed. I did contact their support desk, who responded within 24hours, but by then I had run the third attempt and everything had worked, so never found the problem :confused: .

Good Luck!

---

