---
title: "Google address book no longer works in Evolution"
date: 2009-03-26
forum: Desktop Environments
---

### Post by atombuilder on 2009-03-26
I changed my Google account password, and as expected the Google address book in Evolution no longer works, but I can't figure out how to configure Evolution to use the new password. Email works fine... just the address book does not.  

I was able to set up the address book on another Ubuntu machine with no problem, using my new Google account password.

I've tried everything, including uninstalling (complete) Evolution, deleting the .evolution folder, and then reinstalling it... that did not wipe out my Evolution account and address book settings so that did not solve the problem.

So two questions:
- how to change the password Evolution uses to connect to the google address book
- how to completely expunge an address book from Evolution

---

### Post by jwh400 on 2009-03-26
Try going to your Evolution preferences and unchecking 'Remember Password' in both send and receive settings then click 'OK'. Close and restart Evolution.  Send yourself an email and hopefully there will be a prompt for a password and you can enter your new one when sending and receiving. You can elect to have the new one saved at the prompt.

---

### Post by atombuilder on 2009-03-27
Thank you for the idea... tried it and unfortunately did not work (I was not prompted for a new password).  I unselected both the send and receive 'remember password' checkboxes, restarted Evolution, sent myself an email message and was never prompted for a new password.  I restarted my machine (in case there is an evolution daemon running) as well.

Other than the .evolution folder, do you know where Evolution stores its settings?  I also tried uninstalling Evolution and deleting the .evolution folder, then reinstalling and it remembered all of my account settings, so Evolution is storing that stuff somewhere else.

---

### Post by jwh400 on 2009-03-27
The directory you may be looking for is in usr/share.
I would think that by deleting this directory you will have to do a complete set-up of Evolution. Hopefully someone can advise you further on this.

---

### Post by tgm4883 on 2009-04-15
> **jwh400 said:**
> The directory you may be looking for is in usr/share.
I would think that by deleting this directory you will have to do a complete set-up of Evolution. Hopefully someone can advise you further on this.

No, that seems like a bad idea (and wouldn't fix the problem)

The password is kept in gnome keyring.  Go to Applications > Accessories > Passwords and Encryption Keys and go to the passwords tab.  Look for the login entry that start with google:// If you have multiple of these, you should be able to right click on it and click properties, go to the details tab and find out if the application is Evolution.

If it's the right key, then just delete it, you should be prompted for a password next time you go to that address book in evolution.

---

### Post by filiatra on 2009-05-07
I had exactly the same problem and deleting the entries from the keyring did the job. Thank you !

---

### Post by rw2308 on 2009-06-22
I too had a similar problem that is now resolved, thanks to this thread, by deleting an incorrect password from keyring manager.  My Google address book would not load, even if I deleted and created a new one. 

Evolution could be more helpful with error messages - such as reporting an incorrect password or at least deleting the password when the address book is deleted.

---

### Post by pupfishdesign on 2009-10-03
Background -- I did not change any google passwords.  My evolution on two separate machines stopped accessing my gmail address book after working flawlessly.  I'm having a similar problem as described in this thread.  Unfortunately ridding my keyring of the google address book password then re-entering at the prompt does not solve the problem.  All I get is the original error message: 

Error loading address book.

This address book cannot be opened.  This either means that an incorrect URI was entered. or the server is unreachable.

Detailed error message: Other error.

Any thoughts on what to look at next?

Thanks...

---

### Post by ubuntab on 2009-10-11
> **tgm4883 said:**
> No, that seems like a bad idea (and wouldn't fix the problem)

The password is kept in gnome keyring.  Go to Applications > Accessories > Passwords and Encryption Keys and go to the passwords tab.  Look for the login entry that start with google:// If you have multiple of these, you should be able to right click on it and click properties, go to the details tab and find out if the application is Evolution.

If it's the right key, then just delete it, you should be prompted for a password next time you go to that address book in evolution.

just a short note to say i had the same problems and used the solution above and all is back to normal. thanks everyone!!

---

