---
title: "disable auto away in empathy?"
date: 2009-11-27
forum: Desktop Environments
---

### Post by flinkan on 2009-11-27
hey,

i switched from pidgin to empathy and i have now a little annoying problem...
empathy switches allways after 1min my status from online to offline...
and i dont find a option to change this?
my wish is that empathy never change my status... until i do it myself...
is there a way to do this???

thx!

---

### Post by p3tris on 2010-01-14
I have the same problem! Any help plz?

In their faq I found:

How can I disable idling / auto-away?

Switch to Pidgin. (not really, missing documentation)

---

### Post by kellymartinv on 2010-01-21
I don't have a definite answer, but from what I can tell they have just not implemented a way for users to access that feature. It *is* in the code, though. I downloaded the source and patched it a bit to add an entry to the Preferences window, and it was just a matter of enabling the feature. 

Unfortunately, this isn't really the best way to go about it since the built-in Empathy integrates a lot better into Gnome than my version.  And my version broke since the last update to libpurple...

--Edit: oddly enough, I'm looking at the code and the value for enabling auto-away defaults to false.

---

### Post by kellymartinv on 2010-08-29
Since this might still come up in a search, the way I've found to disable auto-away is to use mc-tool. You can request a particular status for an account (i.e. "available"), and if you put it into your crontab to run every 5 minutes or so it will essentially guarantee that presence.

---

### Post by Sepero on 2013-02-08
I was brought to this thread via search, so here's a more updated answer:
[http://askubuntu.com/questions/64181/how-do-i-disable-auto-away-for-online-presence](http://askubuntu.com/questions/64181/how-do-i-disable-auto-away-for-online-presence)

> Install dconf-tools and open dconf-editor. Go to org.gnome.Empathy and change autoaway like you want.


---

### Post by wildmanne39 on 2013-02-08
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

