---
title: "Questions"
date: 2006-09-18
forum: Desktop Environments
---

### Post by suselinux2 on 2006-09-18
Hello This is my first time writing to this forum. I have problems with my ubuntu 6.06:
- I can`t install Automatix. Each time I try to install it, I found written (can`t find package). I have updated repositories. What is wrong?
- Problems with my clock. I`m not able to fix it in my time zone (it is 2  hours after the clock in my time zone). 

Thank you for your help and sorry for my bad English.

---

### Post by Ramses de Norre on 2006-09-18
-Get automatix [here]("http://www.getautomatix.com/").
-About the clock, can't you set the right time zone with ```
gksudo time-admin
```

---

### Post by suselinux2 on 2006-09-18
Hello

I tried, but I had problems....

suselinux2@suselinux2:~$ gksudo time-admin
(time-admin:9558): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(synaptic:9619): Pango-CRITICAL **: pango_font_map_load_fontset: assertion `pango_font_description_get_family (desc) != NULL' failed

(synaptic:9619): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(synaptic:9619): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-WARNING **: pango_shape called with bad font, expect ugly output

(synaptic:9619): Pango-WARNING **: pango_font_get_glyph_extents called with bad font, expect ugly output

(synaptic:9619): Pango-CRITICAL **: pango_cairo_show_glyph_string: assertion `PANGO_IS_CAIRO_FONT (font)' failed

(synaptic:9619): Pango-CRITICAL **: pango_font_map_load_fontset: assertion `pango_font_description_get_family (desc) != NULL' failed

(synaptic:9619): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(synaptic:9619): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_cairo_show_glyph_string: assertion `PANGO_IS_CAIRO_FONT (font)' failed

(synaptic:9619): Pango-CRITICAL **: pango_font_map_load_fontset: assertion `pango_font_description_get_family (desc) != NULL' failed

(synaptic:9619): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(synaptic:9619): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_fontset_foreach: assertion `PANGO_IS_FONTSET (fontset)' failed

(synaptic:9619): Pango-CRITICAL **: pango_cairo_show_glyph_string: assertion `PANGO_IS_CAIRO_FONT (font)' failed


What is wrong?

---

