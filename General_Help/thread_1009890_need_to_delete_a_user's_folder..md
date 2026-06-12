---
title: "need to delete a user's folder."
date: 2008-12-13
forum: General Help
---

### Post by Heeter on 2008-12-13
Hi all,

I created a user using the users and groups function.

I decided to remove the user, but I cannot remove the user's folder found in the home folder.

How can I delete that user's folder?

As well, I would to change my own username, how can I do that?

Thanks

Heeter

---

### Post by graysky on 2008-12-13
> **Heeter said:**
> How can I delete that user's folder?

```
$ sudo rm -rf /home/USERNAME
```

> **Heeter said:**
> As well, I would to change my own username, how can I do that?

This might be a little more tricky... I would try the following:

1) Make your new user (i.e. the name of the user you want to be), for this example let's use the name "bob".  So make new user "bob" with access to whatever groups you want.  Let's say your old name is "john" for this example.

2) Hit alt+ctrl+F1

3) Log in as another user, one that's different from either of the two you want to mess with.

4) $ sudo mv bob bob-old

5) $ sudo mv john bob

6) $ exit

7) alt+ctrl+F7

There might be a better way... I dunno

---

### Post by Keith Hedger on 2008-12-13
Just moving the contents of a folder may not be enough as certain files are owned etc by certain users and creating a new user will create a different uid and gid to the other user so be prepared for a bit of mucking about with some file permissions.

---

### Post by Heeter on 2008-12-13
Thanks for the reply.

Will try out that username change thing right away.......

Heeter

---

### Post by vanadium on 2008-12-13
```

man usermod

```

---

### Post by haylun98 on 2008-12-13
You can do it in GUI:

First at terminal:

$sudo nautilus #this will open nautilus in sudo mode

Then navigate to the folder you want to delete
Be very careful to only delete the user folder then close the nautilus windows to terminate it in sudo mode

Good luck heeter!

---

### Post by Heeter on 2008-12-13
Thanks guys,

that deleted the user folder.


Thanks again,

Heeter

---

### Post by vanadium on 2008-12-14
> There might be a better way... I dunno

This is why I referred to the usermod command. With usermod, you can easily change the user login without touching anything else.

---

