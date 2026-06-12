---
title: "Pango-WARNING: shape engine failure"
date: 2006-08-24
forum: Desktop Environments
---

### Post by ibot on 2006-08-24
Hi folks!

I have a real bad problem with the Ubuntu Dapper Drake 6.06 Release. After one update the system went mad. It does not display the fonts properly.

> 
Pango-WARNING **: shape engine failure, expect ugly output. the off ending font is 'DejaVu Sans Mono 9.9990234375' 

So it says when I start i. e. gvim, etc.

Almost my complete gnome desktop just show squares for each letter. I can't read anything.

Firefox, Openoffice seem to bee okay, Text is readable as usual.

I did a "dpgk-reconfigure fontconfig", removed the font packages, etc.

When I remove the font folder and restart the x-server some menus get readable again, but that's surely no solution.

Does anyone have the slightest idea how to resolve this?
I don't get a clue, even googling the error message points to cyrillic/asian sites ... *ironic* great, I am soooo good at reading russian or chinese :-)

---

### Post by ibot on 2006-08-29
Sorry for pushing the thread. I usually don't do that, but I'm pretty stuck.
I'm using M$ windows right now. That's an unbearable situation.
If no one has a clue what's going on on my system, does anyone have at least an idea what I could check or where I should dig in the system? If you need some configuration to tell anything, please ask.
Thank you!

---

### Post by ibot on 2006-09-01
So, as no one has a clue I'll do the windows way: New Installation
Sad but the only option I have now.

](*,)

---

### Post by khughitt on 2007-05-02
/bump

I'm getting the same error. I've noticed it twice today: it has crashed mysql-admin, and now also acidrip (which i have just tried for the first time)..

```

AcidRip message - No configuration file found, nevermind.
Pango-WARNING **: shape engine failure, expect ugly output. the offending font is 'DejaVu Sans Not-Rotated 0' at /usr/bin/acidrip line 60.
Segmentation fault
```

Both crashes occur when i try certain actions (in mysql- backing up a database, and in acidrip, backing up a dvd). I tried a different font to see if that helped in acidrip case, but the crash still occured.

Here is the output of pango-querymodules in case it is of any help..

