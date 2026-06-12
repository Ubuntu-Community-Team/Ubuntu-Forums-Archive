---
title: "Email"
date: 2005-11-11
forum: Desktop Environments
---

### Post by Mad Max on 2005-11-11
Hi All, 

New to Ubuntu and having problems with Pop Email - can receive but not SMTP send. Have all the usual settings as in GatesWorld XP. Any clues? 

Thanks
Mad Max

---

### Post by Ampersand on 2005-11-11
It may be that authentification for the smtp server is turned on when it's meant to be off (I've had problems with Thunderbird doing that by default in the past, might be the same with other email clients as well). Might be worth having another look through the server settings.

---

### Post by Mad Max on 2005-11-11
Sorry for the delay - still getting used to this. 

Thanks for the reply - do you know where in Evolution  the server settings are, please? Thx

---

### Post by majikstreet on 2005-11-11
[QUOTE=Mad Max]Sorry for the delay - still getting used to this. 

Thanks for the reply - do you know where in Evolution  the server settings are, please? Thx[/QUOTE]
Edit>>Preferences. Click on "Mail Accounts". Then select your account in the window. Then click "Edit". After that, you should have a window that pops up with a bunch of tabs. I believe the one you want is "Sending Email."


Good luck,
majikstreet (an evolution user xD)

---

### Post by Mad Max on 2005-11-11
Thanks Ampersand and Majikstreet. 

I've discovered that the answer lies in the SMTP setting. 

I was trying to use a Freeserve (now Wanadoo) Email account. It appears that Mail Servers are usually restricted to only allow mail to be sent out from their own Network. Since I have NTL Broadband, I changed the SMTP setting in Evolution from smtp.freeserve.com to smtp.ntlworld.com and my Outbox sent the Email straight away.

Ubuntu just got better for me.

Cheers

---

