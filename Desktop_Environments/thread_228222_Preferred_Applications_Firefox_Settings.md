---
title: "Preferred Applications Firefox Settings"
date: 2006-08-02
forum: Desktop Environments
---

### Post by yetanothersteve on 2006-08-02
Firefox was recently upgraded to 1.5.0.5 through an automatic update broadcast to my 6.06 dapper install on 386.

After the update, clicking on web links or URLs in Mozilla Thunderbird emails no longer opened Firefox if Firefox was not already open. If Firefox was already open, the clicked link would open in a new tab.

In System -> Preferences -> Preferred Applications, I had Firefox as my default web browser with "Open link in new tab" selected. "Open link in new tab" has this as the command:
```
firefox -remote "openurl(%s,new-tab)"
```
Going to a terminal and typing firefox -help reveals no such option as -remote. And it will fail with -remote if no Firefox window is already open.

So I switched the Firefox "Preferred Applications" behavior to "Open link with web browser default" and now links or URLs in Thunderbird open a new firefox window if no firefox window is open or a new tab if one is open.

I guess the Firefox behavior changed OR I never noticed it before.

---

### Post by canadianwriterman on 2006-08-02
Try selecting:

```
Open link with Web browser default
```

And, as the command, enter:
```

Firefox %s
```

That's what mine is set for and it seems to work fine.

---

### Post by aysiu on 2006-08-03
Try [this](http://www.ubuntuforums.org/showthread.php?t=60427).

---

### Post by RichJacot on 2006-08-03
I was having the same issue and this worked for me. Thank you!

---

