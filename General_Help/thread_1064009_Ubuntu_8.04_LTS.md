---
title: "Ubuntu 8.04 LTS"
date: 2009-02-08
forum: General Help
---

### Post by davidryan on 2009-02-08
please can someone help me when i try to update my sysyem i keep getting this message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

any help ?
many thanks
david

---

### Post by overlord.gaurav on 2009-02-08
Do as the message says.
Open a Terminal and type:
```
dpkg --configure -a
```

Try updating your system after this.

---

### Post by davidryan on 2009-02-08
thanks i tried that and got this 
dpkg: requested operation requires superuser privilege
david

---

### Post by jespdj on 2009-02-08
Then do
```
sudo dpkg --configure -a
```
Note: Please use a more describtive topic title than "Ubuntu 8.04" next time when you post something.

---

### Post by paydaydaddy on 2009-02-08
sudo dpkg --configure -a

---

### Post by davidryan on 2009-02-08
cheers thank you for your help , :popcorn:
david

---

### Post by Serpico79 on 2009-02-08
Please somebody help me!!

I have the same problem but when the system ask my password I cannot type anything.

Thanks

---

### Post by howefield on 2009-02-08
> **Serpico79 said:**
> I have the same problem but when the system ask my password I cannot type anything.

You won't see the password being typed, but it is.

Just type your password and press enter.

---

### Post by boof1988 on 2009-02-08
> **Serpico79 said:**
> Please somebody help me!!

I have the same problem but when the system ask my password I cannot type anything.

Thanks

Your password will not be displayed (for security reasons) it wont even show asterisks.  This is what is supposed to happen.  So just type in your password and press enter.

---

### Post by Serpico79 on 2009-02-08
Ok it works, but after the password I have this message:

dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

What does it mean?

Thanks again!!

---

### Post by Racecar56 on 2009-02-08
> **howefield said:**
> You won't see the password being typed, but it is.

Just type your password and press enter.

I used to be baffled by the same question.

Try this:
```
sudo apt-get -f install
```

---

### Post by howefield on 2009-02-08
> **Serpico79 said:**
> Ok it works, but after the password I have this message:

dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed. Aborted

I have seen several posts this weekend with similar errors, there are a couple of threads where other posters seem to have fixed it. I'll try and find one.

Try this post on the ultimate forums by "Nick" 

[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2699&p=28008](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2699&p=28008)

---

