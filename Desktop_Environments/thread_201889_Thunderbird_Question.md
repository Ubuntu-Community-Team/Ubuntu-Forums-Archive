---
title: "Thunderbird Question?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by Mike_N on 2006-06-22
So i have two Linux boxes in my room and i'd like to be able to export my Thunderbird settings to the other machine, rather then run the Account Setup again. I know how to find and copy the profile folder in XP but i'm lost here. Can someone please tell me where it is?

Thank you, Mike

---

### Post by luibh on 2006-06-22
This should help you out - [https://www.mozilla.org/support/thunderbird/profile](https://www.mozilla.org/support/thunderbird/profile)

---

### Post by Mike_N on 2006-06-22
Sad to say, no... it said that the file is in

thunderbird/xxxxxxxxxxxxxxx.default

not very helpful

---

### Post by luibh on 2006-06-22
Sorry about that. On my Ubuntu box it is in ~/.mozilla-thunderbird/mghjlg76.default (this is a little different than what the link states.) I had a whole response written and realized you know where it is in Windows, but not in Ubuntu. So, in the terminal, if you ```
cd ~/.mozilla-thunderbird/
ls
```
you should be able to find it. If you want to browse there in the file browser, open up your home folder press CTRL-L and there you can type in ```
~/.mozilla-thunderbird/
```and you should find it there.

---

### Post by Mike_N on 2006-06-22
Boy do i feel dumb, i followed the instructions and sure enough... so i was wondering why i couldn't see them before, because just like Windows, i had to turn on "hidden files"... duh..!

Thanks...

---

