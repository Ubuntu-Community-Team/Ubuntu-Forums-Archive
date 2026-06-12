---
title: "Xsession error: &quot;unsupported number of arguments (2); falling back to default session"
date: 2006-06-12
forum: Desktop Environments
---

### Post by Ulrich Scholz on 2006-06-12
After a recent upgrade, I started getting this error when I log in with one
user with KDM. It pops up in a little window with an "okay" button. After
I click "okay", it comes back, but after the second dismissal, KDE loads
fine. It doesn't happen with every user, just my main one.

I've Googled and can't find anything that helps. Any ideas would be
appreciated.

Ubuntu 6.06

Linux binge 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

__________________
Ulrich Scholz

---

### Post by Ulrich Scholz on 2006-06-16
The error is caused by the following lines in one of my startup scripts (each of them suffices to produce the error):

set meta-flag on
set convert-meta off
set output-meta on

Why? I can execute them in bash without problem.  And the bash man page sais they are legal.  

I reused the startup script from earlier systems, where these lines worked without problem. 

Ulrich

---

### Post by onp on 2008-01-14
Hi.
In my case it was a line that I added to
```

# file:/etc/profile
set bell-style none

```
An unsuccessfull attempt to disable the terminal bell. 

FYI: The "unsupported number of arguments"  is output in 
```

# file:/etc/X11/Xsession.d/20x11-common_process-args
echo $@

```
where I added the echo at the head of the file to see the arguments.

G'day
onp

---

