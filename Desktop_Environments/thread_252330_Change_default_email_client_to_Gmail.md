---
title: "Change default email client to Gmail?"
date: 2006-09-06
forum: Desktop Environments
---

### Post by markcholden on 2006-09-06
Newb question: I'd like to change my default email client to Gmail. How might I do that?

Thanks.

---

### Post by skymt on 2006-09-06
* Download the attached file
* Extract it to your home folder
* Run the following command in a terminal window: ```
sudo mv ~/gmailcompose /usr/bin
```
* Open System > Preferences > Preferred Applications
* Set Mail Reader to Custom
* Set the custom command to: gmailcompose %s

That should work, it does for me.

---

### Post by KSDZ on 2006-09-14
```

#!/usr/bin/python

# gmailto: Workaround to use GMail as your default email-client

import sys
import os

if len(sys.argv) >= 2:
	email = sys.argv[1]
	if email[0:7] == "mailto:": email = email[7:]
        email = email.replace('?','&')
	email = email.replace('&subject=','&su=')
else: email = False

os.execlp("gnome-open","","https://mail.google.com/mail/" + (email and "?view=cm&fs=1&to=%s" %(email) or ""))

```

* Hit Alt+F2, type "gksudo gedit", hit enter
* Copy & Pase this code, Save as /usr/bin/gmailto
* Hit Alt+F2 again, type "gksudo chmod +x /usr/bin/gmailto", Hit enter
* Open System > Preferences > Preferred Applications
* Set Mail Reader to Custom
* Set the custom command to: "gmailto %s"

This is basically the same as skymt's solution, but also works when no email address is specified.
So it works with mail-notification and other programs that start the default mail-client.

(It's in python because I don't know shell-scripting very well...)

---

### Post by dtmilano on 2006-09-14
Well, here is the bash (oneliner) version:

> #! /bin/bash
# gmailto: to use GMail as your default email-client (bash version)

gnome-open https://mail.google.com/mail/$([ -n "$1" ] && echo "?view=cm&fs=1&to=${1#mailto:}")

Enjoy.

---

### Post by KSDZ on 2006-09-15
I updated mine to support extra arguments like subject=, body=

---

### Post by ubunny on 2006-09-22
> **KSDZ said:**
> ```

#!/usr/bin/python

# gmailto: Workaround to use GMail as your default email-client

import sys
import os

if len(sys.argv) >= 2:
	email = sys.argv[1]
	if email[0:7] == "mailto:": email = email[7:]
        email = email.replace('?','&')
	email = email.replace('&subject=','&su=')
else: email = False

os.execlp("gnome-open","","https://mail.google.com/mail/" + (email and "?view=cm&fs=1&to=%s" %(email) or ""))

```

* Hit Alt+F2, type "gksudo gedit", hit enter
* Copy & Pase this code, Save as /usr/bin/gmailto
* Hit Alt+F2 again, type "gksudo chmod +x /usr/bin/gmailto", Hit enter
* Open System > Preferences > Preferred Applications
* Set Mail Reader to Custom
* Set the custom command to: "gmailto %s"

This is basically the same as skymt's solution, but also works when no email address is specified.
So it works with mail-notification and other programs that start the default mail-client.

(It's in python because I don't know shell-scripting very well...)


Thanks, I'm really liking the python of this, as I'm trying to use and learn python.  However I'm a noob, so I was wondering how to add a subject.  I've tried just gmailto emailaddress subject or &subject or ?subject etc. but gmail doesn't display it.  Could you elaborate slightly further on it's use and I'll learn from the code what it's doing ;)

TIA

---

### Post by Daniel591992 on 2008-02-10
Sorry to bump an old thread, but it's better than making a new one (I guess).

I tried the thing that KSDZ said but was lost at this part, "Save as /usr/bin/gmailto"

So I did, I think.  Then I did this, "gksudo chmod +x /daniel/bin/gmailto/Unsaved Document 1.py", but it's not working. What's wrong here? Thanks in advance.

---

### Post by secretspicy15 on 2008-02-13
> **Daniel591992 said:**
> Sorry to bump an old thread, but it's better than making a new one (I guess).

I tried the thing that KSDZ said but was lost at this part, "Save as /usr/bin/gmailto"

So I did, I think.  Then I did this, "gksudo chmod +x /daniel/bin/gmailto/Unsaved Document 1.py", but it's not working. What's wrong here? Thanks in advance.

Alright, I haven't done this yet but I'm pretty sure your problem is in what you named your file... Instead of naming it "Unsaved Document 1.py" , name it gmailto and put it in the folder ```
/usr/bin/
```

/usr/ should be a directory in your filesystem, NOT your username...

and then ```
gksudo chmod +x /usr/bin/gmailto
```

everything needs to be done thusly in order for the command "gmailto" to run the script... chmod takes the script specified to it and just makes it executable.. it doesn't make a new file or anything like that.. you need to save the script as whatever you want to type to run it...

I hope I understood your trouble and I hope this helps...

---

### Post by SyberKowboy on 2008-02-20
Python script seems to work great! Thanks

---

### Post by tom957 on 2008-07-10
The python script works great for me too. Thanks!

---

