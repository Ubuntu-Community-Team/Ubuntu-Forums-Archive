---
title: "iSeriesAccess lock-up"
date: 2008-09-19
forum: Desktop Environments
---

### Post by capescw on 2008-09-19
Successfully installed IBM iseriesAccess on the 1st try (H Heron), THANK YOU to n8bounds for his article. However, one problem I can't find an answer to, perhaps someone can assist. Emulator connecting to AS400, simple 'fill in the form' application. If I inadvertantly enter a numeric character in a field that is programmed to accept ONLY 1 of 5 alpha characters, I immediately get a 'lock-up', what appears to be a double cursor (_ + -), and a circular symbol (the actual cursor ?). No key sequence seems to clear the condition, I have to use pulldown 'Options - Reset'. IMPORTANT - these same AS400 programs work fine on 'iSeriesAccess' for Windows, allowing the user to backspace and enter the correct info. Obviously, any help would be greatly appreciated.

---

### Post by jflaker on 2008-09-19
Check your keyboard mapping.  I haven't used that version, but use iSeries Access daily.  Usually the left ctrl key will reset the alert

Let me know if it works.

IM me, i've tried to get it to work, but haven't had the time to really check out the app.

---

### Post by capescw on 2008-09-20
Thanks, it was mapped differently than the Windows version! Why do I get a 'lockup' in the Ubuntu version, whereas the Windows version give me a message, but leaves the field available? Are you aware of any correction I could make?

---

### Post by jflaker on 2008-09-20
iseries Access will not allow invalid entries on a field, ie: Character in num field.  I really haven't tried the Linux version yet....soon though

It protects the integrity of the program/data....it is somewhat annoying, but once you understand why, it is so applications remain idiot proof in front of the user if proper programming was made by the programmer such as limiting values in a field...
Yes/No should only be Yes/No instead of YAH or YEA

---

