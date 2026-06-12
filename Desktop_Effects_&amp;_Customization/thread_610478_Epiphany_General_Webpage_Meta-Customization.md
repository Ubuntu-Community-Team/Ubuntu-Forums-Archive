---
title: "Epiphany General Webpage Meta-Customization"
date: 2007-11-12
forum: Desktop Effects &amp; Customization
---

### Post by c0mp13371331337 on 2007-11-12
Hello All!

I have a pretty non-standard theme set up.  I like my blacks and greens and monospace fonts.  No, not because of the Matrix.  In fact I try to shy away from matrix backgrounds/screensavers because people comment too much as it is that using my computer is like entering the matrix.

At any rate.... I digress.  Because of my non-standard themes, CERTAIN PARTS of SOME of the webpages I visit just don't display correctly.  ie, green text on a background that makes it very difficult to see green text; web widgets (inputs, buttons, etc) that are unreadable unless highlighted, general annoyances that are, for the most part, easily cleared with the good ol' Ctrl-A.  But still, annoying nonetheless.

I'd like to keep my display settings for the chrome around the actual webpage, where epiphany's menus, buttons, tabs, statusbar, titlebar and the like reside, but I'd like to know if it's possible to keep my personal theme from being transposed onto webpages I visit.  I'd like to just see pages displayed the way the webmaster wanted me to see them, rather than the way my desktop theme thinks parts of them should look.  Is it possible to keep epiphany from using my personal settings as it renders pages?  I don't have any custom CSS or anything being used, it's just pulling these settings right from my desktop theme.

Here's the pertinant info:

epiphany 2.20
Ubuntu 7.10
Heh, and I just noticed my Controls are named BlackmarbleMatrix, so much for my first paragraph! :---)
Window Boarder is 'Bright'

Let me know if any other information would be necessary.  I can post screenshots of how various pages and web widgets look as well, let me know.

Thanks!

---

### Post by bapoumba on 2007-11-12
Have you looked in the preference panel ?

---

### Post by c0mp13371331337 on 2007-11-12
Hey bapoumba, and thanks for the reply.  Yes, I did check all preferences.  Both the boxes that you have checked, to allow pages to use their own fonts and colors, are checked.  No custom stylesheet either.

Could it be that, where the issue happens only in certain places and I already have those two boxes checked, it's letting my theme take over when the web pages and widgets DO NOT specify their own colors?

---

### Post by bapoumba on 2007-11-12
Hmm, I do not know. I'll try with a dark theme.
Would you please give a link where this behavior happens?

---

### Post by c0mp13371331337 on 2007-11-12
As I mentioned before, the Controls theme is BlackmarbleMatrix, which I found on the Gnome Art webpage, actually installed it via the package gnome-art.

As I browsed the web today, I took note of some of the oddities I've come across with the coloring of webpages.  The first one is an example of the white background with neon-green text:

[http://earth.google.com/intl/en/userguide/v4/flightsim/index.html](http://earth.google.com/intl/en/userguide/v4/flightsim/index.html)

Here's one that seems to have been COMPLETELY taken over by my theme, it has a completely flat black background and green text, but the links are still the default blue, making them difficult to read on the black:

[http://mike.depalatis.net/epiphany/extensions.html#sessions](http://mike.depalatis.net/epiphany/extensions.html#sessions)

And this page has the widget color issue.  The widget background is black, and the text inside the widgets is black, making it impossible to read without highlighting.  The attached screenshot actually has information typed into the inputs, an option on the dropdown, and text in the button:

[http://kolmafia.us/index.php](http://kolmafia.us/index.php)

Let me know if for whatever reason you're not able to get ahold of the controls theme I'm using.  I can attach screenshots of each link so you can see what I'm seeing.

Thanks again for your assistance with this.  It really is great to see how people are so willing to lend a helping hand.

---

### Post by bapoumba on 2007-11-13
Argggh, what a theme :D
Okay, here is a screenshot of the web page. As you can see, the web page used its own setting. Hmm, we'll have to look for some other reason.

---

### Post by c0mp13371331337 on 2007-11-13
Heh, yeah, I know it's quite the theme.  Most people hate it, but I find it to be pretty easy on the eyes.  Easier than a mostly white/light screen at least.

I just can't imagine what else would affect the web page colors like they are.  I've been through all gconf-editor options for epiphany, all GUI options within the program itself.  I just do not know.  And I'm fairly certain it did have to do with the theme, as everything was normal in web pages before changing to that theme.  Then everything immediately changed in epiphany.

Thanks for taking the time to look into it from your end.  Unless anyone else has any ideas, I suppose I'll just live with it, and I'm sure I'll survive!

---

