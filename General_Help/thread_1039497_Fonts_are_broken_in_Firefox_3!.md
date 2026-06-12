---
title: "Fonts are broken in Firefox 3!"
date: 2009-01-14
forum: General Help
---

### Post by NoBugs! on 2009-01-14
[This page shows]("http://www.jesus.org.uk/vault/_symbol.htm") a sample of text that should show up as greek symbols (because it has font-family: symbol) These show up as normal characters, though. It lists a way to fix this in Windows, is there a way to fix it in Linux/Mac also??

This is a very big font bug!! Someone could go to a web page that says 3micro, and they would only see it as "3m" without the font working!

---

### Post by NoBugs! on 2009-01-14
See also this page:
[http://www.alanwood.net/demos/symbol.html](http://www.alanwood.net/demos/symbol.html)
There are many pages on the net with these symbols in normal text with special font required!!

As you can see here, the symbol font won't work if viewed in Linux or Mac:
[http://www.geocities.com/zcphysicsms/chap4.htm](http://www.geocities.com/zcphysicsms/chap4.htm)
[http://www.ampsoft.net/webdesign-l/WindowsMacFonts.html](http://www.ampsoft.net/webdesign-l/WindowsMacFonts.html)

There are some related fonts linked here:
[https://bugzilla.mozilla.org/show_bug.cgi?id=128153#c81](https://bugzilla.mozilla.org/show_bug.cgi?id=128153#c81)

---

### Post by ajcham on 2009-01-14
> **NoBugs! said:**
> This is a very big font bug!!

As described in [the link]("http://www.alanwood.net/demos/symbol.html") on your second post, this is not a browser bug, but bad web design. From the link:
> Symbol font should not be used in Web pages. &#8230; &#8230; &#8230; Specifying Symbol font is contrary to the published specifications, has never been a documented feature of HTML, is not reliable, and should not be done.

I can display Greek text just fine if the author uses Unicode, as they are meant to. For example, if I use the symbols **µ**, **&#931;** or **&#960;**, they should be visible to you without any tinkering.

---

### Post by NoBugs! on 2009-01-14
Ok, my first guess was that this problem was caused by Linux not having the Symbol font installed or configured correctly for viewing.

However, when I test those pages on a Windows pc, the greek symbol font letters appear correctly in IE, but not in Firefox. If the font is installed, shouldn't Firefox also use it?

---

### Post by ajcham on 2009-01-14
> **NoBugs! said:**
> the greek symbol font letters appear correctly in IE, but not in Firefox.

The Symbol font does not use standard character encoding.  It is probably ignored by Firefox (and rightly so) for this reason.

---

### Post by NoBugs! on 2009-01-16
Most of the greek Symbol-font symbols show up in Firefox 2 for mac, but when using Firefox 3 on the same computer it will not show it correctly, it shows up as normal letters. Is there some setting that relates to this?

---

### Post by NoBugs! on 2009-01-17
It seems this is a problem introduced in Firefox 3:
[http://hutchinson.belmont.ma.us/tth/firefox3.html](http://hutchinson.belmont.ma.us/tth/firefox3.html)

---

### Post by ajcham on 2009-01-17
As I said, the problem is with the webpage's design, not the browser.  I think it is right that Firefox should ignore the Symbol font, as should other browsers, otherwise they just encourage a lackadaisical attitude towards web standards.

It is unreliable to use the Symbol font to portray important information.  The meaning is lost on people who are using terminal based browsers, screen-readers or braille output devices.  It would also be lost on people who do not have the font installed, or choose to have their browser override the web developer's font selection. (I fall into both of the latter categories)

It seems to me that any effort exerted in trying to have the Mozilla dev-team reintroduce this 'feature' is misspent.  Better would be to contact the designer or webmaster of the poorly written sites, explaining why their websites are inaccessible to some users and how they can use Unicode to rectify the problem.

---

### Post by NoBugs! on 2009-01-21
> **ajcham said:**
> It is unreliable to use the Symbol font to portray important information.  The meaning is lost on people who are using terminal based browsers, screen-readers or braille output devices.  It would also be lost on people who do not have the font installed, or choose to have their browser override the web developer's font selection. (I fall into both of the latter categories)


I completely agree. What I meant was that I *need* to see a site that uses this sort of symbol-font symbols.

Update: It looks like Firefox, Opera, and Chromium all see this symbol font in the same way. These browsers support userscripts, so [this]("http://userscripts.org/scripts/show/42131") should be able to convert these for normal viewing :)

---

