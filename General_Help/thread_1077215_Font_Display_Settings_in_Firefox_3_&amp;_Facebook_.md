---
title: "Font Display Settings in Firefox 3 &amp; Facebook &amp; Arabic Characters"
date: 2009-02-22
forum: General Help
---

### Post by oarion7 on 2009-02-22
Hello

I have Arabic Language Support installed on Ubuntu 8.04 and am using Firefox 3.0.6. In certain websites, Arabic letters do not connect with each other as they should; they are displayed as separate characters. This is a problem on, for example, Facebook. They display perfectly on many other websites, including Wikipedia.

I found a quasi-solution: EDIT >> PREFERENCES >> CONTENT >> and set default font as "Times New Roman" - Then, ADVANCED button, and unchecked "Allow pages to choose their own fonts, instead of my selections above." This overrided the fonts Facebook was using, switched every font on every website to Times New Roman, and, tada, the Arabic letters now connected.

Question: **is it possible to** leave this font checked, and allow all Western-encoded text to use whichever fonts they want, but **force firefox to override anything written in Arabic to one specific font**?

Or, is there anyone who knows my exact situation, and has found a better solution? I've searched around quite a lot, but not really found anything. There's no problem at all in Firefox on Windows. Kind of tired of having to go to VMwamre to proofread anything I publish in Arabic though.

Thanks!:popcorn:

---

### Post by insert_name_here on 2009-03-23
A greasemonkey script should be able to do it.  Problem is, I don't know javascript or how to write greasemonkey scripts.  

Here's what it'd need to do:

1. Detect if you're at a page with a problematic font OR Detect if you're at a page that is known to be problematic (e.g. facebook.)

2. Detect which characters are problematic (e.g. U0600-06FF)

3. Render those characters in Times New Roman instead of the default font, while rendering all other characters in the default font.

Can anyone write that?  Please?  I'll give you popcorn... :popcorn:

---

