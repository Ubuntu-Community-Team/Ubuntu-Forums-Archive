---
title: "how to copy text from a pdf in Asian language and paste in libreoffice"
date: 2012-02-03
forum: Desktop Environments
---

### Post by jamesbon on 2012-02-03
I have a pdf in an Asian language the pdf can be seen here
[https://rapidshare.com/files/833850670/lalita_sahasranama17_pages.pdf](https://rapidshare.com/files/833850670/lalita_sahasranama17_pages.pdf)

I open this pdf in document viewer and select all now I do a Ctrl+C and open Libreoffice.Here upon pasting I see a random garbled meaning lesss text 
such as 

```
AÉoÉÉsÉaÉÉåmÉÌuÉÌSiÉÉ xÉuÉÉïlÉÑssÉÇbrÉzÉÉxÉlÉÉ
 &#769;ÉÏcÉ¢üUÉeÉÌlÉsÉrÉÉ  &#769;ÉÏqÉiÉç-Ì§ÉmÉÑUxÉÑlSUÏ - 182
 &#769;ÉÏ ÍzÉuÉÉ ÍzÉuÉ-zÉYirÉæYrÉ-ÃÌmÉhÉÏ sÉÍsÉiÉÉÎqoÉMüÉ
LãuÉÇ  &#769;ÉÏ sÉÍsÉiÉÉ SãurÉÉ lÉÉqlÉÉÇ xÉÉWûxÉëMüqÉç eÉaÉÑÈ - 183
CÌiÉ  &#769;ÉÏ oÉë1&#8260;4ÉhQûmÉÑUÉhÉå E &#776;ÉUZÉÉhQåû  &#769;ÉÏ WûrÉaÉëÏuÉÉaÉxirÉ xÉçÇuÉÉSå
 &#769;ÉÏ sÉÍsÉiÉÉxÉWûxÉëlÉÉqÉ xiÉÉå§ÉÇ xÉqmÉÔhÉïqÉç ||

```
How can I see the text correctly in libreoffice. 
A correct document should appear like this
[https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704850858093630402](https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704850858093630402)

I have ibus running so I can easily type text in Hindi as shown here 
[http://www.youtube.com/watch?v=LL7icGNhIfI](http://www.youtube.com/watch?v=LL7icGNhIfI) 
 but I can not do a copy paste from pdf to libreoffice.What is missing here?
I use Ubuntu 11.10 and gnome interface.

---

### Post by andrewc on 2012-02-03
EDIT: Sorry didn't read your post properly. So you can enter Hindi text in Libreoffice properly, but copying and pasting doesn't work properly?

EDIT2: does copying and pasting work properly to Abiword? I came across a post while googling for LibreOffice mangling UTF text that suggests that OO.org can mangle UTF text sent through the clipboard, so it's possible that LibreOffice also suffers from this bug as well. 

This is the post [http://user.services.openoffice.org/en/forum/viewtopic.php?f=25&t=42580](http://user.services.openoffice.org/en/forum/viewtopic.php?f=25&t=42580) 

It's the only a mention of anything similar I could locate in a quick search, though.

EDIT 3: I know this is overkill, but have you tried installing the LibreOffice PDF import filter, importing the PDF and working from there?

ORIGINAL POST BELOW
First, do you have a font installed on your system and selected in LibreOffice that can display the Asian language? Ubuntu should have suitable fonts preinstalled. the Liberation fonts can display most Asian alphabets and there are specific fonts for others, like Hindi and Khmer installed

Secondly, AFAIK, LibreOffice sometime has issues displaying some East Asian alphabets correctly. This is a problem it inherited from OpenOfice.org, something which I hoped had been fixed by now. 

You best solution is probably to install Abiword (if it isn't already), which should work fine with all Asian alphabets, assuming you have the correct fonts installed and selected.

---

### Post by grahammechanical on 2012-02-03
That PDF has two embedded TrueType fonts one of which is BRH Devanagari. Have you tried finding a copy of that font and installing it on your system. 

We can type in different languages in Ubuntu because we have Unicode fonts installed that have character sets for many languages. So, we are able to set different language keyboard layouts.

If the writer on that document had used a Unicode font to create those characters you might not have this problem. Instead he has used a particular font that has been embedded into the PDF document so that the document can be read even on computers that do not have that font installed.

I do not know if this is the answer. I have tried to find this font to download and test out this suggestion but I do not know if I am downloading the right one.

Regards.

---

### Post by jamesbon on 2012-02-03
> **andrewc said:**
> 
EDIT 3: I know this is overkill, but have you tried installing the LibreOffice PDF import filter, importing the PDF and working from there?
 Yes I tried this one and the charachters which I see are like this you can try with pdf I shared at your machine too to confirm it.
```

#&#65533;&#65533;#&#65533;k&#65533;J&#1397;&#65533;&#65533;&#65533;y&#65533;1&#65533;'&#65533;&#65533;*&#65533;#&#65533;N#&#65533;&#65533;U&#65533;&#65533;&#65533;&#65533;#&#65533;o&#65533;>&#65533;!
&#65533;&#65533;=&#65533;0[&#1187;&#65533;&#65533;#NA;b9v&#65533;>&#65533;&#65533;&#65533;T&#65533;&#65533;X&#65533;&#65533;j&#65533;&#65533;##&#65533;l&#65533;#??&#65533;&#65533;&#65533;&#65533;U&#65533;/e&#65533;7#&#65533;dS&#65533;&#65533;n:#&#65533;f&#65533;&#65533;&#65533;7:&#65533;]K&#65533;&#65533;PT
-t#&#65533;l#H#V&#65533;WKc&#65533;&#65533;2r&#65533;&#1831;2&#65533;&#65533;;&#65533;&#65533;x&#65533;#e&#65533;&#65533;-#&#65533;q5#&#1248;qYf&#65533;6c)#&#65533;v-G&#65533;n&#65533;&#65533;#&#65533;os&#65533;&#65533;&#983;I&#65533;&#65533;L &#65533;#&#65533;<&#32061;&#65533;%#@&#65533;&#65533;-&#65533;yzL<#.
*U&#65533;&#65533;#&#65533;&#65533;&#65533;##*e&#65533;&#65533;&#65533;&#65533;r7j&#65533;:&#65533;Kz&#65533;d&#65533;&#65533;&#65533;#&#65533;&#65533;&#65533;|&#65533;&#65533;l&#65533;&#65533;#Z%&#65533;&#65533;+&#65533;.#<#&#65533;

```
> **grahammechanical said:**
> That PDF has two embedded TrueType fonts one of which is BRH Devanagari. Have you tried finding a copy of that font and installing it on your system. 

How did you find that pdf has the font you mentioned?

---

