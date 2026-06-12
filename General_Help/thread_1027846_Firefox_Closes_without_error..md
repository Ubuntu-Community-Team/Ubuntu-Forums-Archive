---
title: "Firefox Closes without error."
date: 2009-01-01
forum: General Help
---

### Post by Sucrac on 2009-01-01
Firefox (3.0.5) closes when loading certain pages. Normally it happens when following links. I have disabled all pug-ins, and add-ons. It only happens to certain pages/links. Running it from the command line in safe mode produces this error:

> firefox -safe-mode
The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 30577 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.) 

I have tried re-installing, and I even tried to force version (3.0.3) but that threw another error altogether. Sounds like a bad RAM stick to me, but the memory check produces no errors. Any ideas / has anyone else seen this problem? Any help would be appreciated.

---

### Post by stderr on 2009-01-01
Did this begin after upgrade to 8.10?

Doubt this is it, but what if you try removing "wins" from the hosts: line of /etc/nsswitch.conf? (You'll need to be root, e.g.

```
sudo vim /etc/nsswitch.conf
```
or
```
gksudo gedit /etc/nsswitch.conf
```
depending on your preferences

---

### Post by Sucrac on 2009-01-01
"wins" doesn't exist in that file. For the record: this is a fresh install of 8.10.

Thank you though.

---

### Post by stderr on 2009-01-01
Oh well. I'd assume it's another example of FF's buggy handling of large images. There are quite a lot of bug reports on it.

I've tried debugging FF, but I can't get it to break on gdk_x_error. I've heard that even those who compile FF with debug symbols still struggle. Are there some particular links you've noticed this happening on that we could test too?

---

