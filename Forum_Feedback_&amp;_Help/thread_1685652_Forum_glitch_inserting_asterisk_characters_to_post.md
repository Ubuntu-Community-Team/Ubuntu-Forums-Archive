---
title: "Forum glitch inserting asterisk characters to posts?"
date: 2011-02-11
forum: Forum Feedback &amp; Help
---

### Post by *uu on 2011-02-11
Hi,

in all my recent posts, maybe during the last three or four hours, whenever I pressed the button [Preview Post], multiple asterisk characters ( * )*got inserted throughout the post, both in the preview and in the edit box. Mostly, I saw them after or even around the one-letter-word "I", but also between punctuation and the first letter of the next word or sentence. In all cases, they replaced a space that I had typed in their place.

Did I*find some forum bug?*Or is my firefox doing some strange things when submitting my text to the forum?*:D

*uu

P.S.:*In this post, I didn't remove the automagical asterisks, so you could see what I'm talking about. I actually only typed two asterisk characters myself in this post, the middle one in parenthesis, and the one in front of my nickname. Interesting enough, when I write the post in an editor and merely paste it into this edit box, or when editing after the first preview, no asterisks seem to get inserted.

---

### Post by CharlesA on 2011-02-11
Does it happen with a different browser? Sounds like firefox is messing with yer posts.

---

### Post by *uu on 2011-02-11
Also I*don't know this is some random text. I write random text when I'm nervous about something. So I type and type and I*type some more. Blahing right away.

*uu


Edit: Well, the above was written in Chromium. So it's definitely nothing Firefox specific.

---

### Post by CharlesA on 2011-02-11
Are you using the quick reply or clicking on the 'new reply' button?

---

### Post by *uu on 2011-02-11
What I*noticed:*According to [FONT="Courier New"]top[/FONT], my physical memory seems to be quite stuffed:

```
Mem:   4058316k total,  3905336k used,   152980k free,   171716k buffers
Swap:  3033172k total,    27968k used,  3005204k free,  1167088k cached
```

Could that have something to do with it? (I'd*really like to avoid restarting just to find out... ;)) This was already the case in the morning when I*opened this thread. Though, system monitor only shows a memory consumption of about 2.45 GB*out of 4 GB.

But as far as I read, [FONT="Courier New"]top[/FONT]'s memory count doesn't mean that the memory is indeed fully used, but only that there is data in the RAM which was left back by applications, but the space could be freed and used by other applications if necessary. Did I*get that right?

*uu

P.S.:*This post is still being typed in Chromium. And just now it put the asterisk into this line, even though I*had previewed the post once before.

EDIT:*Normally, I used the 'new reply' function.

---

### Post by CharlesA on 2011-02-11
A better way to check how much memory you have free is to run this:
```
free -m
```

In any case try a reboot and see if that fixes the problem. It's not a browser issue as it is happening with two different browsers.

---

### Post by *uu on 2011-02-12
Dammit! I just found out what the problem was: A combination of keyboard layout, lazy typing fingers and a forum function. :D

A couple of days ago, I had set up my keyboard layout to type a non-breaking space whenever I press SHIFT+SPACE, which I found useful for something I'm currently working on. Now, when typing rapidly, when typing capitals, I sometimes accidentally typed some non-breaking spaces as well. Usually, they are not distinguishable from normal spaces, but this forum substitutes them by the asterisks when submitting the posts.

In LibreOffice, these non-breaking spaces are displayed with a light gray background, that's how I noticed it in the first place when writing a letter today. Sorry for the fuzz, and thank you, CharlesA, for your help. :)

*uu

---

