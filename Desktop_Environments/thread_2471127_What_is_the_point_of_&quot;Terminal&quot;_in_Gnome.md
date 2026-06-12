---
title: "What is the point of &quot;Terminal&quot; in Gnome Settings &gt; Search?"
date: 2022-01-21
forum: Desktop Environments
---

### Post by Paddy Landau on 2022-01-21
In Gnome Settings > Search, one of the options is Terminal (see screenshot below).

I can't figure out what it means. Searching for an answer gets me a ton of unrelated answers.

What does this setting mean?

---

### Post by watchpocket on 2022-01-21
My guess is that it would enable you to search through your command-line command-history.  

I don't know what else searching in the terminal could mean.

What happens when you go there? (I don't use Gnome, so I can't.)

---

### Post by schragge on 2022-01-21
My understanding of this. There's a list of GNOME apps that provide search functionality. Results of their respective search functions can be included into the GNOME search output. GNOME Terminal provides [Search for text](https://help.gnome.org/users/gnome-terminal/stable/txt-search.html.en), so it's in the list, too.

---

### Post by Paddy Landau on 2022-01-22
> **schragge said:**
> GNOME Terminal provides [Search for text]("https://help.gnome.org/users/gnome-terminal/stable/txt-search.html.en"), so it's in the list, too.
Thanks. This is the intuitive answer, but unfortunately it doesn't work. It works from within gnome-terminal itself, but not from the Gnome search bar.

I put some nonsense in the gnome-terminal ([FONT=courier new]echo[/FONT] [FONT=courier new]yh7uj[/FONT]). When I search for [FONT=courier new]yh7uj[/FONT] within gnome-terminal, I get the correct results. But when I search for [FONT=courier new]yh7uj[/FONT] from the Gnome search bar, I get nothing.

I also thought that it might mean to search for a terminal command, but that also doesn't work, e.g. when I search for [FONT=courier new]echo[/FONT] or [FONT=courier new]/usr/bin/echo[/FONT].

---

### Post by KBar on 2022-01-22
It looks like a bug worth reporting upstream. Or maybe GNOME Project just scrapped this feature?

Do the results come up if you disable everything else and leave only Terminal?

---

### Post by Paddy Landau on 2022-01-22
> **KBar said:**
> Do the results come up if you disable everything else and leave only Terminal?
Good question. I've just tested this, and no, they don't.
> **KBar said:**
> It looks like a bug worth reporting upstream. Or maybe GNOME Project just scrapped this feature?
Well, I've gone through [gnome.org]("https://www.gnome.org/") to find an explanation for what it's supposed to do, but I can't find something relevant.

I also tried searching [superuser]("https://superuser.com/"), but again I had many unrelated answers.

So, I don't want to report this as a bug, because I don't know if it's a bug — at this stage, for all I know, it's doing what it's supposed to do!

I'll turn off the feature and leave it be, because I don't know how to proceed from here, and it's probably unimportant. I was more curious than anything else.

---

### Post by vanadium on 2022-01-22
What it does is allowing you to search an open terminal window in the Activities overview. Say you have some terminal open in ~/Documents/Projects/MyEditor, then searching either "Documents"  or "Projects"  or "MyEditor"  will reveal a category of "Terminal" search results. Selecting the search result brings that terminal window in focus.

No more than that. No-one uses that ever, I guess, but there it is.

---

### Post by Paddy Landau on 2022-01-22
> **vanadium said:**
> … allowing you to search an open terminal window in the Activities overview. … Selecting the search result brings that terminal window in focus.
Thanks for the explanation. I've just tried it, and it still doesn't work!

I can see why no one would want to use it; it doesn't seem useful, unless you use many terminal windows over several desktops.

---

### Post by Frogs Hair on 2022-01-22
The terminal is another directory search option on your system and it maybe as simple as that.

---

### Post by Paddy Landau on 2022-01-22
> **Frogs Hair said:**
> The terminal is another directory search option on your system and it maybe as simple as that.
No, this doesn't work as a directory search.

If I turn off all options including Files, and turn on only Terminal, the only results that I'm shown are apps and settings. No directories.

I get directories only if I turn on Files.

---

