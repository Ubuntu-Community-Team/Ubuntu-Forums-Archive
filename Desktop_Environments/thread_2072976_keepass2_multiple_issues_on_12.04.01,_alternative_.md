---
title: "keepass2 multiple issues on 12.04.01, alternative passwrord manager?"
date: 2012-10-18
forum: Desktop Environments
---

### Post by jhtibbs on 2012-10-18
I'm looking for a password manager and based on a bit of research I decided to try keepass2.

I started off with the keepass 2.18 which is current version in the standard repositories.

Issues:

1) default font hides characters in entry fields such as that for passwords. No big deal,
I switched over to courier.

2) When keepass brings up a window for a new entry I can't type in the first field, even though the window has focus and the blinking cursor is sitting there in the first field looking like it is ready to go. I have click the mouse on that field in order to get started.

3) For my first database I used a weak master password which I confirmed by viewing the password in plain text. I did not use a key file. I entered a couple of entries in to the database, saved it, and then exited keepass.  I then restarted keypass but when trying to load the database I get a popup with:

"The composite key is invalid"

Yep, I made sure I used the same password. Ok, start new DB.

I tried to import the database in to a new database using fix/recovery mode but that did not seem to work. keepass gave no feedback on the success/failure of the imports. 

After doing a bit of research I went ahead an upgraded to version 2.20.01 which is available via PPA. While exercising this version ....

4) I tried to print the database and selected "print preview". This generated an error popup with the following message:

"The .Net framework/runtin under which KeePas is currently running does not support this operation."

:)

I exited out of the popup and when back to the print window. All buttons were greyed out. Furthermore, the "defunct" popup retained keyboard focus. The only thing I could do was log out of ubuntu to recover.

I'm posting this in the hopes that the developers or other users will find the information useful.

I am looking to try another another password manager. Suggestions welcome.

Environment: 32-bit desktop with latest updates running on top of VMware Fusion 5.0.1 Pro.

---

### Post by Yumi on 2012-10-18
I used keepass2 on 12.04 without problems. Now I am on 2.19 in Qantal (or however you spell it) and again no problems.

Michael

---

### Post by jhtibbs on 2012-10-18
> **Yumi said:**
> I used keepass2 on 12.04 without problems. Now I am on 2.19 in Qantal (or however you spell it) and again no problems.

Michael

Thanks for the reply. It could be any number of things on my box. I can't explain the db password issue though: I could not make it happen again. I'm glad to hear it it working for you. I'm going to try a couple of others and maybe circle back to keepass for another go.

Jim

---

### Post by BelJoost on 2012-10-19
> **jhtibbs said:**
> I am looking to try another another password manager. Suggestions welcome.

I have been using KeePassX for a few years now. It uses the 1.x data format. So I am able to use it on Windows, my iPad and cellphone (j2me) as well.

Works great!

---

### Post by abexman on 2012-10-24
> **jhtibbs said:**
> I'm looking for a password manager and based on a bit of research I decided to try keepass2.

I started off with the keepass 2.18 which is current version in the standard repositories.

Issues:

1) default font hides characters in entry fields such as that for passwords. No big deal,
I switched over to courier.

2) When keepass brings up a window for a new entry I can't type in the first field, even though the window has focus and the blinking cursor is sitting there in the first field looking like it is ready to go. I have click the mouse on that field in order to get started.

3) For my first database I used a weak master password which I confirmed by viewing the password in plain text. I did not use a key file. I entered a couple of entries in to the database, saved it, and then exited keepass.  I then restarted keypass but when trying to load the database I get a popup with:

"The composite key is invalid"

Yep, I made sure I used the same password. Ok, start new DB.

I tried to import the database in to a new database using fix/recovery mode but that did not seem to work. keepass gave no feedback on the success/failure of the imports. 

After doing a bit of research I went ahead an upgraded to version 2.20.01 which is available via PPA. While exercising this version ....

4) I tried to print the database and selected "print preview". This generated an error popup with the following message:

"The .Net framework/runtin under which KeePas is currently running does not support this operation."

:)

I exited out of the popup and when back to the print window. All buttons were greyed out. Furthermore, the "defunct" popup retained keyboard focus. The only thing I could do was log out of ubuntu to recover.

I'm posting this in the hopes that the developers or other users will find the information useful.

I am looking to try another another password manager. Suggestions welcome.

Environment: 32-bit desktop with latest updates running on top of VMware Fusion 5.0.1 Pro.

I had used Keepass2 in Windows for a long time and was real happy with it. On Ubuntu 12.04 not so much. In particular I can't even access db files since the Master Password field is so problematic. I would also love an alternative or workaround? 

1. <I repro'd this easily with Ubuntu Keepass 2.18. I  created a new file and saved to the desktop. Set master password as  "test". When I close and reopen the same kdbx file, if I type in "text",  works fine. If I hit backspace after the last "t" and then retype "t",  then hit "ok" I get the keyfile error, even though no keyfile is set and  the password should be identical.> 
 from [https://sourceforge.net/projects/keepass/forums/forum/329220/topic/4503818](https://sourceforge.net/projects/keepass/forums/forum/329220/topic/4503818)

2. copy and paste into master password field does not work: [http://sourceforge.net/projects/keepass/forums/forum/329221/topic/5429832](http://sourceforge.net/projects/keepass/forums/forum/329221/topic/5429832)

3. KeepassX does not have file synchronization and it doesn't seem to have a nice history of passwords that Keepass2 has, that is a huge pain for some passwords because sometimes a password change doesn't "take", when you think it does

---

### Post by BelJoost on 2012-10-27
> **abexman said:**
> 3. KeepassX does not have file synchronization and it doesn't seem to have a nice history of passwords that Keepass2 has, that is a huge pain for some passwords because sometimes a password change doesn't "take", when you think it does
So what are you using now?

I must say I have grown fond of the following features:
* Interchangeable data files and support on Windows, Linux, iPad, Symbian and Android;
* Auto-paste on Windows and Linux;
* Strong password generation;
* Exclude look-a-like characters.

---

### Post by abexman on 2012-11-03
Im stuggling with KeepassX. Its a bit of a pain since I have multiple machines and files get locked out/read only and then I need to save new versions (and then need to compare password histories to determine which is newest). But it does work. Anyone else using something I don't know about that is open source? Lastpass is not bad, but I don't trust a 3rd party client plugin with my most sensitive stuff.

---

