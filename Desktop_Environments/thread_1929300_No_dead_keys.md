---
title: "No dead keys"
date: 2012-02-21
forum: Desktop Environments
---

### Post by Steve88 on 2012-02-21
I cannot enable dead keys anymore. The problem seems to have surfaced when I installed Ibus with anthy in order to type japanese. Now, even though lxkeymap shows I'm using the layout us(intl) there are no dead keys anymore. What should I do?

Best regards,

Steve88

---

### Post by kazztan0325 on 2012-02-22
Hi Steve88,

I would like to ask you what does **"dead keys"** mean?

---

### Post by Rodney9 on 2012-02-22
> **kazztan0325 said:**
> Hi Steve88,

I would like to ask you what does **"dead keys"** mean?

Thanks to Wikipedia -

> A dead key is a special kind of a modifier key that, instead of being held while another key is struck, is pressed and released before the other key. 

Steve, 

This may help, seems your not alone - 

[http://ubuntuforums.org/showthread.php?t=1860014](http://ubuntuforums.org/showthread.php?t=1860014)

Rodney

---

### Post by Steve88 on 2012-02-22
I read it, but it didn't solve the problem. I wasn't using scim. :(


Best regards,

Steve88

---

### Post by kazztan0325 on 2012-02-22
What about trying to use **'ibus-mozc'** instead of using 'ibus-anthy'?

You can install 'ibus-mozc' with Synaptic Package Manager or Software Center.

---

### Post by Steve88 on 2012-02-23
No the problem isn't with anthy... I completely disabled it and I still have the wrong keymap. The problem seems to be ibus.

Best regards,

Steve88

---

### Post by kazztan0325 on 2012-02-24
Which '-buntu' and which version are you running?

I guess maybe you are running 'Lubuntu', because there is a word "lxkeymap" in your first post.
Do I guess correctly?

---

### Post by Steve88 on 2012-02-24
You are guessing correctly although I put that in the title as well :P
I am running OneIric (11.10) to be precise.


Best regards,

Steve88

---

### Post by kazztan0325 on 2012-02-24
OMG!
I didn't notice your post's title has a word [lubuntu], I'm so stupid...

Now, let's return to the subject.

Would you please make clear your issue for me?

You cannot apply your original keymap (I don't know yet it is French or Spanish or something others) with 'lxkeymap' since you installed Japanese Input Method.
Do I grasp correctly?

---

### Post by Steve88 on 2012-02-24
That's correct. I cannot apply my original US International keymap, since I installed ibus (lxkeymap shows it as being applied but it has no effect).

---

### Post by kazztan0325 on 2012-02-24
I found a web page in Launchpad:

**Ubuntu “lxkeymap” package Bugs Bug #729880 "Settings not saved on natty"**
[https://bugs.launchpad.net/ubuntu/+source/lxkeymap/+bug/729880]("https://bugs.launchpad.net/ubuntu/+source/lxkeymap/+bug/729880")

I guess possibly the issue may relate to this bug.
i.e. It is possible the issue would be a bug of 'lxkeymap', not a bug of 'ibus'.

If then, maybe there is no way to solve the issue at present, because it seems Fix would be released in Precise.

---

### Post by Steve88 on 2012-02-26
Hmm... but the strange thing is that lxkeymap says that my current keymap is us(intl) - so it's as if it's saved. If this is indeed the problem then I should be able to fix it bypassing lxkeymap (and using something else). I'll try that.

---

### Post by kazztan0325 on 2012-02-27
By the way, did you install Japanese Language Support? (*System Settings > Language Support*), or just installed only ibus-anthy (and related packages)?

---

