---
title: "script works in Unity not in XFCE"
date: 2014-05-20
forum: Desktop Environments
---

### Post by GrouchyGaijin on 2014-05-20
Hi Guys,

I have a question that maybe someone can help me with.
I've used Ubuntu with Unity for a few years, but as my laptop ages I thought I'd try Xubuntu to see if it responded a little quicker.
Overall the experience has been positive, but there is one thing that confuses me.

I have a script that I've used for a long time that allows me to hit a key combination and my email address is pasted into wherever I have the cursor.
The script runs fine in Unity, but not in XFCE.

```

#!/bin/bash
echo me@mydomain.com | xsel -bi
xdotool key ctrl+v

``` 

In Xubuntu the email address is copied to the clipboard but not pasted.  In order to actually paste the email address into a document or form I have to press ctrl+v.

Does anyone have a clue why this might be?

---

### Post by matt_symes on 2014-05-20
Hi

# !/bin/sh
echo [email]me@you.com[/email] | xsel -bio

Is that what you want ? Does it even work for you as i can`t test it.

Kind regards

---

### Post by GrouchyGaijin on 2014-05-20
Thank you for the reply,
Unfortunatly the problem persists.
The [email]me@you.com[/email] **is** copied to the clipboard, but not pasted into the document as it should be.

---

### Post by matt_symes on 2014-05-20
Hi

I `m rather hog tied as i don`t currently have my laptop with me but, working from memory, i was wondering if xclip would do the job.

I will get my laptop tomorrow and will post back then.

Kind regards

---

### Post by grumblebum2 on 2014-05-20
When using xdotool in scripts called by a keyboard shortcut I usually use a **sleep 0.5** before the xdotool line.
Do you need to send it to the clipboard?
```
sleep 0.5 && xdotool type 'me@mydomain.com'
```

---

### Post by vasa1 on 2014-05-20
> **grumblebum2 said:**
> When using xdotool in scripts called by a keyboard shortcut I usually use a **sleep 0.5** before the xdotool line.
+1. Always worth trying.

---

### Post by GrouchyGaijin on 2014-05-30
Sorry for the late reply grumblebum2 - I just saw that there had been a post here.
Basically what I want is to be able to hit a key combination and have my email address pasted at the cursor.
If that can be done without the clipboard, cool.

Thank you for the help!

UPDATE
I just tried and it seems to be working.
[email]me@mydomain.com[/email]

The sleep command must have been the key!

---

