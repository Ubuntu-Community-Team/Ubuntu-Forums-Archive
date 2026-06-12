---
title: "Change font color while in invert in Evince pdf reader"
date: 2014-12-01
forum: Desktop Environments
---

### Post by Evan I S on 2014-12-01
Greeting!

I am looking for a step by step approach to change font color in evince while it is in invert mode by pressing ctrl + i in Ubuntu 14.04.  I want the font color to be green #00EE00 hex.  When googled I saw some people did it but nowhere on how to.  Thus I came down to post a thread.  One clue I found is that must something to do with c file called "ev-document-misc.c".  I need to know the exact path for it and which line to edit to cause the font color change.  I look forward to hearing from you geeks!

[https://git.gnome.org/browse/evince/tree/libdocument/ev-document-misc.c](https://git.gnome.org/browse/evince/tree/libdocument/ev-document-misc.c)

---

### Post by mc4man on 2014-12-03
That's a source file, any changes would require re-compiling the source.
In any event don't believe that would do you any good, evince is simply inverting all the colors of a pdf, not changing anything in a single color specific manner

---

### Post by Evan I S on 2014-12-06
@mc4man: Thank you for your reply.  Yes even recompiling the source codes with step by step guide will be doable.  Please tell me on how to if you know.  

1. [evince] How to change the font color in evince
[https://mail.gnome.org/archives/evince-list/2011-November/msg00015.html](https://mail.gnome.org/archives/evince-list/2011-November/msg00015.html)

"[COLOR=#2E3436][FONT=Cantarell]I am using debian 6.0 and the version of evince's source code is 2.30.3.[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Cantarell]I modified the evince's source code in order to change the behavior of "Inverted Colors". When I select the "Inverted Colors", the background color will turn to light green instead of simply being inverted:[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Cantarell]  libdocument/ev-document-misc.c:[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Cantarell]     300 void[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     301 ev_document_misc_invert_surface (cairo_surface_t *surface) {[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]           ......[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     323         for (y = 0; y < height; y++) {[/FONT][/COLOR]"


2. How to change pdf background color in evince?
[http://askubuntu.com/questions/191579/how-to-change-pdf-background-color-in-evince](http://askubuntu.com/questions/191579/how-to-change-pdf-background-color-in-evince)

There was a person commented who was able to do it.  Look at the end devav2's comment which pasted below for convenience : 

[COLOR=#444444][FONT=UbuntuRegular]"Yes it is very much possible. After your comment I just went through the evince source code and found this.[ev-document-misc.c]("http://git.gnome.org/browse/evince/tree/libdocument/ev-document-misc.c") holds the inverted color section if (inverted_colors)         cairo_set_source_rgb (cr, 0, 0, 0);     else. So by changing this i think we can achieve our desired color but i haven't compiled and tested this. You can try your luck.[/FONT][/COLOR][COLOR=#444444][FONT=UbuntuRegular] &#8211;  [/FONT][/COLOR][devav2]("http://askubuntu.com/users/49542/devav2")[COLOR=#999999][FONT=UbuntuRegular][Sep 23 '12 at 6:15]("http://askubuntu.com/questions/191579/how-to-change-pdf-background-color-in-evince#comment238146_191582")"[/FONT][/COLOR]

---

### Post by Evan I S on 2014-12-06
@mc4man: Thank you for your reply.  Yes even recompiling the source codes with step by step guide will be doable.  Please tell me on how to if you know.  

1. [evince] How to change the font color in evince
[https://mail.gnome.org/archives/evince-list/2011-November/msg00015.html](https://mail.gnome.org/archives/evince-list/2011-November/msg00015.html)

"[COLOR=#2E3436][FONT=Cantarell]I am using debian 6.0 and the version of evince's source code is 2.30.3.[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Cantarell]I modified the evince's source code in order to change the behavior of "Inverted Colors". When I select the "Inverted Colors", the background color will turn to light green instead of simply being inverted:[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Cantarell]"libdocument/ev-document-misc.c:[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Cantarell]     300 void[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     301 ev_document_misc_invert_surface (cairo_surface_t *surface) {[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]           ......[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     323         for (y = 0; y < height; y++) {[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     324                 guchar *p = data + y * rowstride;[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     325 [/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     326                 for (x = 0; x < width; x++) {[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     327                         //p[0] = 255 - p[0];[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     328                         //p[1] = 255 - p[1];[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     329                         //p[2] = 255 - p[2];[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     330                         // this will turn the background color to light green[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     331                         p[0] = 204; // cc[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     332                         p[1] = 232; // e8[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     333                         p[2] = 207; // cf[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     334                         p += 4;[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     335                 }[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Cantarell]     336         }[/FONT][/COLOR]"


2. How to change pdf background color in evince?
[http://askubuntu.com/questions/191579/how-to-change-pdf-background-color-in-evince](http://askubuntu.com/questions/191579/how-to-change-pdf-background-color-in-evince)

There was a person commented that was able to do it.  Look at the end devav2's comment that is : 

[COLOR=#444444][FONT=UbuntuRegular]"Yes it is very much possible. After your comment I just went through the evince source code and found this.[ev-document-misc.c]("http://git.gnome.org/browse/evince/tree/libdocument/ev-document-misc.c") holds the inverted color section if (inverted_colors)         cairo_set_source_rgb (cr, 0, 0, 0);     else. So by changing this i think we can achieve our desired color but i haven't compiled and tested this. You can try your luck.[/FONT][/COLOR][COLOR=#444444][FONT=UbuntuRegular] &#8211;  [/FONT][/COLOR][devav2]("http://askubuntu.com/users/49542/devav2")[COLOR=#999999][FONT=UbuntuRegular][Sep 23 '12 at 6:15]("http://askubuntu.com/questions/191579/how-to-change-pdf-background-color-in-evince#comment238146_191582")"[/FONT][/COLOR]

---

### Post by mc4man on 2014-12-06
As far as askubuntu - "There was a person commented that was able to do it" Not really, he offered no changes & didn't try 
As far as the other link.
In that case the person commented out (//) the current /* Change the RGB values*/ section & inserted a single defined color. Sounds like he/she wasn't totally pleased with the results.

In any event that was several years ago & while a similar section of code is still there I don't think those changes are going to achieve much, may just alter the thumbnails in invert

---

