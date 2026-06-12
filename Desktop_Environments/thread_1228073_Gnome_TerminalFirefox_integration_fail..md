---
title: "Gnome Terminal/Firefox integration fail."
date: 2009-07-31
forum: Desktop Environments
---

### Post by Numbski on 2009-07-31
So I'm lame.  I still use pine from time to time. :P

Url's are automagically underlined in Gnome terminal.  Clicking them does nothing.  I have Firefox set as my default browser in the gnome config.

So what do I have to do to get these links to launch in firefox when clicked? :)

---

### Post by Simian Man on 2009-07-31
Ctrl-Click them :).

---

### Post by Numbski on 2009-07-31
> **Simian Man said:**
> Ctrl-Click them :).

Son of a....

Okay.  Now that I know what makes it work, is there a way to make it work INTUITIVELY? :)  Ie, click and get the expected behavior? (ie, launch the url in the preferred browser?)

---

### Post by decoherence on 2009-07-31
> **Numbski said:**
> Son of a....

Okay.  Now that I know what makes it work, is there a way to make it work INTUITIVELY? :)  Ie, click and get the expected behavior? (ie, launch the url in the preferred browser?)

Apparently not...

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/296651](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/296651)

As John Hall says; "GNOME developers have perfected the art of ignoring their users." (even though these aren't really gnome developers)

Perhaps you'll change this back in to a bug? Makes sense to me that if you're going to go to the trouble of indicating something is a link, it might as well behave like any other link. Unless someone can come up with a good reason why not (nobody did in the above link... they just refused to acknowledge that it's a bug)

---

### Post by Simian Man on 2009-07-31
I actually like the default behaviour because I copy & paste in the terminal way more than I click on links and it's a pain to try to select a link with the mouse when clicking it follows it.

Ideally there'd be a little popup when you hover over it that says "Ctrl-Click to follow this link" or something.

---

### Post by Numbski on 2009-08-03
> **Simian Man said:**
> I actually like the default behaviour because I copy & paste in the terminal way more than I click on links and it's a pain to try to select a link with the mouse when clicking it follows it.

Ideally there'd be a little popup when you hover over it that says &quot;Ctrl-Click to follow this link&quot; or something.

 Well, at least needs to be a toggle option of some sort.  If a seasoned unix administrator gets stuck like this, what is an end user going to do? :\

---

### Post by Numbski on 2009-08-04
Changed back into a bug.  We'll see how long that lasts though...

---