### Post by KBar on 2022-01-22
> **Paddy Landau said:**
> I also thought that it might mean to search for a terminal command, but that also doesn't work, e.g. when I search for [FONT=courier new]echo[/FONT] or [FONT=courier new]/usr/bin/echo[/FONT].

Maybe you're supposed to invoke commands? Try something like [FONT=courier new]echo test > /tmp/test.txt[/FONT] and see if it succeeds. 

Also, does it provide any hints when you open its kebab menu (the three vertical dots)? 

I'm not a GNOME Shell user, so I wouldn't know.

---

### Post by Paddy Landau on 2022-01-22
> **KBar said:**
> Maybe you're supposed to invoke commands? Try something like [FONT=courier new]echo test > /tmp/test.txt[/FONT] and see if it succeeds.
I've already tried that. It just says, "No results".
> **KBar said:**
> Also, does it provide any hints when you open its kebab menu (the three vertical dots)?
There's no menu on the Gnome search bar.

---

### Post by KBar on 2022-01-22
> **Paddy Landau said:**
> I've already tried that. It just says, "No results".

Hmm, I see. I've just posted this thread on GNOME's IRC channel. No answers so far.

> There's no menu on the Gnome search bar.

Sorry, I meant the one that appears to the right in GNOME Settings > Search dialog. The three dots can be seen in your original screenshot.

---

### Post by Paddy Landau on 2022-01-22
> **KBar said:**
> Hmm, I see. I've just posted this thread on GNOME's IRC channel. No answers so far.
Thanks for posting! I hope that you get an answer :)
> **KBar said:**
> Sorry, I meant the one that appears to the right in GNOME Settings > Search dialog. The three dots can be seen in your original screenshot.
Ah, right. I have looked there, and the Help doesn't mention it at all.

---

### Post by Dennis N on 2022-01-22
I suspect searching "Terminal" output via the Activities search box is broken or not yet implemented, along with searching your bookmarked places shown in **Settings > Search > Search Locations > bookmarks. **

Also, if you try to add a location (besides 'Desktop') with **Settings > Search > Search Locations > Other Locations > <click + and browse to selection>**, it failed to add the location. 

I tried adding search locations in the past, shrugged, and gave up. It still seems the same today.

---

### Post by KBar on 2022-01-22
Coming to the same conclusion as well.

Looks like GNOME already abandoned this feature before it even got introduced.

---

### Post by Paddy Landau on 2022-01-23
> **Dennis N said:**
> … searching your bookmarked places shown in **Settings > Search > Search Locations > bookmarks.**
… add a location (besides 'Desktop') with **Settings > Search > Search Locations > Other Locations > <click + and browse to selection>**
I've just tried, and you're right. It doesn't work!
> **KBar said:**
> Looks like GNOME already abandoned this feature before it even got introduced.
Hmm. When I get a little time, I'll report both of these. I'll post back here once done.

---

### Post by vanadium on 2022-01-23
Wat version is this? For me Ubuntu 21.10. It actually does not only search across windows, but also across tabs. I currently have a single Gnome Terminal window open. Just typing ~ in the activities overview shows two entries, corresponding with the two open tabs. Typing "Downloads"  only shows the tab open in Downloads and clicking the entry brings me there. This actually could be quite handy for terminal users, but then usability would be improved if one could selectively search for these entries (i.e. not be confronted all the time with other not relevant results from other sources). There, the Unity Lenses got it more right.

---

### Post by KBar on 2022-01-23
> **vanadium said:**
> There, the Unity Lenses got it more right.

Another reason to ditch GNOME and bring Unity back.:P

---

### Post by Paddy Landau on 2022-01-23
> **vanadium said:**
> Wat version is this? For me Ubuntu 21.10. 
I have 20.04 (I keep to the LTS versions). So, I'll try again when I install 22.04 later this year.

In this case, I won't report an error; it might have been an advance view!
> **KBar said:**
> Another reason to ditch GNOME and bring Unity back.:P
I loved Unity, but it had too many technical problems, not least being Shuttleworth's refusal to stick to standards, and causing rifts with the wider coding community :(

Still, I find Gnome a pretty good system. I've enjoyed it so far, and parts of it are just like Unity was.

---

