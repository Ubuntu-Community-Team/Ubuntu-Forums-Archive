---
title: "No Login or log out sound 9.04"
date: 2009-05-15
forum: General Help
---

### Post by Eupho on 2009-05-15
Hi

I wondering if the login and logout sounds will ever work again. i know the log out sound hasn't worked for a few releases now, but it is disappointing to  loose the login one now.

Is there any way to get them going?

I have worked around it a little by using .wav files and making sure i check the login sound box in system/administration/login window then the accessibility tab. This is a bit of a cheat really. 

If anyone has a better idea please help. It is only a small problem but it ust finishes of the presentation so well the the eye candy and sounds work as they should.

Other than this I love 9.04

---

### Post by dcstar on 2009-05-15
> **Eupho said:**
> Hi

I wondering if the login and logout sounds will ever work again. i know the log out sound hasn't worked for a few releases now, but it is disappointing to  loose the login one now.

Is there any way to get them going?

I have worked around it a little by using .wav files and making sure i check the login sound box in system/administration/login window then the accessibility tab. This is a bit of a cheat really. 

If anyone has a better idea please help. It is only a small problem but it ust finishes of the presentation so well the the eye candy and sounds work as they should.

Other than this I love 9.04

Login works for me, delete any (hidden) .pulse files/folders in your home and also reinstall all Pulse packages.

---

### Post by Eupho on 2009-05-16
Hi and thanks for your reply

I have done as you said but i still don't have the jungle drums. I deleted the .pulse file and went to synaptic and selected pulse audio and reinstalled it. 

when i check in system/preferences/sound I can here all the sounds fine.

if i check the sound in the system/admin/login widow/accessibility the test the sound it is like listening to static.

I am using Ubuntu 9.04 NBR on a Eee 1000H if that has anything to do with it. I have checked the eee user forum and there is no info there.

Thanks again
Paul

---

### Post by frankelr on 2009-05-16
Hi, If your sound hw acts like a usb sound card,
startup sounds don't work, because the drivers don't get loaded until after the "drums".  If this doesn't help ID your sound hardware, search for bugs or try other sound drivers besides pulse audio.

Bob

---

### Post by Eupho on 2009-05-19
Well there where just to many bugs.

I have gone with the eeebuntu version of 9.04 and it works fantastic. 

It is still Ubuntu to me.

---

