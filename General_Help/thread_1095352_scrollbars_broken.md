---
title: "scrollbars broken"
date: 2009-03-13
forum: General Help
---

### Post by joeyknuccione on 2009-03-13
I can't get a horizontal scrollbar in Firefox3. In looking on the net it says something about a chrome css file, but I got no clue what that is

How can I get my horizontal scrollbar back?

---

### Post by viljun on 2009-03-13
What web page are you viewing? Can you tell the address?

I mean - you wrote to beginner section - so are you sure the web page you're viewing is so big the browser should display the bar?

---

### Post by joeyknuccione on 2009-03-13
> **viljun said:**
> What web page are you viewing? Can you tell the address?

I mean - you wrote to beginner section - so are you sure the web page you're viewing is so big the browser should display the bar?
It happens on any page really.

Say this: I open a page, and I resize FF to be 2/3 of my screen. On the other 1/3 I use a text editor to reply to stuff in the 2/3 or FF section.

So, if I take FF from whole screen down to 2/3, I used to have a horizontal scroll, now I don't. This occurs even if I resize down to a tiny fraction of the screen as well.

---

### Post by viljun on 2009-03-13
how about: sudo dpkg-reconfigure firefox

---

### Post by viljun on 2009-03-13
... or save your bookmarks etc and do this:

sudo apt-get purge firefox (this should erase firefox)
sudo apt-get install firefox (this should install it back)

---

### Post by joeyknuccione on 2009-03-13
> **viljun said:**
> ... or save your bookmarks etc and do this:

sudo apt-get purge firefox (this should erase firefox)
sudo apt-get install firefox (this should install it back)

Killed all my settings but it worked

'Preciate it much, will be looking for the thank you button and the solved button

---

