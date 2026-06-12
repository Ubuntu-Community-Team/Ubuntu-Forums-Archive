---
title: "Cannot close kmymoney"
date: 2006-08-11
forum: Desktop Environments
---

### Post by lakelovers on 2006-08-11
I just installed kmymoney and set up my initial account. Now I cannot close the program. I've tried everything under the sun and cannot shutdown the program or the computer. I have not tried a manual shutdown. This is the first "crash" type problem I've had with Ubuntu. I looked on the kmymoney web site but didn't find anything. I'll post there when my subscription is processed. Any ideas on how I can exit kmymoney?

---

### Post by Seaman on 2006-08-11
I do not know what kind of program kmymoney is but have you tried writing **killall kmymoney** in a terminal? If it doesn't work there is more powerfull commands to use which I don't control.

---

### Post by lakelovers on 2006-08-11
I tried "killall kmymoney" and it didn't work. KMyMoney is home financial program for KDE, but is supposed to work on GNU, also.

---

### Post by orasis on 2006-08-11
> **lakelovers said:**
> I tried "killall kmymoney" and it didn't work. KMyMoney is home financial program for KDE, but is supposed to work on GNU, also.

Open a terminal, sudo (you may not have to sudo) at prompt - type "xkill"
without the quotes, your cursor will change shape - click on the program you wish to terminate.

---

### Post by lakelovers on 2006-08-11
Okay, it worked. The full file name is kmymoney2. I left off the "2." Thanks for the tip.
Jerry

---

### Post by Seaman on 2006-08-11
After some further investigating I found two more ways, which one of them is the more powerfull way I was talking about. Try just launching **xkill** from a terminal, then click on the kmymoney window and it will hopefuly quit. If it does not work, trythe more powerfull way. I will give you an example how I would do in the same situation. In my example we are going to kill the program "snownews"
[b]
# ps -A|grep snownews
>> 12240 pts/1    00:00:00 snownews
# kill -9 12240
[/b]

Good luck!

EDIT: I see you've solved it, good ;)

---

### Post by orasis on 2006-08-11
You have to love "XKILL" =D>

---

