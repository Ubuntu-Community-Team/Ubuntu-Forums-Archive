---
title: "Oh noes! The internets is broken! Javascript, Firefox, Ibex."
date: 2009-03-02
forum: General Help
---

### Post by frith on 2009-03-02
I'm not sure what has happened or how, but for some reason wikipedia no longer works for me using Firefox on intrepid ibex.

Some info:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.10 (intrepid) Firefox/3.0.6

Whenever I go to wikipedia, the pages don't load - all that appears is the background. Then if I refresh the page, the full page briefly appears, before it goes back to just displaying the background. This behaviour disappears if I disable JavaScript in Firefox, but I need JavaScript for the Internet (gmail, slashdot, ubuntu forums, everything else) to work!

I opened the 'error console' in FF, and the following errors occur when I try to open a page in wikipedia:

Page: [http://en.wikipedia.org/wiki/Main_Page](http://en.wikipedia.org/wiki/Main_Page)

Errors:

Warning: Unknown property 'column-count'.  Declaration dropped.
Source File: [http://en.wikipedia.org/w/index.php?title=MediaWiki:Common.css&usemsgcache=yes&ctype=text%2Fcss&smaxage=2678400&action=raw&maxage=2678400](http://en.wikipedia.org/w/index.php?title=MediaWiki:Common.css&usemsgcache=yes&ctype=text%2Fcss&smaxage=2678400&action=raw&maxage=2678400)
Line: 37

Warning: Unknown property 'word-wrap'.  Declaration dropped.
Source File: [http://en.wikipedia.org/w/index.php?title=MediaWiki:Common.css&usemsgcache=yes&ctype=text%2Fcss&smaxage=2678400&action=raw&maxage=2678400](http://en.wikipedia.org/w/index.php?title=MediaWiki:Common.css&usemsgcache=yes&ctype=text%2Fcss&smaxage=2678400&action=raw&maxage=2678400)
Line: 52

These are listed as 'warnings' in the error console.

The status bar on the bottom is just stuck on 'transferring data from upload.wikimedia.org'. If I am really quick on the 'Esc' key (shortcut for 'stop' in FF), then I can get the page to display, but this hardly qualifies as a workaround, since half the time the whole page has not yet loaded.

Any help appreciated!

Frith.

---

