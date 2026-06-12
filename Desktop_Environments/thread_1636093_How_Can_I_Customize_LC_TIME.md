---
title: "How Can I Customize LC_TIME?"
date: 2010-12-02
forum: Desktop Environments
---

### Post by klausner on 2010-12-02
I'm having a problem with the way that Thunderbird displays time values. Specifically, I want to use a 24-hour format, i.e. %H.%M.%S. This is the format I have all the rest of the desktop using.

It's been suggested that TB is referencing LC_TIME to set the format, but since my LC_TIME is using the en_US.UTF-8 package, it shows AM and PM on the times.

Tried doing *export LC_TIME="%H.%M.%S"*, but it doesn't work. *export LC_TIME="C"* just sets things to en_US.UTF-8.

I'm sure there is a way to customize the LC_TIME variable, I just don't know how to do it.

---

### Post by klausner on 2010-12-21
Bump.

---

### Post by ecormier on 2011-05-06
Just find a locale that supports 24 hour time and replace the following "en_US" with it

I was running Sunbird in and it defaulted to 24-mode, so I did the following to get it to 12-hour mode;
if you want to set it permanently:
```
export LC_TIME="en_US"
```
or if you want to change it for only one application:
```
LC_TIME="en_US" sunbird
```

---

