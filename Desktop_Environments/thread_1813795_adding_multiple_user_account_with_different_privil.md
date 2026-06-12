---
title: "adding multiple user account with different priviliges"
date: 2011-07-28
forum: Desktop Environments
---

### Post by madeel on 2011-07-28
I have a desktop which has both windows and ubuntu. I want to add some users in ubuntu, say Me (first user),B and C. 

i) Certain folders should remain inaccessible from windows partition.

ii)Me should be able access both B and C home folder, but not otherwise.

iii) user B can access user C, but user C cannot access user B.

Thanks.

---

### Post by SlugSlug on 2011-07-28
I use setacl for stuff like that 

setfacl -m -R u:me:rwx /home/b
setfacl -m -R u:me:rwx /home/c
setfacl -m -R u:c:rwx /home/b

---

### Post by SlugSlug on 2011-07-28
think on newer version of buntu u need to apt-get install acl   first

& also edit /etc/fstab to have acl on end of line
eg
UUID=lotsofnumbers /home           ext4  defaults,acl

---

### Post by tom4everitt on 2011-07-28
If you don't want to use access list (for some reason, if there is a reason), you should also be able to achieve the same thing with groups. 

Let me just quickly spell out the idea for two users:

User A has primary group A, user B has primary group B (that's the default when you create the users). But then you add user A to group B. 

B's home folder will be owned by group B, of which A is a member, so A will have access. And A's home folder will be owned by group A, of which B is not a member, so B will not have access. (Given the right permissions are set, of course.)


This is just the general idea, let me know and I'll spell out the details and the exact commands etc. for you.

---

### Post by madeel on 2011-07-28
Thanks for valuable help. 

The idea of defining defining different groups seems much cleaner. I would like to give it a try. Yes, please spell it out. 

I don't have any reason for not using acl. It seems that acl gives more control but it is bit technical at first. I may end up using it in future. 

Lastly, how can we make some, not all, folders inaccessible to window user. For example, I log in to windows and can access ubuntu partition.But I want few folders remain inaccessible as the grouping done as above would not be recognized by windows.

---

### Post by tom4everitt on 2011-07-28
Here's the details for the group solution:

By default, you create 3 users, A, B and C:

user A is in group A, primary group A
user B is in group B, primary group B
user C is in group C, primary group C

We want to change that to:

user A is in group A, B and C, primary group A
user B is in group B and C, primary group B
user C is in group C, primary group C

It is pretty straightforward to do this from System->Administration->Users and Groups. So that part is pretty easy. (The command 'groups A' will tell you what groups A belong to.)


You also need to make sure the respective home folders have the right permissions. They should all have something like rwxr-x--- (readable, writable and executable by the user himself, readable and executable by users in the same group, unaccessible by other). 

Code:
```
cd /home
sudo chmod 750 *
ls -l

```

The last command will just show the set permissions.

(Notice though that this is not super safe, since the files inside the home folders may still have permissions letting anyone see them, so a clever user may be able to use that somehow. I don't know how big the risk is though - and I guess one could argue that that is every user's own responsibility. But changing permissions for all files in the home directories, plus changing the default somehow, would make it safer.  I'm not confident enough to give you detailed instructions on how to do that though.)

Encryption is probably what you want for non-Windows-visibility. Not my topic either unfortunately.

---

