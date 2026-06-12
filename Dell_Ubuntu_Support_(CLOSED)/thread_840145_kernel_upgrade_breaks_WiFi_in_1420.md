---
title: "kernel upgrade breaks WiFi in 1420"
date: 2008-06-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by prasannadavid on 2008-06-25
Hello all,

Had installed 8.04 in my inspiron 1420 and slowly getting the devices to work one by one.  

Yesterday, did an upgrade to 2.6.24-19.34 and the WiFi stopped working.  No wifi indicator light also.

Any pointers to what I should be doing ?

(The previous upgrade to 2.6.24-19 did help a bit as I was able to use the modem after that).

regards,
Prasanna David

---

### Post by xcesarfrancox on 2008-06-25
I was looking for another solution but I found this that might help:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/WiFi_LED_does_not_work](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/WiFi_LED_does_not_work)

Was that your problem?

---

### Post by prasannadavid on 2008-06-26
Oops.  probably wrong problem statement.  I figured out that wifi is actually working.  I am connected. (But, I really don't know why I was not able to connect yesterday.)

But, still, after upgrade to 2.6.24-19.34, the wifi led doesn't glow.


> **xcesarfrancox said:**
> I was looking for another solution but I found this that might help:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/WiFi_LED_does_not_work](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/WiFi_LED_does_not_work)

Was that your problem?


I had gone through that earlier.  First, wifi led didn't work.  After following the instructions on the quoted url, the led was working.  But, not, again, after the last upgrade the led is not working.

---

### Post by xcesarfrancox on 2008-07-03
Try with this command
```

sudo apt-get install linux-backports-modules-2.6.24-19-generic

```

Maybe you're trying with the one withing the dell linux wiki page
```

sudo apt-get install linux-backports-modules-2.6.24-16-generic

```

Pay close attention to the hole command, it's not the same, and that's probably the reason your led doesn't work :)

---

