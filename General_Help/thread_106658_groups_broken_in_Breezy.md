---
title: "groups broken in Breezy?"
date: 2005-12-21
forum: General Help
---

### Post by DaveHartburn on 2005-12-21
Anyone got any ideas of a strange problem I have concerning groups? It looks like it may be broken.
I've got two users defined in the password file:
[FONT="Courier New"]55732:x:55732:100:Dave Hartburn,,,:/home/55732:/bin/bash
www-data:x:33:33:www-data:/var/www:/bin/sh
[/FONT]
The group 100/users is my primary group. I have also added a new group in /etc/group:
[FONT="Courier New"]wiki:x:1001:55732,www-data[/FONT]

Now if I create a directory, chown it to www-data:wiki and set group write permission, 55732 should be able to write a file. However:
[FONT="Courier New"]ls -ld test
drwxrwxr-x  2 www-data wiki 4096 2005-12-21 11:58 test
55732@lintranet:/tmp/test$ echo bob > bob
-bash: bob: Permission denied[/FONT]

What?????

Chgrping the test directory to my primary group 'users' is fine:
[FONT="Courier New"]ls -ld test
drwxrwxr-x  2 www-data users 4096 2005-12-21 11:58 test
echo bob > bob
55732@lintranet:/tmp/test$ [/FONT]
All works fine.

It is as if Ubuntu is ignoring my wiki group, or at least the members in it.

The only obvious thing I could think of was a control character or something had crept into /etc/group, however I can not see anything in a hex editor and tried retyping the group wiki right at the top of the file. That did not make a difference.

Any suggestions as to why this basic unix function does not seem to work?

---

