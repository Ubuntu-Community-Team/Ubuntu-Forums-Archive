---
title: "new Inspiron 530, very little sound output :(  have updated the system"
date: 2009-02-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kraymore on 2009-02-01
I met a man at starbucks who saw that I was very savy with computer things and he enlisted my service to make a recommendation to him as to a computer for him to purchase, to I found him a Inspiron 530 that Dell was selling with monitor.  I am very embarassed because the system is fully updated and it is yielding very little sound.  He has gone through the trouble of replacing his speakers, and that has not fixed the problem.  

I have noticed that the Dell Wiki has a entry for "Ubuntu 8.04/Issues/No Sound After Distribution Or Kernel Upgrade"

will the fix there for Hardy restore sound to his system?  I dont seem to recall any modem being on the system at all, for that reason, I'm seeking what options will restore sound to this mans computer.  

thanks so much.

---

### Post by llamakc on 2009-02-01
While you mentioned the 8.04 wiki page, you didn't specify whether or not you're using 8.04. 

Have you unmuted the speakers in `alsamixer` yet? Sometimes that is an issue.

---

### Post by kraymore on 2009-02-01
its using hardy.  is that 8.04 ?

yes i cranked up all the levels.

---

### Post by llamakc on 2009-02-01
Which kernel are you using?

You can find this out (if you do not know how already) in the terminal by typing:

```

uname -r

```

---

### Post by kraymore on 2009-02-01
not sure.  i bought it for a nice man that saw i was a computer geek at starbucks.  i'm supposed to return today to fix it for him.  he bought it by my recommendation, so i hope to get it working.  i can't access his computer from here i am at home.  i'll assume hardy is 8.04 though.

---

### Post by llamakc on 2009-02-01
> **kraymore said:**
> not sure.  i bought it for a nice man that saw i was a computer geek at starbucks.  i'm supposed to return today to fix it for him.  he bought it by my recommendation, so i hope to get it working.  i can't access his computer from here i am at home.  i'll assume hardy is 8.04 though.

Yes: Hardy is 8.04. I am asking about the running kernel that does not have sound working on it (yet). The wiki page's instructions would be where I would start if I were you.

---

### Post by floborg on 2009-02-04
Passive or active speakers?

I reused my old speakers when I got my 530n, and I wasn't getting any sound.  It turns out that this machine has low output because active speakers are assumed - mine are passive.  I'm working around the problem now by plugging into the headphone output on the front of the tower.  The only permanent fix for me is to simply get some active speakers.

---

