---
title: "Discussion - https://help.ubuntu.com/community/SambaActiveDirectoryDomainIntegrationS"
date: 2012-06-29
forum: Documentation and Community Wiki Discussions
---

### Post by Elfy on 2012-06-29
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/SambaActiveDirectoryDomainIntegrationScript](https://help.ubuntu.com/community/SambaActiveDirectoryDomainIntegrationScript)

Support threads should be posted in normal forums.

Thank you.

---

### Post by MartinChir on 2012-07-16
I get an error when running the script, can't find ".ICEauthority"  I have checked using root permissions "ls -l -a" and the file is not there...  Anyone with the same problem?

---

### Post by CorrupterTheLost on 2012-10-18
I too had this issue however it still allowed me to proceed under 12.04  Furthermore however i am now getting an error regarding when a user attempt to log in via SSH it failed to create his home folder and also kicked out an error 

```
Could not chdir to home directory /home/DOMAIN/ad_user: No such file or directory
groups: cannot find name for group ID 10008
```

And i believe that these issues are related.  Because this file does not exist it has something to do with this although my skill level is not good enough to determine what.  Furthmore if you have this file it was suggested that you
```
#chmod u+rw /home/$SUPER_USER/.ICEauthority
```
where $SUPER_USER change that to the SUDOER you used to join the ubuntu machine to the active directory domain.  Lastly  all things seem to be working thus far for me with the exception of new users home directory shares being automatically created.

I would like to change this automatic creation of this folder from its current location to a new location on a different volume and am not sure quite how to do that if anyone can suggest a solution.  Thank you in advance for all your help.

---

