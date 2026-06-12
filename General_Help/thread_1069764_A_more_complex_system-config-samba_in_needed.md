---
title: "A more complex system-config-samba in needed"
date: 2009-02-14
forum: General Help
---

### Post by Smjork on 2009-02-14
So far my search for a GUI administration tool of Samba lead me to just a few options. The best of those came out to be Webmin's Samba module.
The other one is GAdminTool, which looks good and yet not functional on the Ubuntu 8.10 system that I used for tests.
And this lead me to this kind of request for a more complex system-config-samba tool, to do the proper job out of the box, using no other 3rd party sotfware.

I mean, system-config-samba is ok for a very brief share but using it you won't be able to (or there are not explicit ways to):
- set up groups (as in samba user groups)
- set different permissions on different users (let's share a folder, give RW permissions to user Joe and user Jane while user Jack will he only RO privileges) The only thing system-config-samba does is set full ReadOnly or full ReadWrite on ALL the users specified in the users list of that particular shared directory ("writable=yes" and "valid users = John, Jane, Jack")
Not to mention other more complex samba settings...

So, as I said, I tried to set up proper rights on a test directory, using GAdmin tools. Just move user Jack to ReadOnly users of that directory. Everything looked good. I cound set up more parameters, including the permissions I wanted to. I could see the future smb.conf before saving and activating it. But activating it ruined the whole access to that directory.
Looking in the section dedicated to that test directory (in the new generated (and activated) smb.conf file, everything looked correct. The options, the syntax, were all correct. And yet that directory became unaccessible to any user.

I know that all these tools are not the direct responsability to Ubuntu since they have their own project devs working on, but I just feel that Ubuntu, which grew up as the most user friendly distro, should make a stronger stand on this issue.

I know, I know, the wish list is such a long one ... :-)
Still ...

---

