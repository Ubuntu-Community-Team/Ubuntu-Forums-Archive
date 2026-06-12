---
title: "amaroK å, ä, ö collection problem"
date: 2006-06-08
forum: Desktop Environments
---

### Post by PtS on 2006-06-08
When I try to build a collection in amaroK it gets to 0% and stops. After a bit of experimenting I've understood that amaroK can't handle Å, Ä and Ö and my music is in a folder named Övrigt. amaroK treats Övrigt as locked or something and can't read it. I'm using SQLite. Would MySQL handle it right? Is there any way to solve this?

---

### Post by adamkane on 2006-06-09
This is probably just an issue with taglib. Which version of amarok are you using?

If you are using amarok 1.3, then you need to install taglib-1.4 and alsa-oss.

Amarok handles special characters very, if you have the latest taglib installed.

---

### Post by PtS on 2006-06-09
I'm using amaroK 1.4. Anyway, i tried installing those packages with amaroK 1.4 to see if it worked. It didn't. Is there a way to make it work with amaroK 1.4 or do I have to degrade to 1.3?

---

### Post by PtS on 2006-06-15
I've tried degrading to 1.3 but it didn't work. Does anybody have an idea of what to do? I'd really appreciate some help. :-(

---

### Post by PtS on 2006-06-18
I've solved it. I was wondering about what it the problem was and got the idea to check if it would work if I changed system language. I changed it from Swedish(Finland)-UTF8@euro to Swedish(Finland)-UTF8, and then it worked. :D Does anybody know what UTF8@euro is anyway? Thanks adamkane for trying to help.

---

