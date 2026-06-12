---
title: "How do I get Lubuntu to show me the date next to the time in the desktop panel?"
date: 2014-07-12
forum: Desktop Environments
---

### Post by Ralf_Hutter on 2014-07-12
Hello everybody,
this is weird: I can't get my new lubuntu desktop to show me the date in the desktop panel! 
In other desktop environments date and time go together, but here is only the time, and no way to get the date next to it!
This is incredible, but i guess there is a trick...
Thanks in advance.
Oh, and i don't want any of the stuff with more icons to click on. I just want the date to be displayed right next to the time!

---

### Post by Rex Bouwense on 2014-07-12
Read this.
[https://help.ubuntu.com/community/Lubuntu/Documentation/CustomizingTheClock](https://help.ubuntu.com/community/Lubuntu/Documentation/CustomizingTheClock)

---

### Post by Dennis N on 2014-07-12
Right click on the time and open "Digital Clock Settings".

In clock format, replace what is there with:

```
%a %b %d %I:%M %p
```

This will give you the format: **Sat Jul 12 7:50 AM **

---

### Post by Ralf_Hutter on 2014-07-12
That was the trick, Dennis N, thanks a lot!

---

