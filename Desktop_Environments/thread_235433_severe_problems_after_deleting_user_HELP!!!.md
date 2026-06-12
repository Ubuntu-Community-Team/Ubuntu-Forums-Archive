---
title: "severe problems after deleting user: HELP!!!"
date: 2006-08-13
forum: Desktop Environments
---

### Post by morgan on 2006-08-13
i wanted to get rid of a user1 so i cleaned out his home dicectory,  logged in as user2 (who also has root clearence),  went to the user management deleted the user1 and his  group.
so far,so good.
after that weird things started to happen:
i couln't logon as su. doing so gives the following responce;
[INDENT]edith@Ziggy:~$ su
Password:
su: Authentication failure
configuration error - unknown item 'QUOTAS_ENAB' (notify administrator)
configuration error - unknown item 'NOLOGIN_STR' (notify administrator)
configuration error - unknown item 'ENV_HZ' (notify administrator)
configuration error - unknown item 'CHFN_AUTH' (notify administrator)
configuration error - unknown item 'CLOSE_SESSIONS' (notify administrator)
Sorry.
edith@Ziggy:~$
[/INDENT]so i rebooted;
to my surprise user1 is not gone and still can logon. trying the su command as user1 gives the same responce as described.

every task that needs root clearence is gone for both users! no more user management or update manager. even the icon in the desktop are gone (or i need some glases) 
the auto mounter is not functionig. cd's won't mount.  all sound is gone (it was working perfectly) including the default soundcard in the sound preferences.

so  i  tried to  reinstall with  the ubuntu-alternate-iso  (booting from cd is no problem  ) but when it comes to unpacking the kernel, there is  an error  whith the unpacking..  (i can  produce  the text if needed) 

can someon tell me what went wrong and how i can fix this


many thanks

---

