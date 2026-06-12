---
title: "ubuntu post install script for thunderbird configuration"
date: 2011-12-31
forum: Desktop Environments
---

### Post by linux.girl on 2011-12-31
Hello,

I usually configure thunderbird and its add-ons via the  gui. I was wondering if all the add-ons configs can be done with a  script instead of gui, so that I dont have to manually configure each  computer in mass deployment scenario (I would like to add the  thunderbird configs to a post install script or something like that).  Also, same for firefox add-ons...possible?

Does anyone have experience with that?

Thanks in advance,

linux.girl

---

### Post by M1GEO on 2011-12-31
All the settings are maintained in a profile folder inside your home folder:  ~/.thunderbird/  and  ~/.mozilla/

We managed to clone email accounts by simply copying a generic folder over, so all the information required is contained within those folders. I would expect that you could edit these.

Maybe create a generic email account in Thunderbird, with a specific email address, and then grep the thunderbird directory for it; this would show up where these parameters are stored.

I suspect that someone else may have a much better idea of how these things can be done.

Just a few ideas :) Happy New Year.

---

### Post by BC59 on 2011-12-31
You can have synchronized accounts of Thunderbird in different computers or use Dropbox to store your account for safety.
[http://ubuntuforums.org/showthread.php?t=1896310](http://ubuntuforums.org/showthread.php?t=1896310)

---

### Post by linux.girl on 2012-01-03
Thanks for the suggestions!

@BC59 - not sure this is relevant for what I need. I dont need the same account in different computers, what I need is to do a mass deployment of at least 200 desktops where the basis is ready (i.e., generic thunderbird add-ons) and the rest I can do scripts for each user config).

The problem I have is that once I configure a computer "prototype" and clone it, I then have to log in the client with the new user...and once you log in with the new user, the cloned configs are not kept - because they were made under a generic user. 

What is possible is not to log in as a different user, but to log in with the generic user and then run a script from inside to change the username and hostname.

Thanks a lot in advance - any more ideas are more than welcome!!!!

linux.girl

---

### Post by Bobhuber on 2012-01-03
> **linux.girl said:**
> Thanks for the suggestions!

@BC59 - not sure this is relevant for what I need. I dont need the same account in different computers, what I need is to do a mass deployment of at least 200 desktops where the basis is ready (i.e., generic thunderbird add-ons) and the rest I can do scripts for each user config).

The problem I have is that once I configure a computer "prototype" and clone it, I then have to log in the client with the new user...and once you log in with the new user, the cloned configs are not kept - because they were made under a generic user. 

What is possible is not to log in as a different user, but to log in with the generic user and then run a script from inside to change the username and hostname.

Thanks a lot in advance - any more ideas are more than welcome!!!!

linux.girl
Firefox > FEBE backup utility - beta for TB also - should do exactly what you want

---

