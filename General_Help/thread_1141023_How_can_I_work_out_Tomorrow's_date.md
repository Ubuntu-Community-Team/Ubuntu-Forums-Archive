---
title: "How can I work out Tomorrow's date?"
date: 2009-04-28
forum: General Help
---

### Post by SiHa on 2009-04-28
This should be simple, but I've not had any luck so far.

I need to write a simple script to set the BIOS wakeup time to 'Tomorrow' @ 0700hrs.

I'm having trouble with deriving 'Tomorrow'. I thought this would be a case of using the DATE function with the -d switch, and saying something like **date=today+24hrs**:```
tomorrow=date -d=`date +%x`+24:00:00
```

I really don't want to go through the hassle of scripting this manually, as it gets quiet complicated when you start to take leap years into account etc.

Am I barking up the wrong tree completely? Does anybody know of a simple way to achieve this?

TIA,

Simon

---

### Post by benj1 on 2009-04-28
date --date='+1 day'
prints tomorrows date check man and info pages for formatting

---

### Post by SiHa on 2009-04-28
d'oh! See, I told you it would be simple.

A bit like me.

Thanks for your help. I found the man and info pages for this function not very helpful at all. Nowhere do they mention that you can do useful stuff like that.

---

