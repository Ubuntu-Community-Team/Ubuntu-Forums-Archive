---
title: "a question regarding LaTeX"
date: 2011-12-27
forum: Education &amp; Science
---

### Post by thelastblack on 2011-12-27
hey
i use LaTeX (texlive) and TeXMaker for writing, and i have no problem with it.
but i want one thing: an ability name "reverse search".
in windows, my friends use MikTex and texmaker and sumatraPDF and when they get PDF output, if they double click anywhere on PDF file, it will go to texmaker in related line.
i want the same in ubuntu.
i am using 11.10 and texlive and texmaker and the built-in viewer of texmaker. in viewer, i have the option of going back to the line, but this doesnt work.
anyone has any suggestion?
thx in advance

---

### Post by cotcot on 2012-01-02
I was looking for the same. [[COLOR="Blue"]Here[/COLOR]]("http://stackoverflow.com/questions/2543185/latex-inverse-search-from-a-pdf-in-okular-to-texmaker") is a thread on the subject.
I have not tried it yet.

---

### Post by gleedadswell on 2012-01-23
> **cotcot said:**
> I was looking for the same. [[COLOR="Blue"]Here[/COLOR]]("http://stackoverflow.com/questions/2543185/latex-inverse-search-from-a-pdf-in-okular-to-texmaker") is a thread on the subject.
I have not tried it yet.

For the original poster, the source quoted above is to get it to work with emacs, not texwriter.  So if you really like texwriter and aren't willing to learn emacs (which has quite a learning curve) this might not be the solution you are looking for.

I tried the instructions, but they didn't quite work for me.  I did a fair bit of fiddling with it and finally got it to work.  So I'm reproducing that source here with my edits:

1. First, install Okular, the KDE PDF viewer. This may require a huge number of KDE libraries. Evince is nice but doesn&#8217;t support inverse PDF search yet.  You also need the auctex package installed.  It isn't automatically installed as part of emacs, so make sure you've got it.  Make sure you have Emacs 23.  It isn't a default in most Ubuntu versions.

2. In okular, go to Settings > Configure Okular > Editor and change the editor to "emacs client", and the command to "emacsclient -a emacs &#8211;no-wait +%l %f".

3. We need to make some changes to .emacs which is a hidden file in your home directory.  We have to start emacs in server mode so that okular can talk to it. Add this line somewhere in your .emacs file: 
(server-start) 
The next time emacs is started, it will be in server mode.

4. When emacs compiles using latex, it has to include "source specials". Roughly, this is an index connecting every position in the PDF file to a line number in the source file. To create the index, a latex package called synctex must be installed. Under recent Ubuntu versions this is included in the package texlive-extra-utils, so make sure that&#8217;s installed.

5. To tell emacs to always use PDF (i.e. compile with pdflatex instead of latex) insert the line 
(add-hook 'LaTeX-mode-hook 'TeX-PDF-mode)
into your .emacs.  This step is optional if you don't want to automatically pick PDF each time, but everything in this post pertains to PDF.

6. Tell emacs to compile using source specials by adding the following line to your .emacs: '(LaTeX-command "latex -synctex=1")  Alternatively, when editing a tex file, go to the menu LaTeX > Customize AUCTeX > Extend this menu; Then reopen the menu (which will have changed structure a bit) LaTeX > Customize AUCTeX > TeX Command > LaTeX Command, then change"latex" to "latex -synctex=1" and click "Save for future sessions".  Then exit emacs [I couldn't get the direct edit of .emacs to work, but using the AUCTex customization menu did work for me]

7. Reopen your .tex file in emacs.  Open the customization menu LaTeX > Customize AUCTeX > Extend this menu; and again LaTeX > Customize AUCTeX > TeX Command > TeX View > Tex View Program List.  This item will be empty except for some somewhat cryptic instructions.  It has an insertion point marked by a button with "INS" on it.  Click this.  Several fields will be created.  In the Name field enter "okular" without quotes.  In the Command field enter

okular %o

Click "save for future sessions" and "set for current session".  Then click Exit.

8. Yet again go into the customization menu LaTeX > Customize AUCTeX > TeX Command > TeX View > TeX Program Selection.  You will see a number of fields.  One set will list output-pdf in one field.  On the line of fields below this click the Value Menu button beside Viewer:  One of the options you are given should be okular.  Select this.  Again "save for future sessions" and "set for current session".

Now test it out.  In the directory with your .tex file delete any .dvi, .ps and .pdf files that might have been produced from your .tex (this is just so you can see cleanly whether this is working the way it should).  Now in emacs hit CTRL-c CTRL-c and then ENTER.  If you look in the directory again you should see a newly built .pdf, but no .dvi.  Also there should be a new file with extension .synctex.gs.  If this second file isn't there then synctex isn't doing what it should and you won't have the inverse search working.  Check your .emacs file and make sure the line we inserted above isn't mistyped.  Back in emacs hit CTRL-c CTRL-c again and then ENTER.  Your new .pdf *should* open up in okular.  Arrange the windows so you can see the .tex file in emacs and the .pdf in okular simultaneously.  If you SHIFT-left click on any word in the .pdf then your cursor in emacs should move to the beginning of the paragraph containing the word you clicked.

Voila!

I couldn't get this same functionality to work in texwriter despite following a couple of posts about it.  emacs is really powerful.  It's too bad its customization dialogues are so cryptic!

---