```
$ **pango-querymodules **
# Pango Modules file
# Automatically generated file, do not edit
#
# ModulesPath = /usr/lib/pango/1.6.0/modules
#
/usr/lib/pango/1.6.0/modules/pango-arabic-lang.so ArabicScriptEngineLang PangoEngineLang PangoRenderNone arabic:*
/usr/lib/pango/1.6.0/modules/pango-arabic-fc.so ArabicScriptEngineFc PangoEngineShape PangoRenderFc arabic:*
/usr/lib/pango/1.6.0/modules/pango-basic-fc.so BasicScriptEngineFc PangoEngineShape PangoRenderFc armenian:* bopomofo:* cherokee:* coptic:* cyrillic:* deseret:* ethiopic:* georgian:* gothic:* greek:* han:* hiragana:* katakana:* latin:* ogham:* old-italic:* runic:* canadian-aboriginal:* yi:* braille:* cypriot:* limbu:* osmanya:* shavian:* linear-b:* ugaritic:* glagolitic:* cuneiform:* phoenician:* common:
/usr/lib/pango/1.6.0/modules/pango-basic-x.so BasicScriptEngineX PangoEngineShape PangoRenderX common:
/usr/lib/pango/1.6.0/modules/pango-hangul-fc.so HangulScriptEngineFc PangoEngineShape PangoRenderFc hangul:*
/usr/lib/pango/1.6.0/modules/pango-hebrew-fc.so HebrewScriptEngineFc PangoEngineShape PangoRenderFc hebrew:*
/usr/lib/pango/1.6.0/modules/pango-indic-fc.so devaScriptEngineFc PangoEngineShape PangoRenderFc devanagari:*
/usr/lib/pango/1.6.0/modules/pango-indic-fc.so bengScriptEngineFc PangoEngineShape PangoRenderFc bengali:*
/usr/lib/pango/1.6.0/modules/pango-indic-fc.so guruScriptEngineFc PangoEngineShape PangoRenderFc gurmukhi:*
/usr/lib/pango/1.6.0/modules/pango-indic-fc.so gujrScriptEngineFc PangoEngineShape PangoRenderFc gujarati:*
/usr/lib/pango/1.6.0/modules/pango-indic-fc.so oryaScriptEngineFc PangoEngineShape PangoRenderFc oriya:*
/usr/lib/pango/1.6.0/modules/pango-indic-fc.so tamlScriptEngineFc PangoEngineShape PangoRenderFc tamil:*
/usr/lib/pango/1.6.0/modules/pango-indic-fc.so teluScriptEngineFc PangoEngineShape PangoRenderFc telugu:*
/usr/lib/pango/1.6.0/modules/pango-indic-fc.so kndaScriptEngineFc PangoEngineShape PangoRenderFc kannada:*
/usr/lib/pango/1.6.0/modules/pango-indic-fc.so mlymScriptEngineFc PangoEngineShape PangoRenderFc malayalam:*
/usr/lib/pango/1.6.0/modules/pango-indic-fc.so sinhScriptEngineFc PangoEngineShape PangoRenderFc sinhala:*
/usr/lib/pango/1.6.0/modules/pango-indic-lang.so devaIndicScriptEngineLang PangoEngineLang PangoRenderNone devanagari:*
/usr/lib/pango/1.6.0/modules/pango-indic-lang.so bengIndicScriptEngineLang PangoEngineLang PangoRenderNone bengali:*
/usr/lib/pango/1.6.0/modules/pango-indic-lang.so guruIndicScriptEngineLang PangoEngineLang PangoRenderNone gurmukhi:*
/usr/lib/pango/1.6.0/modules/pango-indic-lang.so gujrIndicScriptEngineLang PangoEngineLang PangoRenderNone gujarati:*
/usr/lib/pango/1.6.0/modules/pango-indic-lang.so oryaIndicScriptEngineLang PangoEngineLang PangoRenderNone oriya:*
/usr/lib/pango/1.6.0/modules/pango-indic-lang.so tamlIndicScriptEngineLang PangoEngineLang PangoRenderNone tamil:*
/usr/lib/pango/1.6.0/modules/pango-indic-lang.so teluIndicScriptEngineLang PangoEngineLang PangoRenderNone telugu:*
/usr/lib/pango/1.6.0/modules/pango-indic-lang.so kndaIndicScriptEngineLang PangoEngineLang PangoRenderNone kannada:*
/usr/lib/pango/1.6.0/modules/pango-indic-lang.so mlymIndicScriptEngineLang PangoEngineLang PangoRenderNone malayalam:*
/usr/lib/pango/1.6.0/modules/pango-indic-lang.so sinhIndicScriptEngineLang PangoEngineLang PangoRenderNone sinhala:*
/usr/lib/pango/1.6.0/modules/pango-khmer-fc.so KhmerScriptEngineFc PangoEngineShape PangoRenderFc khmer:*
/usr/lib/pango/1.6.0/modules/pango-syriac-fc.so SyriacScriptEngineFc PangoEngineShape PangoRenderFc syriac:*
/usr/lib/pango/1.6.0/modules/pango-thai-fc.so ThaiScriptEngineFc PangoEngineShape PangoRenderFc thai:* lao:*
/usr/lib/pango/1.6.0/modules/pango-thai-lang.so ThaiScriptEngineLang PangoEngineLang PangoRenderNone thai:*
/usr/lib/pango/1.6.0/modules/pango-tibetan-fc.so TibetanScriptEngineFc PangoEngineShape PangoRenderFc tibetan:*

```

Any help would be greatly appreciated,
Thanks!

---

### Post by saiftynet on 2007-05-02
I had exactly the same problem in my fedora core 6. 
I resolved it by installing pango_sdl.
Others seem to have managed by reintsalling fontconfig or reverting to an older version

Saif

---

### Post by lakerssuperman on 2007-05-03
When I run Acidrip and try to read the TOC of a DVD to rip I get

"Pango-WARNING **: shape engine failure, expect ugly output. the offending font is 'DejaVu Sans Not-Rotated 0' at /usr/share/perl5/AcidRip/signals.pm line 203.
Segmentation fault (core dumped)"

I have tried installing the pango-sdl package and reinstalling font-config but it has had no effect.  I am running Feisty and have it completely up to date.  It is very strange because Acidrip was working fine and now it isn't.  All that changed was I updated the system so I suspect that one of the packages is messed up.

---

### Post by rohan! on 2007-05-05
ditto

trying to use acidrip and it's crashing when i attempt to load up the table of contents.

```
Pango-WARNING **: shape engine failure, expect ugly output. the offending font is 'DejaVu Sans Not-Rotated 0' at /usr/bin/acidrip line 60.
Segmentation fault (core dumped)
```

---

### Post by azote on 2007-05-16
> **rohan! said:**
> ditto

trying to use acidrip and it's crashing when i attempt to load up the table of contents.

```
Pango-WARNING **: shape engine failure, expect ugly output. the offending font is 'DejaVu Sans Not-Rotated 0' at /usr/bin/acidrip line 60.
Segmentation fault (core dumped)
```

I have this same issue ... but with another font
the offending font is '**Bitstream Vera Sans 0**' at /usr/bin/acidrip line 60.

---

