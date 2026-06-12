---
title: "E: dpkg was interrupted"
date: 2009-02-07
forum: General Help
---

### Post by manojchandra on 2009-02-07
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I am an absolute beginner.

How do I do as advised?

How do I find "terminal"?

Please ignore me if I am being very silly.

---

### Post by kestrel1 on 2009-02-07
Not being silly at all.
To run the terminal go to:
Applications - Accesories - Terminal
once the terminal opens type the command:```
sudo dpkg --configure -a
```
You will be asked for your password.

---

### Post by ibutho on 2009-02-07
Do the following

Applications -> Accessories -> Terminal and enter the following
```
sudo dpkg --configure -a
```

---

### Post by drs305 on 2009-02-07
ALT-F2, tick "Run in terminal".
Copy the following command.
Tick "Run in terminal".
Hit "Run"

```
sudo dpkg --configure -a
```

You will be asked for your password. You won't see it as you type. Hit ENTER after you have typed it in.

---

### Post by manojchandra on 2009-02-07
Thanks to you all.
I typed as stated.
used space and dash as in the script.

It says unknown command.
obviously i am doing something wrong here.

---

### Post by howefield on 2009-02-07
Try copying and pasting from the posts to make sure there are no typos.

---

### Post by manojchandra on 2009-02-07
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

When I did, as advised, this is what happened

THANKS

---

### Post by howefield on 2009-02-07
It is an old thread, but a few posters seem to have recovered from this.

[http://ubuntuforums.org/showthread.php?t=231752](http://ubuntuforums.org/showthread.php?t=231752)

---

