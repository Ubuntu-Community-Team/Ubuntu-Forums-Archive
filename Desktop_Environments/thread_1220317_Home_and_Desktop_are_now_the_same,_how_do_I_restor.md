---
title: "Home and Desktop are now the same, how do I restore the original settings"
date: 2009-07-22
forum: Desktop Environments
---

### Post by lindsay7 on 2009-07-22
I was moving some Dropbox files around and somehow my Desktop directory is now my Home directory.  In other words I no longer have a Desktop and a Home Directory.  Anything I put in Home is put on the Desktop, and there is no separate Desktop loacation.

How do I get back to the original settings?

---

### Post by merlinus on 2009-07-22
Too much real ale, eh?

You might try creating a Desktop folder in your /home folder, with the same permissions.

---

### Post by raf_kig on 2009-07-22
Try the following:

- fire up gconf-editor
- go to /apps/nautilus/preferences/
- see if desktop_is_home_dir is checked. if it is: uncheck it, problem solved

Regards,

raf

---

### Post by lindsay7 on 2009-07-22
Well, those things did not get my Desktop folder back, so I will just run my restore home partition option form my backup. It will take an hour or so but it is painless. I was hoping I could do this with a click or two, anyway thanks for looking at my problem.  

This all started because Dropbox was showing up on my Desktop unexpectedly and I could not figure out how to get it off.

---

### Post by ASK87 on 2009-07-22
To know what is your home directory try printing it using

```
echo $HOME
```
I think you can override it

---

