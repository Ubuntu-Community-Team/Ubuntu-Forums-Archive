---
title: "Xresources &amp; Emacs"
date: 2009-04-24
forum: General Help
---

### Post by bitskrieg on 2009-04-24
Putting the Emacs settings in an .Xdefaults file in the home directory, the using the command:
```
$ xrdb -merge .Xdefaults
```works fine. 
What I want is global settings, normally placed in the /etc/X11/Xresources file.
I noticed that Debian/Ubuntu has a directory app-defaults where each application, like Emacs, can have its own X settings placed. I created an Emacs file with options like:
```
Emacs.toolBar: 0
```and then logged out, and logged back in, but it didn't work.
I tried naming it emacs instead, I also rewrote the options to:
*toolBar: 0
but this wasn't recognized either.
What am I doing wrong here?

---

### Post by gettinoriginal on 2009-04-30
I do not know about macs, so just trying to help by 
bumping  ;)

---

### Post by Brandon Williams on 2009-05-01
Try using strace to figure out where emacs is actually looking to find the app-defaults directory. For example, this:
```
$ strace xclock 2>&1 | grep app-defaults
```
shows me the places where xclock looks for its app-defaults files, and the order in which they are searched.

It may be that emacs just doesn't look in /etc/X11/app-defaults/, which would be a bug to be reported against the specific emacs version that you're using.

---

### Post by Arndt on 2009-05-01
> **Brandon Williams said:**
> Try using strace to figure out where emacs is actually looking to find the app-defaults directory. For example, this:
```
$ strace xclock 2>&1 | grep app-defaults
```
shows me the places where xclock looks for its app-defaults files, and the order in which they are searched.

It may be that emacs just doesn't look in /etc/X11/app-defaults/, which would be a bug to be reported against the specific emacs version that you're using.

I tried this, and Emacs does read the file, but it doesn't perform what it says, for me either.

---

