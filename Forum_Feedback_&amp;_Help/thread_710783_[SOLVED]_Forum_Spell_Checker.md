---
title: "[SOLVED] Forum Spell Checker"
date: 2008-02-28
forum: Forum Feedback &amp; Help
---

### Post by Bruce M. on 2008-02-28
Hi Folks,

I noticed while I was using a LiveCD in the process of installing Gutsy that Firefox "automatically" had the Spell Checking function turned on while I visited the forums.

Is this something in the Forums I can do?
Or is it a Firefox thing that I just can't find?

Thanks
Bruce

---

### Post by p_quarles on 2008-02-28
That's part of Firefox, not part of the forums. If you'd like to disable it or change the localization -- just say so.

---

### Post by wieman01 on 2008-02-29
> **p_quarles said:**
> That's part of Firefox, not part of the forums. If you'd like to disable it or change the localization -- just say so.
You like to change the localization or localisation? ;-)

---

### Post by kerry_s on 2008-02-29
sudo apt-get install myspell-en-us

---

### Post by Bruce M. on 2008-02-29
> **kerry_s said:**
> sudo apt-get install myspell-en-us

Let me rephrase this for you:

Firefox "automatically" had the Spell Checking function ***turned on*** while I visited the forums with the LiveCD, but not now that it is installed.

You know, right click in this "create a post" box and select: "Spell check this field", it was "automatically on" with the live CD, not now.

---

### Post by Bruce M. on 2008-02-29
> **p_quarles said:**
> That's part of Firefox, not part of the forums. If you'd like to disable it or change the localization -- just say so.

I would have thought this was a forum function, that's why I posted here.

I'd like to have it turned on by default. (I'm horrible when it comes to typing and create typos a lot.)

How can I turn it on in FF then?

---

### Post by Bruce M. on 2008-02-29
> **wieman01 said:**
> You like to change the localization or localisation? ;-)

localization

Just turned Spell check this field.  :)

---

### Post by Bruce M. on 2008-03-03
> **p_quarles said:**
> That's part of Firefox, not part of the forums. If you'd like to disable it or change the localization -- just say so.

I'd like to "Enable" it by default.
But I have no idea how.  :(

---

### Post by Bruce M. on 2008-03-04
Well, I found out how [here]("http://www.ubuntugeek.com/speed-up-firefox-web-browser.html")

In your location bar, type **about:config**

In the Filter bar that opens: (copy/paste) type: **layout.spellcheckDefault**

Double click on it and change the value to: **2**

Spell checking is now on by default!

Bruce

---

