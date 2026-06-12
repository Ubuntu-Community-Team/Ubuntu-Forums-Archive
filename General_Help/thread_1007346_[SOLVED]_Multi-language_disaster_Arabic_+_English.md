---
title: "[SOLVED] Multi-language disaster: Arabic + English"
date: 2008-12-10
forum: General Help
---

### Post by itsols on 2008-12-10
Hello everyone, I hope this is the right place for this thread.

Problem:
I've been working with Arabic and English on Windows in the past specially for development. Now that I've (almost) switched (99%) to Ubuntu 7.10, I enabled complex languages on my system, SPECIALLY Arabic. On the settings it shows that I've checked Saudi Arabic.

But here's the issue-
1. I get an UGLY list of languages that makes switching between English/Arabic a disaster. I see Tamil, Thelugu, etc... and I'm not least interested in them as far as my work is concerned. I disabled the above unnecessary languages by unchecking them and they don't seem to go away.

2. I see a keyboard icon at the top panel and it expands into a kind of menu with a list of languages. UNFORTUNATELY it shows Arabic EGYPT and NOT Saudi. Does this mean there's a bug?

3. I tried typing out a test sentence on Open Office odt. I get garbage - most of the keys aren't what they should be!!! This is most disappointing as my work IS bilingual and as I was making the transition to 100% Ubuntu, I did not actually try this until today.

4. Finally, this is PROBABLY NOT SERIOUS but I tend to ACCIDENTALLY hit SHIFT+SPACE and this pop up an annoying keyboard switch making my language change into something that I can't recognise - probably THAI. It is kind of automatic that for example when I type "IT Career" on a document, I tend to hold the SHIFT key continuously until I type "IT" and "C". This results in Shift + space.

I really love this Ubuntu OS and I seriously don't want to go back to Windows, despite the fact that I could NOT find a match for Dreamweaver and PhotoShop.

Any help is much appreciated!

---

### Post by itsols on 2008-12-13
Hello once again. It looks like this is a rare issue and I've observed that this thread did not pick up any attention.

To say it again, I think there's a problem with enabling Arabic (Saudi) on Ubuntu. I've done it but I only get the letters on the keyboard don't correspond to the actual text!!!! I'm starting to think if this is a bug that has NOT got any attention or being reported.

If anyone else out there has a similar problem, please respond with some info so that I can report this as an official bug on Ubuntu.

Please respond so that we can have our favourite open source OS back on track.

It is rather sad that I write this message on Windows as I was constrained due to the language problem.

Hope to hear from you folks... Happy computing!

---

### Post by mohamed_en on 2008-12-17
I have the same problem i hope you find a solution

---

### Post by itsols on 2008-12-18
At last the problem has been solved!!!

I hope everyone else out there with similar issues will benefit by this.

First, I should tell you what to do and what NOT to. Ok... In order to enable Arabic or for that matter any other language, you need to run through System > Administration > Language Support - like I've described before (in the first post of this thread).

Then, the WRONG thing that I did was to go setup SCIM (Smart Common Input Method). This is where the problem lies. So don't do this.

Instead you should right click on the top panel (to newbies from Windows, this is like the taskbar at the top), then select "Add to Panel". Once this is done, simply include the "Keyboard Indicator" and you'll see the current language show up there.

Now to use it, open up ANYTHING that allows you to type - eg: text editor, word processor, etc. Type something in. Now click on the Keyboard indicator on the top panel. Now continue typing in the OTHER language. switch back likewise.

Happy computing!
Khalid

---

