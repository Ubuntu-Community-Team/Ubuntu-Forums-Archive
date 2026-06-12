---
title: "[SOLVED] 8.04 I have a Phantom Folder..."
date: 2009-01-02
forum: General Help
---

### Post by thelugnut on 2009-01-02
I can't get rid of this folder.
It is located in : Places>Home.
It is titled: mycomputer
I have tried everything I think I know to get rid of this folder but it is still there. When I do a sudo nautilus, it does not appear.
I haven't a clue as to how it got there, but obviously something I must have done.
Any suggestions?

---

### Post by ju2wheels on 2009-01-02
That is a user folder. When you installed Ubuntu was your first user name "james" or "mycomputer"? At some point after installation you must have created a second user. If you did then theres nothing really to worry about as each user gets a home folder.

In order to remove it you will most likely have to become the super user
```

sudo rm -rf /home/mycomputer

```

---

### Post by thelugnut on 2009-01-02
Thank you for the reply ju2wheels.

Yes, that is the solution. I appreciate it. I  had completely forgotten about the second user. A senior moment I suppose.:P

---

