---
title: "mini-commander panel applet"
date: 2009-03-30
forum: Desktop Environments
---

### Post by ktmom on 2009-03-30
While looking for reference information to solve a PHP problem I found a quick reference for gnome users on the php.net website.  The post indicated that I should incorporate the following;

```

Quick Reference for Gnome Users
Submitted by Benjamin Curtis (29-Jul-2000)

Here's another search option for Linux users who use Gnome. This is a macro for gnome's mini-commander panel applet (modified from the Yahoo search that comes with the applet):

Regex:
^php: *(.*)$

Macro:
gnome-moz-remote --newwin http://www.php.net/$(echo
'\1'|sed -e ': p;s/+/%2B/;t p;: s;s/\ /+/;t s;: q;s/\"/%22/;t q') 

```

1) I believe this creates a launcher to get me directly to the reference pages. It looks benign to me, but what I don't know would fill a library.  Is this OK to use?

2)  What am I supposed to do with it?

Thanks for any help

---

