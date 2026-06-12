---
title: "Why does the file owner have a trailing hyphen in Nautilus?"
date: 2014-08-08
forum: Desktop Environments
---

### Post by giecrilj on 2014-08-08
I have observed that, given my *username*, all file security property windows shown by [Nautilus]("http://live.gnome.org/Nautilus") display *username*- (with a trailing hyphen) for owner.  Why is that?

---

### Post by TheFu on 2014-08-08
I don't see that.
Open a terminal and type "id" - what does that show?

---

### Post by sisco311 on 2014-08-08
Good catch!

I think this is BUG.

It seams that Nautilus tries to display the **user name or comment field **from the /etc/passwd. If it's empty, then it displays username<a space>-(a dash)<a space><an empty string(nothing)> 

I can't check this in Ubuntu, but in Arch Linux with **GNOME nautilus 3.12.2 **if the **user name or comment field**  contains the user name then the dash is not displayed by nautilus. If it contains a comment, then the comment is displayed after the dash.

---

