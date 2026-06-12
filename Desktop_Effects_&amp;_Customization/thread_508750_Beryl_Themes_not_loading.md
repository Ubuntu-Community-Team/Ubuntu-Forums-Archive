---
title: "Beryl Themes not loading"
date: 2007-07-24
forum: Desktop Effects &amp; Customization
---

### Post by guilly on 2007-07-24
Either i'm doing something wrong or something is miss configured. I loaded Beryl last night but now when i go into beryl-manager none of the themes seem to want to load. I can select them but they don't see to load i've tried to do a reboot and also to go to Select Window Decorator and then click on standard beryl decorator....

any help is appreciated...

tahnks

---

### Post by hyperair on 2007-07-25
First make sure Beryl is running. If this command returns a number, then it is :
```

pidof beryl

```

If Beryl is running, try running this command in the terminal:
```
emerald --replace
```

---

### Post by guilly on 2007-07-25
Ok will do when i get home tonight, Just a quick question, if i can access Beryl-Manager thru the GUI does that mean Beryl is running. Also some of the effects are working like being able to Alt-Tab or the superkey and tab to get the circular motion that is all working, I simply can't change themes or get the cube effect ( but that's another battle) i'd like to focus on simply getting the themes to work for now...

thanks for the help

---

### Post by hyperair on 2007-07-25
Oh that means that Beryl definitely is running. You just gotta get Emerald running now. ```
emerald --replace
``` and to check if its still running, ```
pidof emerald
```

---

### Post by guilly on 2007-07-25
ok kool, I've been reading alot on the border issue and currently I do not have any borders on my windows, meaning my close, maximize, minimize buttons are gone... is this because emerald is not running? alot of the issues i've been reading seem to be related to compiz and not beryl though...

---

