---
title: "Is this a bug? (where do I report it)"
date: 2010-12-21
forum: Desktop Environments
---

### Post by nrundy on 2010-12-21
I have my Time set to 24hr time. Yet when I Print to File (pdf) say to capture an internet page, the lower right footer always displays the time in AM/PM. Shouldn't this display of the time match my system's time (i.e., 24hr time)?

---

### Post by mcduck on 2010-12-21
how did you set the time format?

If you just changed the setting on the clock applet on your panel, that's not a system setting and only the clock applet itself.

The overall time format comes from your current locale (you can check that with the "locale" command in a terminal).

The system-wide setting for this comes from your system's default locale, set during the install. So that's again a different thing than what your user has set.

---

### Post by smuthavarapu on 2010-12-21
I changed the Time from Top Panel Applet, And I printed to PDF, its showing in 24 hour format only. Looks like not a Bug

---

### Post by nrundy on 2010-12-21
I changed the time System > Admin > Time and Date. And I changed it via applet on panel. Everything shows 24hr until I print to pdf file, then AM/PM.  Any idea how I can fix this?

---

### Post by nrundy on 2010-12-24
I'm in U.S. It must default to AM/PM time. I hate AM/PM time. You guys are in Europe, so maybe that explains the difference.

---

### Post by amauk on 2010-12-24
First, you'll need a launchpad account
goto [https://launchpad.net](https://launchpad.net) and create an account

To file a bug against a package
it's best to open up a terminal and type
ubuntu-bug <package>
This allows the system to automatically compile all the relevant system information together in your bug report

In your case, it sounds like a bug in CUPS (the print sub-system), so
```
ubuntu-bug cups
```

Follow the on-screen instructions

---

### Post by mcduck on 2010-12-24
> **nrundy said:**
> I changed the time System > Admin > Time and Date. And I changed it via applet on panel. Everything shows 24hr until I print to pdf file, then AM/PM.  Any idea how I can fix this?

That's still just the time, not the locale (which defines paper format, time format, and all the stuff like that).

Try running the "locale" command in a terminal and you'll see the current settings.

Also, you really need to change the *system locale*, not your own user's settings. Cups doesn't run as your user, so your personal settings have no effect on it.

[https://help.ubuntu.com/community/Locale]("https://help.ubuntu.com/community/Locale")

---

