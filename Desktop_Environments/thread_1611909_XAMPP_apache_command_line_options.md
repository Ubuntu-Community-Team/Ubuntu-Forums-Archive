---
title: "XAMPP apache command line options"
date: 2010-11-02
forum: Desktop Environments
---

### Post by crong on 2010-11-02
Does anyone know how I can start apache with command line options? Specifically, I need the -D switch to set a variable.

/opt/lampp/lampp start -D local doesn't work but the other ways I've tried seem to bypass all XAMPP settings.

---

### Post by crong on 2010-11-09
The answer is here: [http://www.apachefriends.org/f/viewtopic.php?f=3&t=42621&start=0](http://www.apachefriends.org/f/viewtopic.php?f=3&t=42621&start=0)

---

### Post by crong on 2010-11-10
C'mon dude - this is the age of the Internet. I'm the author of that thread - "Bigbread" - and I don't speak German either:

[http://www.google.com/language_tools](http://www.google.com/language_tools)

I didn't get any replies in the English section so I switched to the German one.

Anyway, the upshot is that all the answers are in the /opt/lampp/lampp file which is a straightforward shell script file. I got confused because when I tried to open it with gedit I got an error saying the character encoding couldn't be determined and I simply accepted the suggestion that it was a binary file, i.e. not human-readable. Instead, it's a case of the file being ANSI encoded (so maybe was written on a Windows platform) and gedit has no provision for ANSI encoding (= stupid, in my opinion).

This is what I'm now using to start Apache:
```
/opt/lampp/bin/apachectl -k start -D PHP5 -E /opt/lampp/logs/error_log -D local
```Note that a define directive variable, PHP5, is already being used and is essential (can also be PHP4)

---

