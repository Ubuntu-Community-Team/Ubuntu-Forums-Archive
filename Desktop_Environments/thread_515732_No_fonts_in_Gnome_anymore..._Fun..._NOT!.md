---
title: "No fonts in Gnome anymore... Fun... NOT!"
date: 2007-08-02
forum: Desktop Environments
---

### Post by cokehabit on 2007-08-02
oh boy, you're going to love this...

Gnome has no fonts anymore, literally: [http://www.cokehabit.org/Screenshot.png](http://www.cokehabit.org/Screenshot.png)

I have reinstalled xorg etc and pango etc but still no luck.

pango-query-modules gives me ```
george@george-laptop:~$ pango-querymodules 
# Pango Modules file
# Automatically generated file, do not edit
#
# ModulesPath = /usr/lib/pango/1.6.0/modules
#
/usr/lib/pango/1.6.0/modules/pango-thai-lang.so ThaiScriptEngineLang PangoEngineLang PangoRenderNone thai:*
/usr/lib/pango/1.6.0/modules/pango-hebrew-fc.so HebrewScriptEngineFc PangoEngineShape PangoRenderFc hebrew:*
/usr/lib/pango/1.6.0/modules/pango-basic-fc.so BasicScriptEngineFc PangoEngineShape PangoRenderFc armenian:* bopomofo:* cherokee:* coptic:* cyrillic:* deseret:* ethiopic:* georgian:* gothic:* greek:* han:* hiragana:* katakana:* latin:* ogham:* old-italic:* runic:* canadian-aboriginal:* yi:* braille:* cypriot:* limbu:* osmanya:* shavian:* linear-b:* ugaritic:* glagolitic:* cuneiform:* phoenician:* common:
/usr/lib/pango/1.6.0/modules/pango-arabic-lang.so ArabicScriptEngineLang PangoEngineLang PangoRenderNone arabic:*
/usr/lib/pango/1.6.0/modules/pango-hangul-fc.so HangulScriptEngineFc PangoEngineShape PangoRenderFc hangul:*
/usr/lib/pango/1.6.0/modules/pango-arabic-fc.so ArabicScriptEngineFc PangoEngineShape PangoRenderFc arabic:*
/usr/lib/pango/1.6.0/modules/pango-basic-x.so BasicScriptEngineX PangoEngineShape PangoRenderX common:
/usr/lib/pango/1.6.0/modules/pango-thai-fc.so ThaiScriptEngineFc PangoEngineShape PangoRenderFc thai:* lao:*
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
/usr/lib/pango/1.6.0/modules/pango-tibetan-fc.so TibetanScriptEngineFc PangoEngineShape PangoRenderFc tibetan:*
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
/usr/lib/pango/1.6.0/modules/pango-syriac-fc.so SyriacScriptEngineFc PangoEngineShape PangoRenderFc syriac:*

```all is good there..

opening gedit with a term gives this still though: 
```
Pango-WARNING **: No builtin or dynamically
loaded modules were found. Pango will not work correctly.
This probably means there was an error in the creation of:
  '/etc/pango/pango.modules'
You should create this file by running pango-querymodules.

(gedit:5987): Pango-WARNING **: pango_shape called with bad font, expect ugly output

(gedit:5987): Pango-WARNING **: pango_font_get_glyph_extents called with null font argument, expect ugly output

(gedit:5987): Pango-WARNING **: pango_font_get_metrics called with null font argument, expect ugly output

(gedit:5987): Pango-WARNING **: _pango_cairo_font_install called with bad font, expect ugly output

```Soooooooooo, anyone have any idea?

---

