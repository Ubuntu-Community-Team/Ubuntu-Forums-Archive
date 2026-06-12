---
title: "Localization problems"
date: 2008-12-23
forum: General Help
---

### Post by LB06 on 2008-12-23
Hello, currently I'm running into to some problems regarding the language settings of my Ubuntu 8.10 system. My native language is Dutch, but since I'm used to having an English OS and the translation is slightly lacking (quite a few strings did not get translated) I prefer to run an untranslated version of Ubuntu. The problem is that I absolutely do not want US dates, times and numeric conventions. I don't know what to do with Fahrenheit, I hate am/pm and my week starts on monday.

So basically I have this:

```

luk@raptor-ubuntu:~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

and I want this:
```

luk@raptor-ubuntu:~$ locale
LANG=en_US.UTF-8
LC_CTYPE="nl_NL.UTF-8"
LC_NUMERIC="nl_NL.UTF-8"
LC_TIME="nl_NL.UTF-8"
LC_COLLATE="nl_NL.UTF-8"
LC_MONETARY="nl_NL.UTF-8"
LC_MESSAGES="nl_NL.UTF-8"
LC_PAPER="nl_NL.UTF-8"
LC_NAME="nl_NL.UTF-8"
LC_ADDRESS="nl_NL.UTF-8"
LC_TELEPHONE="nl_NL.UTF-8"
LC_MEASUREMENT="nl_NL.UTF-8"
LC_IDENTIFICATION="nl_NL.UTF-8"
LC_ALL=nl_NL.UTF-8

```

Is this possible? I tried to add LC_ALL=nl_NL.UTF-8 to /etc/environment, but doing so somehow made gnome or gdm believe that I also wanted LANG to be nl_NL.UTF-8, which I don't. All my strings were in Dutch again.

Any help would be very much appreciated. Tnx!

---

### Post by Pobega on 2008-12-23
Why not just set each of them manually in /etc/environment, and leave LC_ALL empty? I've never changed locales before, but from what I can tell LC_ALL changes every single one of them; Not just the ones starting in LC.

---

