---
title: "Code Tags"
date: 2007-01-21
forum: Forum Feedback &amp; Help
---

### Post by gummibaerchen on 2007-01-21
Hi,

are there any chances for better "Code Tags"?

I mean the font in the real ```
-Tags sucks.

HTML-Code-Tags oder the PHP-Code-Tags have a much better Font.

[code]-Tags are no use for example when publishing Shell output.

And on the other hand it's stupid when I wrap my Pyhton-Program in PHP-Code-Tags.

Here a quick comparisation:

[CODE]The original CODE-Tags, which suck
```

[HTML]The HTML-Code-Tags which are all right.[/HTML]

[PHP]The PHP-Code-Tags which are superfluous[/PHP]

Regards

---

### Post by po0f on 2007-01-21
gummibaerchen,

I've raised this issue before, as well as another member, but the problem still hasn't been fixed.  I have been using a combination of [code] and [font="Courier New"] tags, but it is kind of annoying to have to resort to this combination, considering I use this/these tags a lot.

---

### Post by jpeddicord on 2007-01-21
Add my vote for better stylizing of CODE tags. The variable fonts in the tags tend to get annoying with code.

---

### Post by matthew on 2007-01-22
Doing this would involve more than just changing an admin setting. As far as I can tell it would require a bit of hacking at a deeper level. At best it could make it on to an already long list of "if I ever have some free time" projects ubuntu-geek would like to do. More likely I should just say, "We hear what you're saying. Sorry, it's not something we can change at the moment."

---

### Post by jpeddicord on 2007-01-22
I'm bored :mrgreen:, so I managed to find the right style to change in case there ever is time to do it. I found this about halfway down vB's generated CSS file, however it is probably in a different file than that knowing the way it handles CSS.

Quick font patch:```
.ubuntu_codebackground
{
	font-weight: normal;
	font: monospace, Verdana, Sans-Serif;
	background: #F8F8F3;
	border-right: 1px solid #ddddc5;
	border-top: 1px solid #ddddc5;
	border-left: 6px solid #ddddc5;
	border-bottom: 1px solid #ddddc5;
}
```

(I love the web developer Firefox extension)

Jacob

---

### Post by ubuntu-geek on 2007-01-22
It'll be fixed in the next update which will happen sometime in the next month. :)

---

### Post by Ben Sprinkle on 2007-01-22
No, the code tags actually look better. :D

---

### Post by dorcssa on 2007-01-22
Actually I don't even understand the problem... You have problem with the fontstyle? If that's the issue, I do't see much difference, so why bother?

---

### Post by po0f on 2007-01-22
matthew/ubuntu-geek,

I hope my tone didn't come off as being accusative ("They know, they just don't fix it."), I was just pointing out that they *do* know, but here's a work-around.  Entering the [code][font="blar"] tags is pretty much automatic on my part now when posting code.  When it is indeed fixed, I'm sure I'll redundantly add the [font] tags just out of habit for a while.  ;)


dorcssa,

If you notice from the first post, the text between [code] tags are rendered in a sans-serif font, not really optimal when viewing "code" (can mean a few things, namely code and terminal output).  A mono-spaced font would be much better.  The [html] and [php] tags render their text as mono-spaced, which is expected behavior, and wanted for the vanilla [code] tags as well.

---

### Post by gummibaerchen on 2007-01-22
But why is there a special "PHP"-Tag anyway? I noticed that in many BB-softwares.

I mean syntaxhighlighting would be the the greatest, but why only PHP?

At least I would expect C, C++ and Python highlightings in an Ubuntuforum.

---

### Post by Ben Sprinkle on 2007-01-22
Because php can be done with 1 line of code. I think it's *something*_highlight("yourtext");
Mabey syntax_highlight?

---

### Post by gummibaerchen on 2007-01-22
> **Ben Sprinkle said:**
> Because php can be done with 1 line of code. I think it's *something*_highlight("yourtext");
Mabey syntax_highlight?

Yeah, ok, if you look from that point of view.

But only because it is easy to write that in PHP (as this board is written in PHP), it does not mean, that it is a necessary feature.

I mean you can easily write a calculator, dictionary or even a search-engine in PHP, but all that is not included in this board either :biggrin:

---

