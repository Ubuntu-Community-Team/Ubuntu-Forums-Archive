---
title: "Full Circle In HTML Form"
date: 2008-02-11
forum: Full Circle Magazine
---

### Post by usmanzia on 2008-02-11
Hello I am a new reader of this great magzine but i want the .html version of it. I tried many pdf to html convertor but the text obtained in html form readable ,as there are many spaces etc in letters.so please any help me .

---

### Post by onlineapps on 2008-02-11
I agree. Maybe it can be built into the fcmcollab app that's being built.

---

### Post by ronniet on 2008-02-12
Our (super-secret ;) ) proofing wiki effectively has (most) articles in HTML format, but the problem is man-power. It would need someone who can do wiki stuff really well who would pretty up the wiki pages as each issue is launched.

Not a very nice job...  :(

---

### Post by onlineapps on 2008-02-12
Well, can't you make the fcmcollab output to HTML? Then we could just bypass the wiki altogether... (wasn't that the original idea?)

---

### Post by mrmonday on 2008-02-13
> **onlineapps said:**
> Well, can't you make the fcmcollab output to HTML? Then we could just bypass the wiki altogether... (wasn't that the original idea?)

That is the plan, but the collab project isn't far enough to do that currently. There's a lot of work that needs doing for the collab project (see [http://fullcirclemagazine.org/fcmapp/](http://fullcirclemagazine.org/fcmapp/) for the full list of things). As it could be a while, ronnie's idea would be needed in the mean time.

---

### Post by ncappel1 on 2008-03-02
Hi Everyone! I am here in Rio de Janeiro, Brazil having a difficult, but great time. It's too bad I can't be part of the project for a while, but an html version would also be great for someone like me, who no longer has a computer and has to surf at cyber cafes ("time is money" is very clear in this context, and often times the computers only have "high speed" internet, with no download policies, how frustrating)

I like keeping up with the ubuntu world, even though I haven't used it since December. I did go through withdrawl, by the way. :) my temporary fix has been the the computers in the labs at my langugage school used ubuntu.

---

### Post by RobinC@Amethyst on 2008-04-11
Aha! First post on this forum. This must be web-two-point-doh!

HTML version of mag - may be possible through  the Pmwiki site if we have control of stylesheets and extensions. 

I've just installed a copy to test and proved AutoImageResize works in somebody else's sandbox. 

Just how much 'fancy/really clever wiki-stuff' do we need for this?

RC

---

### Post by RobinC@Amethyst on 2008-06-05
In case you haven't seen the Full Circle main site yet, the HTML Preview edition is at:

_[COLOR="Navy"][http://fullcirclemagazine.org/2008/06/03/preview-full-circle-magazine-html-edition/](http://fullcirclemagazine.org/2008/06/03/preview-full-circle-magazine-html-edition/)[/COLOR]_

It's a first attempt to create a standards-compliant, cross-browser, fast, portable and light-weight online edition of the magazine - using only standard HTML, CSS and all Open-Source tools.

RC

---

### Post by onlineapps on 2008-06-05
That's so cool! Is it automated?

---

### Post by RobinC@Amethyst on 2008-06-06
Automated? Oh yeah, I've heard of that...

Right now I'm piggy-backed off the wiki text and Ronnie's PDF. The rpl tool is handy for updating the template set.

The pdftohtml tool extracts the graphics set (except those that get 'hidden' in Scribus layers in the pdf!) to default size but named with my edition prefix, the page number and position number. 1 command.

I put those thru imagemagick to produce a consistent set of compressed jpegs for full size and an inline thumbnail size. 2 commands

The wiki text is in basic html format so I drop that in the template as-is. 1 operation per section.

I then have to replace the original image reference with my standard code which places floated thumbnails, opening the enlargements into a new window. 2 operations per image.
Picking up the filename is easy enough, but we've got no title, alt or captions text on the wiki worth having, so I have to add those. That's a pain. 3 operations per image

Next, check page layout in different browsers. For layout and a bit of visual interest, I'll amend the classes for left/right float and maybe adjust the vertical text spacing (it's called cheating, I think).

Most of the sections run in pretty standard. It's mostly mine and Ronnie's how-to's that need intervention to layout. Sometimes the 'faux-columns' styles work well and look ok, that's all done with one CSS declaration.

Recreating Ronnie's covers it a bit of a kludge. Trying to keep things fast, light and accessible, otherwise I'd cheat and use an image map.

If I didn't write such lousy code, I'd have a go at scripting more of this conversion process. Trouble with that is we need very strict rules for entry and formatting the original content for the scripts to run properly each time, not to mention a strict standard page layout to load into and a rigid set of CSS styles. That gets a bit dull. Fine for an e-commerce site, not so good for a magazine. And we're still finding our way.  

Having managed a process to pull content from 42 brochures x3 editions a year into an online edition via 2 content management systems, I know some of the pitfalls.

RC

---

