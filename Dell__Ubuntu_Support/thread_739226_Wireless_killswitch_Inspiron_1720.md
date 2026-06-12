---
title: "Wireless killswitch Inspiron 1720"
date: 2008-03-29
forum: Dell  Ubuntu Support
---

### Post by h3r0n on 2008-03-29
Looking for a howto for enabling the wireless on/off switch on the front left corner of  a Dell Inspiron 1720

---

### Post by h3r0n on 2008-04-02
bumpage =)

---

### Post by notwen on 2008-04-02
If it is anything similar to my Inspiron 1420n's kill switch then it is enabled by default.  I turn it off, it kills wifi and bluetooth, turn it back on wifi and bluetooth are working once again.  Have you checked your BIOS by chance?

---

### Post by h3r0n on 2008-04-03
BIOS is all set. Its a setkeycodes issue, it just needs to be told what this little button is doing.  I'm just not entirely sure what the mapping is supposed to be...

Something like <setkeycodes e011 $KEY_CODE>

what $KEY_CODE is.....

Thanks for the reply

---

### Post by niteshifter on 2008-04-03
Methinks [FONT="Fixedsys"]showkey[/FONT] and [FONT="Fixedsys"]getkeycodes[/FONT] are what you need.

---

### Post by h3r0n on 2008-04-03
Neither produce needed results. 

```
Couldnt get a file descriptor referring to the console
```

Never-the-less...I'll keep looking.

---

