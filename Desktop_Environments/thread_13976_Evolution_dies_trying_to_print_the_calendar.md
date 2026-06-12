---
title: "Evolution dies trying to print the calendar"
date: 2005-02-03
forum: Desktop Environments
---

### Post by montgomj on 2005-02-03
New to Ubuntu and generally doing well.  However, have been using Evolution for mail and sync to a Palm, and things were fine until I decided to print a calendar (day view).  Evolution dies and goes away.  Can bring it back and print emails fine.  Quit and started at the command line to replicate the problem.  Here is the output


john@ANTFW003:~ $ evolution %

(evolution:11027): evolution-shell-WARNING **: Invalid URI: %

(evolution:11027): GnomePrintCupsPlugin-WARNING **: iconv does not support ppd c haracter encoding: ISOLatin1, trying CSISOLatin1
art_render_invoke: no image source given
art_render_invoke: no image source given
art_render_invoke: no image source given
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
art_render_invoke: no image source given
art_render_invoke: no image source given
art_render_invoke: no image source given
art_render_invoke: no image source given
art_render_invoke: no image source given
art_render_invoke: no image source given
art_render_invoke: no image source given
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
art_render_invoke: no image source given
art_render_invoke: no image source given
art_render_invoke: no image source given
art_render_invoke: no image source given
art_render_invoke: no image source given
art_render_invoke: no image source given
art_render_invoke: no image source given
john@ANTFW003:~ $


Have tried to reinstall Evolution but this does not improve the situation.  Any ideas on how I can fix this printing problem?

All other apps print fine, except Firefox which does not print the neat headers and footers showing the date, URL and such.  I can live with that but would like to print a daily calendar with appointments.

Thanks in advance for any assistance.

---

