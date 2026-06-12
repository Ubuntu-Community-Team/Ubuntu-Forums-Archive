---
title: "Emerald theme manager as default"
date: 2009-03-11
forum: Desktop Environments
---

### Post by astonerose on 2009-03-11
Hi, I have a problem with emerald theme manager. I have edited a theme and it looks really nice but it wont set as default I have to type "emerald --replace" how to set it up to this automatically as I find my self typing it in a few times each session as it doesn't seem to stay, all the title bars disappear and i have to type "emerald --replace" again.

Also I am having problems with cursor themes and emerald it seems to be randomising which cursor it uses even thought iI have set it to crystal ble.

Thanks

---

### Post by Ratscallion on 2009-03-11
Hi. I would advise that you go into System->Preferences->Sessions and add a launcher called Emerald to this list. This would make it run at startup. If this fails, you could try 
```
 emerald& --replace
```
OR
```
 emerald --replace&
```
OR
```
 emerald& --replace&
```
Which would allow you to run a command via Terminal, but also allowing you to close the Terminal without terminating said program. Hope this helps.

---

### Post by binbash on 2009-03-11
add emerald --replace to your startup : 

System > Preferences > Sessions

---

### Post by astonerose on 2009-03-11
thanks binbash that sorted it

---

