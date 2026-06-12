---
title: "Terminal seems to think I'm not the super user?"
date: 2009-01-18
forum: General Help
---

### Post by Spoot89 on 2009-01-18
Hi, I'm trying to install some drivers for my graphics card. I downloaded a .run file, and I was told to use the terminal to run the installer for the drivers. So I do that, and the installer starts up, but shortly after that, I get the following message:

"You need to run this installer as the super user."

How could I not be the super user? There is only one account on this computer, so I have to be the super user by default, don't I?

---

### Post by taurus on 2009-01-18
You are not root even if you use the original account that you created during the installing process.  If you need root privilege, run the command with the sudo in front with the same password that you use to log in.

```
**sudo** filename
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by albinootje on 2009-01-18
> **Spoot89 said:**
>  How could I not be the super user? There is only one account on this computer, so I have to be the super user by default, don't I?

Let's assume your file is called MyNewDriver.run
If that script is text only, do this :
```

sudo sh ./MyNewDriver.run

```
If your script needs GUI wings to fly :
```

sudo -H sh ./MyNewDriver.run

```

Read also this :
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Spoot89 on 2009-01-18
Thank you, that worked for me!

The help was much appreciated =)

---

### Post by MaxIBoy on 2009-01-18
[http://www.akamarketing.com/unix-files-permissions.html](http://www.akamarketing.com/unix-files-permissions.html)

You can mark a thread as solved through the "thread tools" menu, right above the topmost post.

---

### Post by snova on 2009-01-18
> **MaxIBoy said:**
> You can mark a thread as solved through the "thread tools" menu, right above the topmost post.

Not at the moment. ;)

[http://ubuntuforums.org/showthread.php?t=1039481](http://ubuntuforums.org/showthread.php?t=1039481)

---

