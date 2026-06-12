---
title: "Strange issue when starting Chrome"
date: 2012-07-25
forum: Desktop Environments
---

### Post by netsurfau on 2012-07-25
This is one Ubuntu 10.04

This issue has been ongoing for around 12 months & thought I'd ask about it here first, in the hope
of a quicker response/solution than I'd probably get from Google.

Whenever I start Chrome a dialogue box pops up asking the following:

"Enter password to unlock your login keyring

The login keyring did not get unlocked when you logged into your computer."

Then has a space to enter PW with Cancel & OK buttons

Generally I just click on "Cancel" because, if I do try to enter my SU PW, I get 
an error message saying that the password is incorrect :confused:.  
This is especially confusing as obviously, I have no other passwords entered for system use.

Any ideas on how to get rid of this dialogue box & why I'm being told my password is incorrect?

---

### Post by netsurfau on 2012-07-26
I just upgraded my primary Desktop PC to 12.04 and now I'm getting the same "Unlock Login Keyring" window appearing as soon as the system finishes booting. And, of course my Admin PW is still the wrong password.

What the hell is this password the system is asking for & where do I find it.

Just to add to my frustration, the upgrade to 12.04 has killed my network connectivity from the same PC.  If I try to access the network settings, I get an error msg telling me, quote:***The System network services are not compatible with this version***.  

WTF??? This is ridiculous

---

### Post by beboylips on 2012-07-26
Run ```
 ifconfig 
``` and paste the output here. In terminal.

-beboy

---

### Post by netsurfau on 2012-07-26
@beboy: Posting to forum from my 'Windoze 7" PC.

Have an ip of 127.0.0.1 and yes I do know what that address means.

am try to sort out connectivity through a dedicated post in the "Installation & Upgrades" forum.  really want help with this login keyring issue in this thread.

---

### Post by netsurfau on 2012-07-26
Solved it.

Did some further searching of the forums using different search parameters & this thread:

[http://ubuntuforums.org/showthread.php?t=2010211&highlight=login+keyring](http://ubuntuforums.org/showthread.php?t=2010211&highlight=login+keyring)

Had a simple command line fix, so simple.

---

