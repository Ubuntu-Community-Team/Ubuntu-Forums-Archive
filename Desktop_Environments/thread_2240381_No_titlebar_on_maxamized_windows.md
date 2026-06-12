---
title: "No titlebar on maxamized windows"
date: 2014-08-19
forum: Desktop Environments
---

### Post by dethredic on 2014-08-19
I'm running Xubuntu 14.04, everything was working correctly yesterday, but today (after a reboot and update) I'm having an issue.

When I open an application it looks normal, but when I maximize it the titlebar is no longer visible, and the menubar/tab bar are now at the top of my screen.

Here is what it looks like NOT maxamized: [http://i.imgur.com/vRRjVsb.png](http://i.imgur.com/vRRjVsb.png)
Here is what it looks like maxamized: [http://i.imgur.com/i4PyL86.png](http://i.imgur.com/i4PyL86.png)
This is what I expect maxamized to look like: [http://i.imgur.com/TA7oobe.png](http://i.imgur.com/TA7oobe.png)

I tried deleting all my session data, but that didn't work. I changed my themes to Greybird but that didn't help either.
I have integrated intel graphics

Edit: here is my update list from last night:
[http://pastie.org/private/ut1zu8hgycd688rm17jiw](http://pastie.org/private/ut1zu8hgycd688rm17jiw)

---

### Post by Buntu Bunny on 2014-08-20
You can try

```
xfwm4 --replace
```

---

### Post by dethredic on 2014-08-20
As you can see from the pastie I posted xfmw got updated. I downgraded and that fixed my issue.

---

### Post by snidely2 on 2014-08-21
still, i think there was a config option that could be adjusted to correct that, i.e., someone thought they were "fixing" things . . .
I'll look around and see if I can find it . . .

---

