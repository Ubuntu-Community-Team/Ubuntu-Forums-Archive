---
title: "How do I migrate thunderbird on windows to thunderbird on Ubuntu Linux?"
date: 2006-09-01
forum: Desktop Environments
---

### Post by solarwind on 2006-09-01
Hi all,

How do I migrate thunderbird on windows to thunderbird on Ubuntu Linux? I have thunderbird on windows with several accounts and would like to transfer ALL of the settings, profiles and mail to Ubuntu Linux. How can this be done?

All replies are much appreciated.
Thanks in advance!

---

### Post by aysiu on 2006-09-01
Copy C:\Documents and Settings\*username*\Application Data\Thunderbird to /home/*username*/.mozilla-thunderbird

Or, if you're using Mozilla's Thunderbird instead of Ubuntu's Thunderbird:
Copy C:\Documents and Settings\*username*\Application Data\Thunderbird to /home/*username*/.thunderbird

---

### Post by solarwind on 2006-09-01
Thankyou so much!

---

### Post by solarwind on 2006-09-02
Hmm. The incomming messages came in as usual, but when I try to send a message from either one of both my smtp servers, thunderbird keeps saying

"connecting to xxyyzz" when i compose a message and press send.

Note: I stored my passwords

Why might this be happening?

---

### Post by solarwind on 2006-09-03
Why is this happening?

---

### Post by aysiu on 2006-09-03
> **solarwind said:**
> Why is this happening?
I don't know. SMTP isn't my area of expertise. I just know how to copy over the settings in general.

---

### Post by solarwind on 2006-09-03
Yeah, but i cant SEND messages to anyone. I can only RECEIVE them.

---

### Post by aysiu on 2006-09-03
Any SMTP gurus out there who can help out solarwind?

---

### Post by solarwind on 2006-09-04
I doubt it has anything to do with smtp. I think something went wrong when I transferred my profiles. I'll try some experiments to confirm.

---

### Post by solarwind on 2006-09-14
I dont know if I have entered the right commands and chowned/chmodded properly.

Can someone please post the EXACT terminal commands (not just drag and drop konqueror like I did)? I tried chmodding and chowning but I didnt get very far.

---

### Post by outofnicks on 2006-09-14
I've moved thunderbird from one computer to another a few times, and always recreated the accounts anew then manually copied the contents of each of the folders in the Mail directory. The name of the directory for your Profile is always unique, so you should let Thunderbird create that instead of copying one over from a different system.
 I just noticed there is an Import feature under the Tools menu, maybe worth a try?
Have you checked your Account settings?

---

### Post by solarwind on 2006-09-15
Thanks I'll try that.

---

