---
title: "Openoffice landscape page"
date: 2009-01-22
forum: General Help
---

### Post by cguy on 2009-01-22
I'll start the same way I am going to finish: OpenOffice is one of the worst, lowest quality software available for Linux.

To the point: how do I change a single existing page to landscape?! Using page styles only affect the first page.

OpenOffice is one of the worst, lowest quality software available for Linux.

---

### Post by Zill on 2009-01-22
cguy:  Welcome to the forums. You are, of course, entitled to your views on the free software you are using.  However, your negative comments do not *really* help to improve the quality of the software!

On your specific point, OpenOffice allows you to easily change page format between portrait and landscape.

I suggest you follow the detailed instructions in the application help section entitled "To Use Landscape and Portrait Page Orientation in the Same Document".  This section can be found by typing "landscape and portrait" into the help index search box.

---

### Post by cguy on 2009-01-23
I surely did those things said in the help file (and on the Internet as well). The custom style always changed the first page and only the first page.
Then I went through the steps again, maybe I forgot or didn't see something. To no effect.
I may be blind, so I retried over and over again, about 7 times. Nothing!!

I tried to apply a style to the table of contents page and that didn't work either.

Before this I have had problems with:
- the all to complicated menus. One will find his way around by searching on google rather than searching through the menus.
- paragraph styles - Customizing just one paragraph screws up the whole deal. The AutoUpdate function has some misterious ways of working. The lists' paragraph style must be modified by hand, each list at a time.
- lists - lost numbering after reopening the document, bad list items levels, uncustomizable bullets, hidden numbering of paragraphs, applying paragraph styles to the lists
- page numbering - you really must search on google on how to print the numbers on both the odd and even pages ("Same content left/right" is totally unintuitive) and how to hide the page number on the first page. Since hiding the p. no. works through page styles, it can only be done on the first page.
- no rotation of most of the objects; bad rotation for the OO Draw shapes with text

There may be more, but right now I am just too tired after spending 10 hours on formatting a 30 page document.


These negative comments won't help improve the quality of the software, but they help me vent. Maybe you can resonate with me and understand my frustration.



As an exclusively OSS user for about an year, I am really dissapointed to find out there's really no alternative to MS Office, which I may be installing now that the ordeal is over.

---

### Post by mssever on 2009-01-23
It took me a while to get used to OOo, since some things work quite a bit differently than MS Office. While I still think that MS Office is superior, OOo has made an awful lot of progress over the years and I no longer feel limited by it.

Format > Page > Page tab > Orientation applies to the entire document. If that doesn't work for you, then maybe there's something screwy with your styles. As a usage note, I should point out that I always use styles to format documents (both in OOo Writer and MS Word) which might affect my experience with OOo.

As far as your other complaints go:
> **cguy said:**
> - the all to complicated menus. One will find his way around by searching on google rather than searching through the menus.People have said the same thing about MS Word < 2007. OOo's menus aren't any more complicated, but they *are* a bit different.

> - paragraph styles - Customizing just one paragraph screws up the whole deal. The AutoUpdate function has some misterious ways of working. The lists' paragraph style must be modified by hand, each list at a time.I don't know how you're using the paragraph styles, because they work just fine for me, and they're quite similar in use to Word. I don't use the AutoUpdate function (in either Writer or Word), so I can't comment on that. Perhaps that's your problem and disabling it will fix it. Besides, having an auto updater just seems to me to be a bad idea. After all, the whole point of using styles is so you *don't* do direct formatting of the documentation other than assigning styles.

> - lists - lost numbering after reopening the document, bad list items levels, uncustomizable bullets, hidden numbering of paragraphs, applying paragraph styles to the listsLists work fine for me
> - page numbering - you really must search on google on how to print the numbers on both the odd and even pages ("Same content left/right" is totally unintuitive) and how to hide the page number on the first page. Since hiding the p. no. works through page styles, it can only be done on the first page.I don't think I've ever tried anything like you mentioned in OOo, so I can't comment on it.
> - no rotation of most of the objects; bad rotation for the OO Draw shapes with textYes, graphics is where Word totally obliterates Writer. I used to use Word for many graphical purposes. Now that I'm using OOo, I do my graphics in GIMP or Inkscape. This is, I think, one of OOo's major weaknesses.

---

### Post by Zill on 2009-01-23
cguy:  As mssever has advised, OOo works best with styles - "direct" formatting rarely gives good results and is likely to create problems.

Regarding the portrait/landscape problem, you simply need to create a "landscape" page style, and possibly a new "portrait" page style if this is not your current default.  Then just follow the instructions as per the OOo Help:

> 1.Click in front of the first character of the paragraph where you want to change the page orientation.
2.Choose Insert - Manual Break.
3.Select Page break.
4.In the Style box, select a page style that uses the landscape or portrait page orientation.
To change the orientation of the current page only, select a page style where the Next Style option is set to "Default".
**To change the orientation of the current and subsequent pages, select a page style where the Next Style option is set to the name of the page style.**
If you want to change the page orientation later on in the document, repeat steps 1 to 3.
5.Click OK.

If this does not work for you then please advise exactly which step is failing.  I attach a screenshot showing my test file of Portrait-Landscape-Portrait.

---

### Post by scouser73 on 2009-01-23
OpenOffice isn't Microsoft Office, things aren't where you'd expect them to be with OpenOffice. In my opinion it's possibly the best office suite.

You should take a look at the tutorials on this site; [http://www.tutorialsforopenoffice.org/]("http://www.tutorialsforopenoffice.org/") and then make a judgement as to how you find OpenOffice.

As I've said, OpenOffice isn't Microsoft Office.

---

### Post by cguy on 2009-01-23
Actually, that was my first document ever to be created entirely with styles.
While the rest of my bitching stands (right now I am looking at bad numbered lists and broken OODraw organigram), I admit I have been blind about the page style.
I never noticed the "page style" **combo box** on the "insert page break" dialog. Instead, I inserted a page break and then I double clicked on the desired style in the "Styles box" which always affected the first page of the document (weird, undesired behaviour)

scouser73: I'm not trying to make a comparison with MSOffice; it's just that after spending numerous hours trying to accomplish basic tasks and not having another Linux alternative, I remembered that I never wanted to pull my hair out when I had MSOffice on my hard drive. A comparison is not what I want from this thread :)

---

### Post by Zill on 2009-01-23
> **cguy said:**
> ...While the rest of my bitching stands (right now I am looking at bad numbered lists...

I am pleased that you have now resolved the orientation problem. :-)

Regarding list numbering, this is likely to be due to the use of "direct" numbering, rather than numbering styles, or a mixture of the two.  If you *only* use styles for numbering, and then modify the style to meet your requirements, it should work OK.

If you have any problems with this, or anything else, then I suggest you break the problem down into discreet steps, posting exactly what you have done, what you expected and what actually happens.

This forum will help with general Ubuntu questions, but you will also find more specific help at the [OpenOffice forums]("http://user.services.openoffice.org/en/forum/").

---

