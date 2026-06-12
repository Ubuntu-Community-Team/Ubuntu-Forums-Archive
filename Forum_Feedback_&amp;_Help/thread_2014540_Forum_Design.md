---
title: "Forum Design"
date: 2012-07-02
forum: Forum Feedback &amp; Help
---

### Post by lewisgoddard on 2012-07-02
While i love that this forum (in which i don't post as much as i should) finally got a redesign, i do have a few little niggles about it:

*Why does the bar with "User CP", etc, in it have no space between it and the one above?*
Either get rid of the curved corners that join together, or give it "margin-top: 10px;".

*Why does the page always extend to nearly the full width of the screen?*
It is difficult to read posts that go all the way across my screen before going onto a new line, and i frequently find myself skipping or re-reading lines. For the first Div inside Body, i would add "margin: 0px auto; max-width: 1000px;".

*Why is the search form outside the rest of the page?*
[HTML]<td align="right">
<div id="searchbox">
<form action="search.php?do=process" method="post" style="margin-top: -30px;">
<label for="q" accesskey="s">
<span class="mnemonic">S</span>earch
</label>
<input type="text" value="" name="query" id="q">
/* Hidden Search Values */</form></div></td>[/HTML]

*Why is there an empty a?*
I will presume the <a name="top"></a> is so that the button at the bottom of the page will jump to the top. This would still work if you added id="top" to the first table element.

*Why did i just spend more time finding twenty tiny images than downloading them?*
Sprites, anyone?

**TL;DR**
Install [this]("https://chrome.google.com/webstore/detail/keimphpnhnicpenfffoopahkgpkehfok"). :popcorn:
Look better?

All just Constructive Criticism! ):P

---

### Post by kansasnoob on 2012-07-02
I see there have been no new posts there in a week but Technoviking was tracking feedback here:

[http://ubuntuforums.org/showthread.php?t=1977943](http://ubuntuforums.org/showthread.php?t=1977943)

I'm not really a gambling man but if I were I'd bet he's still tracking that thread ;)

---

### Post by Paddy Landau on 2012-07-02
> **lewisgoddard said:**
> *Why does the bar with "User CP", etc, in it have no space between it and the one above?*
Either get rid of the curved corners that join together, or give it "margin-top: 10px;".
Actually, I disagree with that point. I like that part the way it is. :)

---

