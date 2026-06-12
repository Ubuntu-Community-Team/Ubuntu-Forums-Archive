---
title: "Select all when clicking text box?"
date: 2006-04-28
forum: Desktop Environments
---

### Post by techstop on 2006-04-28
Hi all. Searched for this one but couldn't find anything. 

In Windows (sorry) when you click on a text box, eg. dialog box, address bar of Firefox, search box etc, all the text in the box is automatically selected, which makes it very easy to type in new URL's, search queries straight over the top. In Ubuntu, I need to click in the box, select all the text and then start typing. How can I fix this in Ubuntu 5.10? Cheers.

---

### Post by louis_nichols on 2006-04-28
Are you talking about any particular piece of software? I'm asking because, GUI wise, firefox may behave differently from the rest of the apps in Gnome. In addition to this, firefox actually behaves in the exact manner you just described: one click on the address-field selects all (or is that 2 clicks?... hm... I don't have my Ubuntu close rght now, sorry).

With the rest of the apps, it's true one click doesn't always do it (it's actually the same with windows in almost all other edit boxes, except the address field in IE - it's just the more practical way), but 2 clicks will.

**EDIT:**typos and a little addition

---

### Post by techstop on 2006-04-28
Hmmm, I guess I was talking about all apps, but I've just seen that double-clicking works as I want. That will do for now. Thanks for your help. Didn't think to try clicking a second time! ;)

---

### Post by techstop on 2006-08-26
Sorry to reply to my own very old thread, but I have finally figured this one out!

In Firefox, type about:config in the address bar to access the config options. Then, change the below setting to true;

browser.urlbar.clickSelectsAll

That's it! Too easy.

apologies if this is captain obvious material to some of you, it was bugging me for ages!:D

---

### Post by ryu kun on 2006-09-08
I just wanted to thank you for adding this solution to your thread after you found it.

I was wondering how to do that. However I decided to keep the settings as they are, because it would be harder to click a specific point in the address line, however it is not hard to double click.

Anyway, thank you for sharing this information.

---

### Post by techstop on 2006-09-08
Aha, no worries... :-D

---

