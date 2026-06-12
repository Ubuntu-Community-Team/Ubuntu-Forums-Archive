---
title: "Suggest disabling search until it works..."
date: 2008-03-04
forum: Forum Feedback &amp; Help
---

### Post by pmorch on 2008-03-04
Several times also in the past I have experienced that the search tool on these forums seems broken. 

In the  [Why doesn't forum search work?]("http://ubuntuforums.org/showthread.php?t=686518") thread, [jaytek13]("http://ubuntuforums.org/member.php?u=187457") suggests to use "Search Titles Only" from advanced search, and [LaRoza]("http://ubuntuforums.org/member.php?u=266234"), a Ubuntu Forum Staff member, suggests to use quotes and/or use google for searching.

So even the Ubuntu Forum Staff cannot search the forums using the built-in search tool with reliable results. Then please disable the search altogether and replace it with a simple input field that does a Google search!

Here is a failing search example: There is a thread called [update "cannot be authenticated" ]("http://ubuntuforums.org/showthread.php?t=304430") and another: [update packages cannot be authenticated]("http://ubuntuforums.org/showthread.php?t=53210") . However searching for the string "cannot be authenticated" (with or without the quotes, with or without using the "Search Titles Only" from the [Advanced Search]("http://ubuntuforums.org/search.php") page), gives this message:

[quote="Search Engine"]
The following errors occurred with your search:

   1. Sorry - no matches. Please try some different terms. 
[/quote]

Clearly, that is wrong. There are matches. I found them! Why doesn't search find a thread with that exact phrase in the title??? Searching for 'site:ubuntuforums.org "cannot be authenticated"' in Google gives 10 threads. But none when using the ubuntuforums search engine. 

Searching for "underline" (without quotes) *does* find something, so now I'm totally confused...

Isn't search simply broken? In my opinion, either search should work reliably, or it shouldn't be there at all. And I seem to remember having been troubled with this earlier too, so I don't think it is a new problem.

I hope someone can tell me how to find the 10 threads with "cannot be authenticated" in the title reliably using the search engine, or hope to see searching disabled.

Peter

---

### Post by bapoumba on 2008-03-04
Please try without 2-char words in the Search field (1 or 2 character words make the search fail), and search for titles only. This brings up 11 threads.

---

### Post by kko1 on 2008-03-04
Hello.

I have come across this problem as well, and find it annoying. *Now, I understand that there may be technical reasons for why the search terms are limited, but I feel the situation is not ideal as it stands.* Let me elaborate.

> **bapoumba said:**
> Please try without 2-char words in the Search field (1 or 2 character words make the search fail)

There are two issues here:

*

1. **When searching with quotes**, the length of the words included *within* the actual search term (the whole string) **should not** matter. I find it hard to understand why it does, and think that it is either a **bug** or, if not a bug, a **serious limitation** in the (current) forum search function.

In other words, a search with...
```
"cannot be authenticated"
```
should always work, even if a search with...
```
cannot be authenticated
```
fails.

Moreover, if I am not mistaken, **the latter search** (without the quotes) **used to give a warning** that some search terms were shorter than 3-characters, and suggest adjusting the search terms. Now, this warning is no longer shown, and only a *"Sorry - no matches."* is given. *This is clearly a problem, and highly inaccurate.*

*

2. When searching *without* quotes, the word-length limitation is (as described) currently *not* shown at all. This is also a problem.

For this, I have two suggestions:
- Either bring back the warning that I seem to recall existed at some point in time.
- Or add a **clearly visible** mention of the word-length limit on the advanced search page near the text input boxes.

- An intelligent search engine *could* also simply drop those too short terms, *but warn the user on the results page that this was done.* (Just as long as the equivalent of the following doesn't happen ;) )
> <Insomniak`> Stupid ******* Google
<Insomniak`> "The" is a common word, and was not included in your search
<Insomniak`> "Who" is a common word, and was not included in your search

*

In the hopes that this will be seen as constructive feedback towards better usability of the forum search engine,

kko1

PS. You can search for The Who (with or without quotes) nowadays on Google. :KS

---

### Post by Cryophallion on 2008-03-06
> **bapoumba said:**
> Please try without 2-char words in the Search field (1 or 2 character words make the search fail), and search for titles only. This brings up 11 threads.
I just had this problem with searching for "static ip".

It is much harder with so many abbreviations out there to not be able to put in standard two letter abbreviations like "ip".

Also, there have been a number of times that a person posts to a thread where the title doesn't really address what you are looking for, or there may be a huge thread with only one response that fits (another pet peeve is not being able to go right to the post that has the keywords).

So, while some search is ok, the existing search is not really acceptable for use, and should be fixed. As I posting in the brainstorm before I found this thread:

"This has happened to me a number of times and is very frustrating. It says keyword(s), but it never seems to work right. Add that to a 15 second delay if you had a typo and it ends with a rather annoyed user who can't find help on a problem that is already most likely irked by the problem they are trying to solve."

As many people are trying out Ubuntu and finding help here, we should really have a working search system to not frustrate them more.

---

### Post by bapoumba on 2008-03-06
Hmm, yes, IP is tricky.

I'm not sure if we are still using the sphinx plugin for the search (u-g ?), but the results are far better with it than without. The delay between searches (and posts) helps the servers load.

---

### Post by Cryophallion on 2008-03-07
I understand the reason for the delay, I'm just saying that when searches aren't working, the delay gets frustrating.

Would changing it to 10 from 15 be too much extra load on the servers? It always seems I have 5 or 7 seconds left when I click. If the cons aren't too bad, maybe it could be changed in the interest of ease of use. Has this been attempted or looked at?

---

