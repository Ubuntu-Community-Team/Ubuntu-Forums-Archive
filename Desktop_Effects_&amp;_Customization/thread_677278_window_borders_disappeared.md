---
title: "window borders disappeared"
date: 2008-01-24
forum: Desktop Effects &amp; Customization
---

### Post by slarrabe on 2008-01-24
This occured after I installed the nVIDIA drivers on my Compaq Presario F756NR.  All my window borders are missing and I can't open a terminal (I just get a white rectangle).  How do I fix it?

---

### Post by jmbenson89 on 2008-01-24
bump.

I have Compiz Fusion, and one time (so far...I've had it a few days) the window borders disappeared. I could still start new apps, but they would also not have window borders (window themes, whatever you wanna call it).  I'm using Emerald themes.  Is there a way to  make the themes come back incase this happens again?

---

### Post by BuntuFreak on 2008-01-25
I'm in the same boat. Terminal does not post characters at all. And borders and captions have gone. Someone says to enable "Place Windows" and change the "General" option to "Centered" from "Smart". Did not work for me and another poster. But you may want to try it all the same. Maybe you'll get lucky.

Best.

---

### Post by biffta on 2008-01-26
[http://ubuntuforums.org/showthread.php?p=3561151#post3561151](http://ubuntuforums.org/showthread.php?p=3561151#post3561151)

---

### Post by BuntuFreak on 2008-01-26
Thanks. But I'm still having problems.

First I have the "Advanced Desktop Settings Menu" already. Now I did go to "Windows Decorations" but did not see "command box". There is a "filter" box. Is that where I type "emerald".

Regardless, I don't have emerald installed. So I did "sudo apt-get emerald" only to be greeted by this error.

E: Invalid operation emerald

Please help!

---

### Post by tangibleorange on 2008-01-26
> **BuntuFreak said:**
> Thanks. But I'm still having problems.

First I have the "Advanced Desktop Settings Menu" already. Now I did go to "Windows Decorations" but did not see "command box". There is a "filter" box. Is that where I type "emerald".

Regardless, I don't have emerald installed. So I did "sudo apt-get emerald" only to be greeted by this error.

E: Invalid operation emerald

Please help!

Well firstly you've forgotten your install in "apt-get" :P.
Correct command is "sudo apt-get install emerald".

---

### Post by BuntuFreak on 2008-01-26
My Bad. Anyways, I just wen to Synaptic Manager and installed emerald.

Also I got a new presecription for my glasses, found the "Command" edit box and typed in emerald in it.

Still same problem. No window captions and Absolutely no characters getting posted to the Terminal.

Please help!

---

### Post by slarrabe on 2008-01-28
WHOO HOO!  Finally got my borders back!  Used the code shown below.:guitar:

> I have an nvidia graphics card as well and had a lot of the same problems posted in this thread. 
No borders and my terminal windows came up white.
I looked around for a while and found this command:

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

Restarted X and everything worked for me.

---

