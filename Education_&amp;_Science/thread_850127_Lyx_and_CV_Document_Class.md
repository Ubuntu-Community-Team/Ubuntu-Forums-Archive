---
title: "Lyx and CV Document Class"
date: 2008-07-05
forum: Education &amp; Science
---

### Post by ugm6hr on 2008-07-05
I've just started experimenting with Lyx in preparation for my thesis.

As a trial, I'm hoping to re-write my CV with Lyx (to ensure that editing it is easy in the future).

However, having installed Lyx (v1.5.3 via aptitude) on Hardy, I'm having difficulty getting templates and classes to work.

As a start, how do I use the modern CV document class?

After starting a new document, going to Document Settings menu, all 3 curriculum vitae classes are "unavailable" - 
> The layout file requested by this document,
moderncv.layout, is not usable. This is probably because a LaTeX
class or style file required by it is not available. See the Customization documentation for more information. LyX will not be able to produce output.
How do I resolve this?

---

### Post by ugm6hr on 2008-07-05
OK.

I appear to have solved this by going into Synaptic and finding all the texlive packages, and then installing some of the -recommended and -extra packages.

I suspect it was texlive-formats-extra that did the trick - but not sure.

New question:

In the eurocv template, all the personal information is in the "preamble" in the Document Settings.

But where is the "Europass Curriculum Vitae" text stored?  I was hoping to delete the Europass bit (since it isn't really relevant for me), but the rest of the layout is great!

I have found the readme here: [http://www.ctan.org/tex-archive/help/Catalogue/entries/europecv.html](http://www.ctan.org/tex-archive/help/Catalogue/entries/europecv.html)  This gives the "notitle" option, but this removes Curriculum Vitae as well as Europass...

---

### Post by kleeman on 2008-07-06
These are latex files. The standard location is 

/usr/share/texmf-texlive/tex/latex

Latex also allows for a local directory as well where you can store customized files. Checkout standard latex docs...Here's a good first place to look:

[http://www.ling.upenn.edu/advice/latex.html](http://www.ling.upenn.edu/advice/latex.html)

---

### Post by mariux^3 on 2009-04-07
Hi,
(first time posting)
i have another question. I want to write my cv (europe) but i ve got this error when exporting in preview:
LaTeX Error: Option clash for package inputenc.
So that in the Document Settings I ve changed the Language Encode to the uff8x. But now when exporting in preview it asks to choose the application to open it (the preview). What should i choose?
Thanks.

---

### Post by eljalill on 2009-04-09
@OP: Before you go to mess around in the latex Macro files... have you tried to the noflag, notitle, nologo options to the documentclass? You can then write whichever heading you want before you begin the europecv environment.

EDIT: Sorry, only just saw that this answer might come a wee bit too late...

---

### Post by Good_Newz on 2009-09-17
For all of you reading this post, this is how you change the title of the CV so that it doesnt say Europass:
put this in your preamble/header(at the very bottom of the preamble/header):
\renewcommand*{\ecvtitle}{\ecv@utf{\Large\textbf{C\ecv@kern u\ecv@kern r\ecv@kern r\ecv@kern i\ecv@kern c\ecv@kern u\ecv@kern l\ecv@kern u\ecv@kern m \ecv@kern V\ecv@kern i\ecv@kern t\ecv@kern a\ecv@kern e}}}

to change any of the left column titles, like the order of the name, the nationality (to Citizenship), you could do this:
\def\ecv@namekey{\ecv@utf{First name/ Surname}}
\def\ecv@nationalitykey{\ecv@utf{Citizenship(s)}}

again in the preamble/header ( at the very bottom).
There are some other that i have changed, just in case you want to change them:
\def\ecv@emailkey{\ecv@utf{Email}}
\def\ecv@telkey{\ecv@utf{Telephone}}
\def\ecv@addresskey{\ecv@utf{Address}}

u can change any environmental macro using the \def\ecv@macro_name{\ecv@utf{New_Title}} 
The macro names could be found in the ecven.def or europecv.cls files.

Cheers
PS:better late than never :)

---

