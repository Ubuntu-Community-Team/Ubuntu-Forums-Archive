---
title: "Start Conky after Desktop as loaded"
date: 2012-09-29
forum: Desktop Environments
---

### Post by insecure hyena on 2012-09-29
Hi community here I am with a tricky question.
What's the name of the process that handles the desktop in XFCE environment (i.e the application that draws the desktop icons)?
I'm asking this because I'm trying to write a simple script to run conky after the desktop has loaded.
As many of you know in fact if conky starts before the desktop it disapperas when the desktop loads.
So I need to know what's the name of the process of the overmentioned applcation.

---

### Post by ajgreeny on 2012-09-29
> **insecure hyena said:**
> Hi community here I am with a tricky question.
What's the name of the process that handles the desktop in XFCE environment (i.e the application that draws the desktop icons)?
I'm asking this because I'm trying to write a simple script to run conky after the desktop has loaded.
As many of you know in fact if conky starts before the desktop it disapperas when the desktop loads.
So I need to know what's the name of the process of the overmentioned applcation.
The command you need is **sleep**.

The easiest way to set a time interval for startup programs is to customise the command used in the list of applications to ```
bash -c "sleep 10; conky"
```which will delay it by 10 seconds.  Use a higher figure if that is too short a time lag.

This exactly what I use for conky in my 10.04 Ubuntu for exactly the same reason.

---

### Post by insecure hyena on 2012-09-29
Thank you for the quick replay but you suggest me an alternative to what I want to do.
Acutally I have implemented your solution but sometimes the desktop loads after the seconds passed to the sleep command so conky gets overridden by the desktop.
I need to know the name of the process that handle the desktop to implement a more specific control.
However let me thank you for your intervention. ;)

---

### Post by GreatDanton on 2012-09-29
Why would you like to write script for delaying conky? You can achieve the same thing by clicking on startup applications and adding the following command:
```
conky -p <number>
```The number is delay in seconds.

Hope this helps.

---

### Post by ajgreeny on 2012-09-29
So as I said in my post, just increase the sleep time to a value that works, eg 60 (or alternatively 1m for 1 minute).

I don't see why that can not be made to work if the time interval is correctly used. You say > Acutally I have implemented your solution but sometimes the desktop  loads after the seconds passed to the sleep command so conky gets  overridden by the desktop." which I assume means that your desktop is very slow to appear.

If you were using ubuntu it would be easy to tell you that nautilus writes the desktop, but in Xubuntu I don't think thunar does the same job, (or not yet, at least, though I think it may in xfce 4.10), so I can't help you with that question, I'm afraid..

---

### Post by ajgreeny on 2012-09-29
> **GreatDanton said:**
> Why would you like to write script for delaying conky? You can achieve the same thing by clicking on startup applications and adding the following command:
```
conky -p <number>
```The number is delay in seconds.

Hope this helps.
That is a trick I was not aware of!

Thanks for the tip GD, much appreciated. Even though it is only doing exactly the same job as my more complex command, it is an easier way to do it.

However, as you can see, the OP says it does not work for him.  I still think it will if the time interval is set correctly.

---

### Post by insecure hyena on 2012-09-29
My desktop doesn't took to long to display and the simple solution is, as you said, to increase the seconds before starting conky.
But my objective is different...I want a smart way to start conky.
However thanks again mate ;).

---

### Post by insecure hyena on 2012-10-01
C'mon community it's a simple question...what's the name (or even better the id) of the application that draws the icons on the Xubuntu's desktop? :lolflag:

---

### Post by LewisTM on 2012-10-01
It's **xfdesktop**
A script like that might work for you
```
#!/bin/bash
until (pgrep xfdesktop)
  do
    sleep 2
  done
conky
```
Cheers!

---

### Post by insecure hyena on 2012-10-01
Thank you very much for your quick replay.
I'll test the code as soon as I can to let the community know if it works.
Thanks again mate ;).

---

### Post by insecure hyena on 2012-10-02
Here I am with bad news :(.
The script you suggest me works flawlessly but conky gets always overridden.
Perhaps xfdestkop isn't the correct process that handles the drawn of the desktop's icons.
I don't know...
Please community help us. :(

---

### Post by LewisTM on 2012-10-02
I don't use Conky but by searching a bit, I found a possible fix.
Xfdesktop is known to override Conky display if the latter is set as a desktop window. This has nothing to do with load order.

Modify your .conkyrc file to contain:
> own_window_type override
If you don't have a ~/.conkyrc, copy it first from /etc/conky/conky.conf

---

### Post by insecure hyena on 2012-10-14
This line is already in my conky config but conky is always overridden by the desktop...
C'mon community...what is the damn process that override conky?!?!

---

