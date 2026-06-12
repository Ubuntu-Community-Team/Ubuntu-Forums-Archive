---
title: "Security Permissions"
date: 2005-11-29
forum: Desktop Environments
---

### Post by brummie on 2005-11-29
When i set up ubuntu i gave a username (jimbob for example) and password.
That then created a /home/jimbob

When i add users to the system they have permissions from standard to read the contents of the  /home/jimbob but jimbob does not have permission to read their files. 

Where have i gone wrong? I just lost a whole load of files because of this and would like to fix it before anymore go missing.:(

---

### Post by aysiu on 2005-11-30
Are they in the jimbob user group?

---

### Post by nocturn on 2005-11-30
[QUOTE=aysiu]Are they in the jimbob user group?[/QUOTE]

Is Jimbob in their user groups?

---

### Post by brummie on 2005-11-30
No. just checked.

According to jimbob folder permissions they had access.
Cant remember what they were as  i have changed them straight awaw think it was 755.

Can anyone else check theirs? 

This wouldnt have anything to do with /home being mounted on a different partition would it?

---

### Post by tomwell on 2005-11-30
Brummie,

Here is a bit of info on file permissions...:

[http://www.linuxcommand.org/lts0070.php#file_permissions](http://www.linuxcommand.org/lts0070.php#file_permissions)

its very interesting, and will also let you know what 755 is... + the permissions  you need to allow what groups or users you want to allow to use jimbob's files...

Peace

Tom

---

### Post by brummie on 2005-11-30
I know what the permissions are (though will read that) just would like to know where it went wrong if at all possible.

---

