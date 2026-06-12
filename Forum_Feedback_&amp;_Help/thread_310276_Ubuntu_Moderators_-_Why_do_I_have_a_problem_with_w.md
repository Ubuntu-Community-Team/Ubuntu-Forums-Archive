---
title: "Ubuntu Moderators - Why do I have a problem with wiki.ubuntu.com?"
date: 2006-11-30
forum: Forum Feedback &amp; Help
---

### Post by dvarsam on 2006-11-30
Dear Ubuntu Moderators,

I have a problem with "wiki.ubuntu.com"!

I am visiting the "Hardware Support" & try to Edit some Hardware posts I have created...

[https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters](https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters)

I am getting the same error again & again!!!

> ////\\\\ Edit Conflict: Start  ////\\\\

////\\\\ Edit Conflict: End ////\\\\

These "Edit Conflicts" are spread out through my text & I go & erase whenever I see these lines...

I then click save on my Post, only to find that some text have been repeated twice!!!

I then go back again to "Edit Mode" & more "Edit Conflicts" appear on the Text...

I start again the same process:

1. I delete all "Edit Conflict" lines

2. Delete the Text that appeared twice

3. And try to save the document.

Only there is a huge delay...

I wait for 3-4 minutes...

I finally stop the Browser & Reload again...

3 minutes later, the page is uploaded!

But I have **more** "Edit Conflicts"!!!

Can somebody tell me what is wrong?

Cause it is driving me crazy!!!

Thanks.

---

### Post by dvarsam on 2006-11-30
And then I get all these different Revisions created...

So I am Revising a older Revision which needs more Revisioning due to this Error I get...

**The Revisioning process is Endless!** :) ](*,) 

The Firefox Browser takes forever to update, but all other pages I try to connect to, I connect very fast...

I am very tired...

I will check again tomorrow.

I need to sleep now.

Thanks for your attention.

---

### Post by matthew on 2006-12-01
Wow, how frustrating. I wish I could help you. We don't have any direct involvement in the wiki so we're not even capable of looking into the problem directly. Perhaps someone who does will wander past and see this thread, otherwise I have to suggest you look around on the wiki for a maintainer's email address. Sorry.

---

### Post by PriceChild on 2006-12-01
Or check out #ubuntu-doc on irc.freenode.net
 
Pricey

---

### Post by az on 2006-12-01
> **dvarsam said:**
> And then I get all these different Revisions created...

So I am Revising a older Revision which needs more Revisioning due to this Error I get...

**The Revisioning process is Endless!** :) ](*,) 

The Firefox Browser takes forever to update, but all other pages I try to connect to, I connect very fast...

I am very tired...

I will check again tomorrow.

I need to sleep now.

Thanks for your attention.
I tried mucking around with the page and I cannot reproduce your error.

What you descrive is not supposed to happen, anyway.  And the wiki may be slow due to Ubuntu Open week?  Or maybe some system maintenance at the time you were working on your page?

Your browser does not slow the loading of the page - it is python-based preprocessing and it can be quite slow on the server side.  I think the pages are cached so they load faster when read, but to modify them is much slower....

---

### Post by dvarsam on 2006-12-01
Dear Moderators,

Thanks for your replies.

Today, I visited again the following page:

[https://wiki.ubuntu.com/D-Link_DBT-122_USB_Bluetooth_Adapter](https://wiki.ubuntu.com/D-Link_DBT-122_USB_Bluetooth_Adapter)

I managed to Edit the page successfully today!

No "Edit Errors" or anythings...

> It seems to me that the problem occurred due to one of the 2 reasons:

1. After a clean install of Ubuntu v6.10 with no available Updates installed, you go & try to edit the page, or

2. The site wiki.ubuntu.com was being moderated (or applied changes) & it was a temporary Site's problem that got fixed.

Thanks.

P.S.> If the problem was due to case #1 above, you probably could not reproduce it, because you had _already_ installed all the available Updates in your Ubuntu v6.10. I can't think of anything else...

---

### Post by az on 2006-12-01
> **dvarsam said:**
> 
P.S.> If the problem was due to case #1 above, you probably could not reproduce it, because you had _already_ installed all the available Updates in your Ubuntu v6.10. I can't think of anything else...

Editing a wiki page is agnostic to your OS or web browser.  It is a web application and has nothing to do with your OS.

---

### Post by mattheweast on 2006-12-01
The problem you describe occurs when you edit a page and someone else is editing it at the same time. The wiki preserves both edits as an "edit conflict", in order to try to minimise data loss.

When you edit a page and someone else is editing it at the same time, that person has a lock on the page, and the wiki tells you not to edit it for this precise reason: you should follow its advice (make sure you read the text at the top of the page when editing).

---

### Post by matthew on 2006-12-01
Thanks for the answer, Matt!

---

