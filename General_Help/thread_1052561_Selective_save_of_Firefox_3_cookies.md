---
title: "Selective save of Firefox 3 cookies"
date: 2009-01-27
forum: General Help
---

### Post by jamouneau on 2009-01-27
I want to automatically delete all but a select few cookies when firefox is closed.

I have "Preferences > Privacy > Private Data > "Always clear my private data when I close Firefox" checked with settings to clear cookies.

This, of course, clears even the cookies I wish to keep. 

Is there a Firefox plugin that adds capability to automatically delete all but selected cookies?

My first thought of a workaround was to write a script that copied the cookies.sqlite file (with only the desired cookies) into the default profile and then started firefox, but that doesn't work.

Ideas?

Thanks

---

### Post by dcstar on 2009-01-27
> **jamouneau said:**
> I want to automatically delete all but a select few cookies when firefox is closed.
.........

Can't you set them to be accepted as "Session" cookies that delete in that way?

---

### Post by pedja_portugalac on 2009-01-27
You just have to deselect allow cookies (under preferences - privacy tab) and allow exceptions for those you want to keep, par example ubuntuforums.org or rapidshare.com etc.

---

### Post by TTFN on 2009-01-27
What you are wanting is already built into Firefox.

Set Firefox to accept cookies.  Then set "Keep Until" to "I close Firefox".  That takes care of the cookies being deleted when you close Firefox.  Now, using the button on the right that says "Exceptions", this will open a dialog box where you can enter the sites that you wish to keep even after firefox is closed.

I would also recommend that you remove the check by "Accept third-party cookies", but that is just a recommendation.

Hope this helps. :)

---

### Post by TTFN on 2009-01-27
Pedja, you beat me to the punch.  LOL.   I hadn't thought about disabling cookies all together then allowing exceptions.  By doing this you also disable session cookies, too.  Is that right?

---

### Post by pedja_portugalac on 2009-01-27
> **TTFN said:**
> Pedja, you beat me to the punch.  LOL.   I hadn't thought about disabling cookies all together then allowing exceptions.  By doing this you also disable session cookies, too.  Is that right?

Yes, it's right. Why would you allow some alien cookies talking from your computer to the space? You just have to allow cookies when you really have to. Par example you can't log into ubuntuforums.org if you do not allow they cookie. But ones you have made that exception firefox will clear all but those mentioned in exceptions.

---

