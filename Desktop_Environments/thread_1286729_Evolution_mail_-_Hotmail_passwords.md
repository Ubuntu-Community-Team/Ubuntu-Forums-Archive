---
title: "Evolution mail - Hotmail passwords"
date: 2009-10-09
forum: Desktop Environments
---

### Post by paul kinell on 2009-10-09
Hi all, I recently changed over to Evolution mail from Thunderbird, the setup, whilst a bit fiddly, presented no real problems and at the end of it everything worked.
The problem began with the recent scare over email account details published to a website. So I thought --- it's new passwords time!
Onto the webmail sites Hotmail and Google, via a browser and change passwords. I changed from a 15 character lower case alpha numeric to a 25 character all ASCI, logged out and then back in to test and all worked ok.
I then fired up Evolution mail to update with the new info, Google worked ok but Hotmail ---- nah! it wouldn't accept the new passwords, gives this message:

"Error while Fetching Mail. Unable to connect to POP server pop3.live.com. Error sending password: Resource temporarily unavailable"

No setting had been changed other than the password.

Test--
Google + new 25 char pass via browser    = works ok
    Google + new 25 char pass via Evolution     = works ok
    Hotmail + new 25 char pass via browser     = works ok
    Hotmail + new 25 char pass via Evolution = does not work!?
    
Tried a reinstall of Evo + all the bits, no difference.

Very frustrating!!!!

As a last effort before junking Evolution and going back to Thunderbird I went back to Hotmail via the browser and changed the password back to the old one, tested it ok; then I fired up Evo and enter the old pass ----- SUCCESS!!! ----- it works.

Conclusion--
After a bit more testing it seems that a password of more than 15 characters sent via Evolution to Hotmail fails, 15 chars or less ok. Strange no!

So my new password for Hotmail = 15 random ASCI characters and that works.

Is this Microshaft clicking about as I've heard they do, or an Evolution mail thing; or is it me having just enough computer nouse to muck thing up, anyone else had/have this problem?;)
Hope this helps someone.

---

### Post by donato roque on 2009-10-10
Evolution stores/saves your account password in Seahorse.  You will find it in Application>Accessories>Encryptions and Password keys.  Now I'm guessing here that Seahorse is still keeping the old password even after you've given the new passwords to Evolution when you were prompted for it.

For me the quickest way to do this is to delete the folders in Seahorse.  Just give your login password and delete the folders then close the application.

The next time Evolution opens it will prompt you for the account password, make sure you ticked the remember my password option in the pop up window.  Seahorse will save the new passwords.

---

### Post by Simon Jexter on 2009-11-12
I've gotten a similar error setting up my Evolution for the first time... I'm running 9.10 64 bit, trying to get hotmail set up.  I can receive fine, but sending i get this error:

DATA command failed: resource temporarily unavailable

I tried changing the port... a few guides suggested this, and I tried the two i found listed, but either they don't work at all, or (as with the :587 extension) return the above error.

Any ideas?  You people are amazing - thanks in advance for any help!

---

### Post by pataphysicianu on 2009-11-24
> **paul kinell said:**
> 

Conclusion--
After a bit more testing it seems that a password of more than 15 characters sent via Evolution to Hotmail fails, 15 chars or less ok. Strange no!

So my new password for Hotmail = 15 random ASCI characters and that works.

Is this Microshaft clicking about as I've heard they do, or an Evolution mail thing; or is it me having just enough computer nouse to muck thing up, anyone else had/have this problem?;)
Hope this helps someone.

My hotmail password is 17 characters and works fine in evolution.  I would say it's a hotmail problem, their pop3 server is really flaky, I have another mail app that constantly has problems with hotmail, and I have a large number of different email accounts of various types, pop3 and imap, thay all work fine it's always hotmail that acts up. It took me awhile for my other mail application to accept the hotmail password, but it finally did.

My feeling is that MS doesn't care about really supporting the pop3 service, I think outlook and outlook express access hotmail though a different imapish means, so the only people forced to use pop3 are people MS doesn't really care that much about.

---

