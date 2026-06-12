---
title: "Video fonts, subtitles etc."
date: 2006-09-14
forum: Desktop Environments
---

### Post by Anonii on 2006-09-14
Greetings,

I'm trying to apply the freaking Greek subtitles to a movie, for my sister to watch it. I found the subtitles, (which I will attach, for no reason) and tried to make them work.(Note , that I can see English subtitles) In mplayer (my main video player) (I had the same results with other players too) the subtitles were a weird font that appears when you are trying to view a Greek or a foreign site with firefox. I understood nothing, obviously. (Note, that when I opened that text file with an editor I could see the Greek letters etc.) I asked in some channels in IRC, and I was mainly advanced to convert that text to UTF-8 (I dont really know what this means ^_^) so I used this command
_iconv -f iso8859-1 -t utf-8 clockwork_orange_grk.sub > clockwork_orange_grk.sub2_
(The filenames may not be right, but it doesnt matter)
I got another text file. which I couldnt understand if I opened it in a text editor (I could before the convert)and I'd get the same font that I was getting in mplayer before the convert. If I tried to apply the subtitles to mplayer I would get a "?????????????????" line instead of the subtitles. Just question marks, nothing else.

I'm not really that hopeless, and I dont really care if my sister will see the movie. But I'd like to know that I can fix this problem, and also understand what UTF is, and what format my text is right now, and also why I should convert it :/ (A solution would be great too :P)


Thank you!

---

### Post by Anonii on 2006-09-15
[COLOR="DarkOrange"]Hump De Bump[/COLOR]

---

### Post by Ziggurat on 2006-10-27
Hi. Maybe too late but here i go. To convert your subs to utf just open it with the text editor (gedit) and select save as... then look it gives you a couple options at the botton there you can select utf-8.

And with mplayer you need to add this to your config file (located in .mplayer):

subcp=utf8

Hope this helps.

---

### Post by Anonii on 2006-10-28
> **Ziggurat said:**
> Hi. Maybe too late but here i go. To convert your subs to utf just open it with the text editor (gedit) and select save as... then look it gives you a couple options at the botton there you can select utf-8.

And with mplayer you need to add this to your config file (located in .mplayer):

subcp=utf8

Hope this helps.
Thank you! I dont have any movies to try it out, right now.
But I will check it, the sooner possible.
Thanks again!

---

### Post by Anonii on 2006-10-28
Tried it out. I got messed up characters :/

Check the screenshot attached. The characters appearing on gedit, are the same that appear as the mplayer's subtitles :[

---

### Post by aNTwNHs on 2006-10-29
I have exactly the same problem with my sister,...sorry displaying greek subtitles! Any suggestions?

---

### Post by aNTwNHs on 2006-10-29
VLC media player can display greek subtitles quite well:P

---

### Post by Anonii on 2006-10-29
> **aNTwNHs said:**
> VLC media player can display greek subtitles quite well:P
It didnt work for me :(
Pity... Seems like my sister wont see her movies subed, this time :]

Thanks antoni!

---

### Post by aNTwNHs on 2006-10-30
Just in cased u missed it(since I did the first time I tried VLC).
File>Open File>Check:Use Subtitles File>Advanced Settings>Encoding>8859-7.

(I use the ubuntu 6.10)

---

### Post by Anonii on 2006-10-30
Wii! Thats great! The Greek subtitles now work for VLC. But I get a stupid error when I try to watch them in mplayer.

**"Cannot load subtitles <path_to_subtitles>.srt"**

Anyway, I guess that VLC will do it.

Euxaristo antoni!

---

### Post by bggr on 2008-03-25
> **Anonii said:**
> Wii! Thats great! The Greek subtitles now work for VLC. But I get a stupid error when I try to watch them in mplayer.

**"Cannot load subtitles <path_to_subtitles>.srt"**

Anyway, I guess that VLC will do it.

Euxaristo antoni!


you can try and this solution.... as well.... 

[http://www.sapioi.gr/blog/?p=1005](http://www.sapioi.gr/blog/?p=1005)

it works with me for Caffeine and Xine

bggr

---

