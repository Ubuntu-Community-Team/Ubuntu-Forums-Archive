---
title: "passwordless ssh"
date: 2009-06-02
forum: General Help
---

### Post by gforster on 2009-06-02
I am trying to figure out how to do the passwordless ssh thing so I can write a script that will send out a command (such as apt-get update or apt-get install) to all of the computers in our lab.

This is what I have done:

On my local machine- ```
ssh-keygen -t rsa
```

then
```
scp ~/.ssh/id_rsa.pub remote.server.ip:.ssh/authorized_keys2
```

but it wouldn't recognize the directory, so I ran  ```
ssh-keygen -t rsa
``` on the remote computer. and then copied the key over and it seemed to work.

Now when I go to ssh into the remote computer, it wants me to ssh in as "mylocalusername@remote.server.ip" instead of "my**remote**username@remote.server.ip"

How do I make it recognize me as the remote user? It is asking for my local user which doesn't exist on that machine.

---

### Post by JohnFH on 2009-06-02
When you ssh into the remove computer, specify the remote user as well, so do this:

```
ssh remoteUser@remotePC
```

instead of 

```
ssh remotePC
```

That's assuming I've understood your problem.

EDIT: By the way, you can use the ssh-copy-id command for a more convenient way to copy your ssh id to other machines.

---

### Post by gforster on 2009-06-02
Ok, duh on my part!  But, it now returns

Agent admitted failure to sign using the key.

and I have to enter my password. What simple thing am I missing this time?

---

### Post by JohnFH on 2009-06-02
Try the following and if it doesn't work post the results.

```

ssh-copy-id remoteUser@remotePC

```
You will be prompted for the password of 'remoteUser' on 'remotePC'.  After entering the password, try ssh again:

```

ssh remoteUser@remotePC

```

---

### Post by gforster on 2009-06-02
same deal. it seems that it is a problem with 64-bit Jaunty. There has been a bug report filed by someone else, so hopefully something can be done about it.

---

### Post by JohnFH on 2009-06-02
> **gforster said:**
> same deal. it seems that it is a problem with 64-bit Jaunty. There has been a bug report filed by someone else, so hopefully something can be done about it.

Strange.  I'm running 64bit Jaunty as it works perfectly for me.  Ah well ...

---

### Post by gforster on 2009-06-02
For reference, it is bug 328445

---

