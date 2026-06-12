---
title: "[SOLVED] New 8.10 need shift+Alt shortcut"
date: 2009-01-08
forum: General Help
---

### Post by niceguy123 on 2009-01-08
Just installed 8.10 on a new laptop. I can figure out how to configure shift+Alt to switch keyboard languages.

---

### Post by Ivo Moelans on 2009-01-08
Open *System&#8594;Preferences&#8594;Keyboard*, tab *Layouts*, button *Other Options...*. The last item is *Layout switching*.
If you didn't know this already: you can add a *Keyboard Indicator* applet to the panel to indicate which keyboard layout you are currently using. You can even make it show flag icons.

---

### Post by Ivo Moelans on 2009-01-08
Double

---

### Post by sendblink23 on 2009-01-08
> **Ivo Moelans said:**
> Double

Read my next post ..  I wrote it wrong

---

### Post by sendblink23 on 2009-01-08
> **Ivo Moelans said:**
> Double

Any idea how to make this letter: Ñ

but not capitalized ... like normally inside Windows it was simply Alt + 164

Any idea how to add that function in Linux(Ubuntu 8.10) ??

Yes I tried the Keyboard method you mentioned...  But I did not understand it one bit... since our *Puerto Rico* Keyboards (from any Computers) are all default normal USA Keyboards, it is not a Spanish keyboard nore anything like that...  so it was all simply  a command in Windows  by using    Alt + ###   a combination of 3 numbers that would create certain characters letter.


Any idea how to create that running this OS?

---

### Post by Ivo Moelans on 2009-01-08
Seems to depend on what kind of keyboard you have: US or US International.
See this Wikipedia article: [http://en.wikipedia.org/wiki/Keyboard_layout]("http://en.wikipedia.org/wiki/Keyboard_layout"). If you have US International you are in luck. The article explains how to do it.

---

### Post by sendblink23 on 2009-01-08
> **Ivo Moelans said:**
> Seems to depend on what kind of keyboard you have: US or US International.
See this Wikipedia article: [http://en.wikipedia.org/wiki/Keyboard_layout]("http://en.wikipedia.org/wiki/Keyboard_layout"). If you have US International you are in luck. The article explains how to do it.


Where in the page does it has to do with LINUX?

Like I Mentioned the First time, in Puerto Rico all Computers come with Natural Default US Keyboards... Exactly how its shown in the Normal US Keyboard Layout in that Wiki page.

Us Keyboard layout: [http://en.wikipedia.org/wiki/File:KB_United_States-NoAltGr.svg](http://en.wikipedia.org/wiki/File:KB_United_States-NoAltGr.svg)

Anyways, what on that page has anything related to what I asked you if you could help me out?

Its really weird it mentions this in the Article of the WIKI-PAGE.. (in the left side of that Keyboard image:

"The US keyboard layout has a second Alt key instead of the AltGr key and does not use any dead keys, and thus offers no way of inputting any sort of diacritic or accent; this makes it unsuitable for all but a handful of languages. On the other hand, the US or UK keyboard layout is occasionally used by programmers in countries where the keys for []{} are located in less convenient positions on the locally customary layout.[4]"

And that is completely WRONG, how come in all normal US Windows OS, we do have *DEAD KEYS* Functions pressing   ALT to input any diacritic or accent as an example for Spanish letters.. the ones I'm only interested on using are these:
ñ, á, é, í, ó, ú

MAC has the same thing but in the Keyboard clicking *Option Key* to make it, in Windows is *Alt Key* and by the way ... it works the same way on any US Windows OS Computer, I used to live in the States for 5 years, I had a computer from over there and it did work the same way.

I have always use my Computer on US English Settings. 

Is there a way to make the Keyboard work in a US Keyboard, inside Linux... through making any changes in System > Prefences > Keyboard

---

### Post by Ivo Moelans on 2009-01-09
> Anyways, what on that page has anything related to what I asked you if you could help me out?

You asked how to make ñ. Well, in the article it says how to do this with a US International keyboard:

> An accent key is activated by pressing it (without holding it), and next pressing the letter that requires an accent. After the two strokes, the single accented character would appear on the screen. Note that only certain letters (such as vowels and n) can have accents in this way. If one wishes to use the normal single quotation mark, caret and so on, one would press the accent key followed by the spacebar; this is a minor inconvenience when using quotation marks and apostrophes before vowels while typing English. Accented characters can be typed with the following combinations:

    * ' + the letter (é), versus ' + space + the letter ('e)
    * ` the letter (è)
    * " the letter (ë), versus " + space + the letter ("e)
    * ^ the letter (ê)
    * **~ the letter (ñ)**


You still haven't said which kind of keyboard you have: Middle North American (look at the pictures) or US International. Do you have two *alt* keys (= Middle North American) or one *Alt* key and one *AltGr* key (= US International)?
If you have the latter (US International) you should be able to make "ñ" by first typing "~" and then "n". As far as I can see the "~" is located on the left of "1".
If you have the former (Middle North American) you can't make accented letters, like it says clearly in the article:

> The US keyboard layout has a second Alt key instead of the AltGr key and does not use any dead keys, and thus offers no way of inputting any sort of diacritic or accent; this makes it unsuitable for all but a handful of languages.

The Windows solution of using ALT and three numbers doesn't work in Linux.

BTW: Alt, Shift & Ctrl are not dead keys as you seem to think, but modifier keys.

---

