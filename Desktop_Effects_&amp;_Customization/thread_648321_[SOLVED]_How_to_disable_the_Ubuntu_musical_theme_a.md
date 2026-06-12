---
title: "[SOLVED] How to disable the Ubuntu musical theme at startup?"
date: 2007-12-23
forum: Desktop Effects &amp; Customization
---

### Post by berliita on 2007-12-23
How to disable the Ubuntu musical theme at startup? I don't want all my household and neighbors to know when exactly i log into my account.

---

### Post by kshane on 2007-12-23
> **berliita said:**
> How to disable the Ubuntu musical theme at startup? I don't want all my household and neighbors to know when exactly i log into my account.

To get rid of the startup music, **go to System >>Preferences >> Sound** and choose the Sounds tab.  Set all of the sound options to **No Sound**.  

Then go to **System>>Administration>>Login Window**.  Choose the Accessability tab and uncheck the sounds. 

You now have no startup sounds...

Kevin

---

### Post by berliita on 2007-12-26
Thanks.

---

### Post by n6k6t6 on 2008-02-16
This works!

Now I can restart my laptop in the library as often as I want!
But please, someone explain to me how can the login theme sound be disabled using 
command line/config files?  I tried setting 

SoundOnLoginSuccess=false    

in /etc/gdm/gdm.conf-custom, but that did not remove the sound.
Someone please explain!..

---

