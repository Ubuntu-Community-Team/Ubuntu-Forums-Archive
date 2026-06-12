---
title: "How to display these Chinese characters ?"
date: 2009-07-08
forum: Desktop Environments
---

### Post by Physicist on 2009-07-08
Click an arbitrary character on the left part of the webpage, then many characters get shown on the right side, many of which don't display well:

   [http://zi.guoxue.com/](http://zi.guoxue.com/)


What should I do to display them correctly ?

---

### Post by Zorael on 2009-07-08
For CJK characters you need an awesome unicode font to get good bitmap coverage. The Kochi Gothic/Mincho and Sazanami Gothic/Mincho fonts in the repository sort of work well enough with Japanese kanji, but to work well with Chinese you probably need something beefier.

If you have a copy of Windows where these characters display properly, perhaps you could copy the font it uses to render them and import it to your *ubuntu installation? Then you'd need to set up your ~/.fonts.conf to use that font as a fallback when your standard "non-unicode" fonts (DejaVu, Times, whatnot) lack any given character. There should be a thread or two about this here somewhere.

---

### Post by NathanaelCulver on 2009-07-09
I will presume you're using Firefox as your web browser.

In the top menu line click on (V)iew, then Character Encoding (or just type Alt-VC) and make sure Unicode (UTF-8) is selected. There are several different encoding schemes for Chinese -- Big5 is generally used in China (and Hong Kong?), GB32 is Taiwan. My written Chinese isn't too hot, but the page displays correctly for me in Firefox with Unicode selected, and it appears to be traditional Chinese.

Nathanael Culver

---

### Post by NathanaelCulver on 2009-07-09
Correction - it appears to be simplified Chinese.

---

