---
title: "stupid forum search limits"
date: 2008-02-28
forum: Forum Feedback &amp; Help
---

### Post by Polygon on 2008-02-28
I just tried to search using this term:

"Java on firefox 3"

and i got this message from the forum

> 
The search term you specified (3) is under the minimum word length (2) and therefore will not be found. Please make this term longer.

If this term contains a wildcard, please make this term more specific.


so HOW exactly am i supposed to make my search? I want to be specific for firefox 3...not just plain firefox...

---

### Post by icechen1 on 2008-02-28
Happened to me when I wanted to search something about the ls command.

---

### Post by KiwiNZ on 2008-02-28
replace 3 with three

---

### Post by Polygon on 2008-02-28
> **KiwiNZ said:**
> replace 3 with three

and get a bunch of results for 'firefox', which usually translates to firefox 2 which isnt what i want.... since everyone usually refers to firefox 3 as....firefox 3

---

### Post by angryfirelord on 2008-02-28
I think the reason for the limit is so the forum isn't pulling up the word "on" or other 1-2 letter words and returning 500+ posts, but I'm not sure of the real reason. Regardless, you can always use google and just add site:ubuntuforums.org to the end of your search terms.

[http://www.google.com/search?hl=en&client=firefox-a&channel=s&rls=org.mozilla%3Aen-US%3Aofficial&hs=GpF&q=java+firefox+3+site%3Aubuntuforums.org&btnG=Search]("http://www.google.com/search?hl=en&client=firefox-a&channel=s&rls=org.mozilla%3Aen-US%3Aofficial&hs=GpF&q=java+firefox+3+site%3Aubuntuforums.org&btnG=Search")

---

### Post by mips on 2008-03-01
> **Polygon said:**
> 
so HOW exactly am i supposed to make my search? I want to be specific for firefox 3...not just plain firefox...

Search the site with google: Java on Firfox 3 site:ubuntuforums.org

---

### Post by popch on 2008-03-01
It is usual behaviour for text search in a database to ignore non-count words. Since most implementations determine those on the base of word length, they will produce some by-catch, so to speak.

However, searching for 'firefox' alone will produce 115 hits, while searching for 'firefox_3' will produce one. Enter the terms without the quotes. Enter an underscore between 'firefox' and '3' in place of a space.

The other suggestions are valid as well. Use external searching services for more sophisticated searching.

You might also want to think about your use of words. If you say 'stupid' when you really mean "strange, I don't understand" some people might misunderstand your intention.

---

