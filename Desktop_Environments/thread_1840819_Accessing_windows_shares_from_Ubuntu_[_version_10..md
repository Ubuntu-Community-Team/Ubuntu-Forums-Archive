---
title: "Accessing windows shares from Ubuntu [ version 10.04 ]"
date: 2011-09-08
forum: Desktop Environments
---

### Post by rawat on 2011-09-08
Hi Guys,

Ubuntu version : 10.04 Lucid

From a very long time I am experiencing below error while accesing the windows share

> Error 1 :
  Sorry, could not display all the contents of "CRM_Attach": DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.> Error 2 :

Error: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Please select another viewer and try again.Both came when accessing the same location. I can navigate to few folders but then on accessing one folder I get errors.

Suppose I am accessing smb://IP_ADDRESS/folder1/folder2/folder3/folder4/folder5

folder4 gives this error,till folder3 it works fine.

Any solution or alternatives??

Thanks,
Rawat

---

### Post by Morbius1 on 2011-09-08
> smb://IP_ADDRESS/folder1/folder2/folder3/folder4/folder5
That's the wrong syntax. It should be:
```
smb://IP_ADDRESS/share-name
```

---

### Post by rawat on 2011-09-08
Hi Morbius

> folder1 is the share-name 

after that i am navigating by clicking on folders mentioned.

---

### Post by Morbius1 on 2011-09-08
By any chance did you set up access from Ubuntu and have it remember the password for the share forever? There's an old bug that should have been fixed by now:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/463267](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/463267)

You'll need to remove the credentials from "Passwords and Encryption Keys" for that share: System > Preferences > Passwords and Encryption Keys. Somewhere in there is the saved credentials for that remote share.

---

### Post by rawat on 2011-09-08
Before posting here I searched about the problem and found the same.

Did that but still no success.

There is another bug > [https://bugs.launchpad.net/ubuntu/+source/libgnome-keyring/+bug/560588](https://bugs.launchpad.net/ubuntu/+source/libgnome-keyring/+bug/560588) which resembles lot to my issue.

I guess it is not fixed.

So I was looking for some workarounds :(

---

### Post by rawat on 2011-09-12
Hi,

> Update :

Freshly installed 11.04 and same issue there as well!! :( :(

How people are accessing windows shares?? 

This is really affecting work :(.

Please guide

Thanks,
Rawat

---

