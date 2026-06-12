---
title: "Firefox keeps hanging."
date: 2011-03-05
forum: Desktop Environments
---

### Post by DipreSantana on 2011-03-05
Firefox turns black and white while I'm using it, sometimes when I'm watching videos, sometimes when I click on a new page, sometimes when I'm doing nothing, what could be causing this? I'm using Ubuntu 10.10 - 64 bit.

---

### Post by Krytarik on 2011-03-06
Try Firefox with a fresh user profile, therefore rename your profile directory "~/.mozilla/firefox/*.default".

---

### Post by SVEN1 on 2011-03-06
ever since upgrading Ubuntu to the latest Firefox 3.614, Firefox is slower loading or at times hangs  and will not load a website as the older version. Rather annoyed with Firefox at this point. The only reason I still use it is for sites that needs a password. Firefox will store the password and it's protected from peering eyes with a Master password.

I have installed Chromium and it runs faster than FF and doesn't hang. Only thing that bugs me about Chromium you don't have the ability to hide your passwords with a master password.

By the way tried every tweak on FF but no real difference seen.

At this point anytime FF hangs, I just open Chromium. By the way I was able to import FF bookmarks and book mark bar into Chromium so it's identical to FF layout.

Had the same hang problem with my wife's computer using the newest Firefox in Win XP, she was getting pissed with the way it was hanging or slowness. Got tired of hearing her complaining and installed Chrome and she loves it.

I here that the newer Firefox slowness hang situation is a common complaint.

---

### Post by mwl128340 on 2011-03-06
im not sure if this will help you or not but i was experiencing the same problem with firefox recently.  im not sure what happened but i guess the flash i had installed caused ff to hang up.  if you search for the add-on flash aid in firefox addons, it may cure your problems as far as flash is concerned. it helped mine and has been running like a champ since. good luck

---

### Post by mwl128340 on 2011-03-06
[https://addons.mozilla.org/en-US/firefox/search/?q=flash%20aid](https://addons.mozilla.org/en-US/firefox/search/?q=flash%20aid)    here is a link to flash aid

---

### Post by SVEN1 on 2011-03-06
> **mwl128340 said:**
> [https://addons.mozilla.org/en-US/firefox/search/?q=flash%20aid](https://addons.mozilla.org/en-US/firefox/search/?q=flash%20aid)    here is a link to flash aid

tried it a little while ago, now my Adobe plug crashes at Utube and I have to refresh the page to get the vid to play.

---

### Post by DipreSantana on 2011-03-06
I already have Flash-Aid, Chrome does the same thing.

---

### Post by Krytarik on 2011-03-06
> **DipreSantana said:**
> I already have Flash-Aid, Chrome does the same thing.
Does disabling Flash help, for example in Firefox with the extensions Flashblock or Prefbar?

EDIT: Of course you can also disable Flash via "Tools -> Add-ons -> Plugins" to test it. I didn't thought of it in the first place because I usually use those extensions, since I have a bit older machine.

---

### Post by SVEN1 on 2011-03-06
> **DipreSantana said:**
> I already have Flash-Aid, Chrome does the same thing.

I'm using Chromium and do not have the problem in that browser

---

### Post by DipreSantana on 2011-03-07
> **SVEN1 said:**
> I'm using Chromium and do not have the problem in that browser
Chromium does not work with the add ons I like, I will try a new profile in Firefox and see how that works, removing Flash is not an option I like, maybe if HTML5 was up and running, but, it still has a long way to go.

---

### Post by Krytarik on 2011-03-07
> **DipreSantana said:**
> Chromium does not work with the add ons I like, I will try a new profile in Firefox and see how that works, removing Flash is not an option I like, maybe if HTML5 was up and running, but, it still has a long way to go.
Since you said that you experience the same issue in Chrome, I don't believe it's related to Firefox' user profile. As for Flash, I said "test", just to narrow down the issue.

---

### Post by DipreSantana on 2011-03-07
> **Krytarik said:**
> Since you said that you experience the same issue in Chrome, I don't believe it's related to Firefox' user profile. As for Flash, I said "test", just to narrow down the issue.


Then what could be the issue, if it's not flash and it's not the user profile?  Could it be because there are multiple versions of Firefox in the usr/lib folder?

---

### Post by Krytarik on 2011-03-07
> **DipreSantana said:**
> Then what could be the issue, if it's not flash and it's not the user profile?  Could it be because there are multiple versions of Firefox in the usr/lib folder?
Did you rule Flash out then, by disabling it!? Do you have more than one fully installed (!) Firefox versions in the "lib" directory? I bet, no.

---

### Post by DipreSantana on 2011-03-08
> **Krytarik said:**
> Did you rule Flash out then, by disabling it!? Do you have more than one fully installed (!) Firefox versions in the "lib" directory? I bet, no.

There's only one full version of Firefox in the lib, and it's not Flash, it's really starting to annoy me, any more ideas?

---

### Post by Krytarik on 2011-03-08
There are new updates out now, for both Firefox and Chromium. Please upgrade your packages and check again.

---

### Post by DipreSantana on 2011-03-10
> **Krytarik said:**
> There are new updates out now, for both Firefox and Chromium. Please upgrade your packages and check again.

I switched to a Chrome beta release, everything seems to be working fine so far.

---

