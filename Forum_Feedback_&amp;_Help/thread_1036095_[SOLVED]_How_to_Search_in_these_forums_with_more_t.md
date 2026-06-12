---
title: "[SOLVED] How to Search in these forums with more than one keyword?"
date: 2009-01-10
forum: Forum Feedback &amp; Help
---

### Post by The Question on 2009-01-10
I would like to, for example, search for all posts containing BOTH the keywords OpenOffice and hyperlink.  The search engine seems to return all posts with EITHER word in them no matter what I do.

---

### Post by drs305 on 2009-01-10
Normally the ubuntu search options are fine. Sometimes I go externally to Google to use it's full range of search options. 

I have a shortcut set up so it's pretty easy. This link takes you to a Google page which will search for posts on the ubuntu forums for the past year (you can make one for anytime, 24 hours, week, month or year):

[_Google Forum Search_]("http://www.google.com/search?num=30&hl=en&lr=&q=site%3Aubuntuforums.org&as_qdr=y&btnG=Search")

Add a space, then type the search terms. It uses the Google search logic, so it will look for posts with all the entered words.

Since this is an external site, immediate posts may not show up for a while.

---

### Post by mc4man on 2009-01-10
If you do have occasion to search in this site you should choose 'advanced search' and in most cases limit your search to a particular forum.
Searches here are limited to 250 results so that increases your chances.

keyword+keyword will do what you asked.

another google method is to use

keywords site:ubuntuforums.org

---

### Post by Rocket2DMn on 2009-01-10
Moved to Forum Feedback & Help.

---

### Post by sdennie on 2009-01-10
You can also place the following in ~/.mozilla/firefox/*.default/searchplugins/ and get a google search for Ubuntu forums in the Firefox search bar:

```

<SearchPlugin xmlns="http://www.mozilla.org/2006/browser/search/" xmlns:os="http://a9.com/-/spec/opensearch/1.1/">
<os:ShortName>Ubuntu Forums</os:ShortName>
<os:InputEncoding>UTF-8</os:InputEncoding>
<os:Image width="16" height="16">data:image/x-icon;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABmJLR0QA/wD/AP+gvaeTAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH1gUYBy8UWHdfBwAAAcJJREFUOMuVk09IVFEUxn/nNb7pkbV7r4jQQHKTbQya2rSxJJmoRbYLEqZl0MJolataFkW4k0ebmDaVCD4EEQdsEW+aTRuxdKGDCDMuhJjxNWN5WnjHzHkqntW958/lu993PjhEhHjDId5iiHerkZO9mjXjtADdwGVgY+lLcqo0a3835ekU5R6ARNNg7uxRqmsOo/UscKORb79Se1SatceBa0A2FoEqwoQ7jeocn6ojwFfAMuUa8LRWkYVkqy6LHxWaHwjcAeAt8AfdvMDoegewCnjAfeCOaS0C58WPKvIPutvKOvPAKYQVNqRbbpdLu3gZAR6Y65D40XNLM067ZpxBwnonEJm/PN49bOIZUDfn3gaJH4GLzNe/0dXyBpFXbOpMnDLiR0XNOPeADuBXrAoHRd4/vuMWkTDE9HPOziHyAQBLrgLvYxapDXgH2MBn4LUlfrQkfvSSlP0DcLawygsd807GABgywwCTB8qYv3lkXxlTlCt7LlI+bcUuUuKELvz+KcspyoUmEkVQzR3ro7rmQDK7YxjgyaVAr29JqQ9JU9jXTCHef2Y6M6BTp++ybSZJr/YcVkE0cIc1cBc1cLft/BckXKkAO9v5fAAAAABJRU5ErkJggg==</os:Image>
<os:Url type="text/html" method="GET" template="http://www.google.com/search?q={searchTerms}&amp;sitesearch=ubuntuforums.org">
</os:Url></SearchPlugin>

```

(Yes, that's safe.  The scary stuff is just an ASCII representation of the icon used.)

---

### Post by jocko on 2009-01-11
> **sdennie said:**
> You can also place the following in ~/.mozilla/firefox/*.default/searchplugins/ and get a google search for Ubuntu forums in the Firefox search bar:

```

<SearchPlugin xmlns="http://www.mozilla.org/2006/browser/search/" xmlns:os="http://a9.com/-/spec/opensearch/1.1/">
<os:ShortName>Ubuntu Forums</os:ShortName>
<os:InputEncoding>UTF-8</os:InputEncoding>
<os:Image width="16" height="16">data:image/x-icon;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABmJLR0QA/wD/AP+gvaeTAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH1gUYBy8UWHdfBwAAAcJJREFUOMuVk09IVFEUxn/nNb7pkbV7r4jQQHKTbQya2rSxJJmoRbYLEqZl0MJolataFkW4k0ebmDaVCD4EEQdsEW+aTRuxdKGDCDMuhJjxNWN5WnjHzHkqntW958/lu993PjhEhHjDId5iiHerkZO9mjXjtADdwGVgY+lLcqo0a3835ekU5R6ARNNg7uxRqmsOo/UscKORb79Se1SatceBa0A2FoEqwoQ7jeocn6ojwFfAMuUa8LRWkYVkqy6LHxWaHwjcAeAt8AfdvMDoegewCnjAfeCOaS0C58WPKvIPutvKOvPAKYQVNqRbbpdLu3gZAR6Y65D40XNLM067ZpxBwnonEJm/PN49bOIZUDfn3gaJH4GLzNe/0dXyBpFXbOpMnDLiR0XNOPeADuBXrAoHRd4/vuMWkTDE9HPOziHyAQBLrgLvYxapDXgH2MBn4LUlfrQkfvSSlP0DcLawygsd807GABgywwCTB8qYv3lkXxlTlCt7LlI+bcUuUuKELvz+KcspyoUmEkVQzR3ro7rmQDK7YxjgyaVAr29JqQ9JU9jXTCHef2Y6M6BTp++ybSZJr/YcVkE0cIc1cBc1cLft/BckXKkAO9v5fAAAAABJRU5ErkJggg==</os:Image>
<os:Url type="text/html" method="GET" template="http://www.google.com/search?q={searchTerms}&amp;sitesearch=ubuntuforums.org">
</os:Url>

```(Yes, that's safe.  The scary stuff is just an ASCII representation of the icon used.)

That's a nice tip, but I think you may have missed something in there.
I fiddled a little with it and got this to work:
```
<SearchPlugin xmlns="http://www.mozilla.org/2006/browser/search/" xmlns:os="http://a9.com/-/spec/opensearch/1.1/">
<os:ShortName>Ubuntu Forums</os:ShortName>
<os:Description>Search Ubuntu Forums</os:Description>
<os:InputEncoding>UTF-8</os:InputEncoding>
<os:Image width="16" height="16">data:image/x-icon;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABmJLR0QA/wD/AP+gvaeTAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH1gUYBy8UWHdfBwAAAcJJREFUOMuVk09IVFEUxn/nNb7pkbV7r4jQQHKTbQya2rSxJJmoRbYLEqZl0MJolataFkW4k0ebmDaVCD4EEQdsEW+aTRuxdKGDCDMuhJjxNWN5WnjHzHkqntW958/lu993PjhEhHjDId5iiHerkZO9mjXjtADdwGVgY+lLcqo0a3835ekU5R6ARNNg7uxRqmsOo/UscKORb79Se1SatceBa0A2FoEqwoQ7jeocn6ojwFfAMuUa8LRWkYVkqy6LHxWaHwjcAeAt8AfdvMDoegewCnjAfeCOaS0C58WPKvIPutvKOvPAKYQVNqRbbpdLu3gZAR6Y65D40XNLM067ZpxBwnonEJm/PN49bOIZUDfn3gaJH4GLzNe/0dXyBpFXbOpMnDLiR0XNOPeADuBXrAoHRd4/vuMWkTDE9HPOziHyAQBLrgLvYxapDXgH2MBn4LUlfrQkfvSSlP0DcLawygsd807GABgywwCTB8qYv3lkXxlTlCt7LlI+bcUuUuKELvz+KcspyoUmEkVQzR3ro7rmQDK7YxjgyaVAr29JqQ9JU9jXTCHef2Y6M6BTp++ybSZJr/YcVkE0cIc1cBc1cLft/BckXKkAO9v5fAAAAABJRU5ErkJggg==</os:Image>
<os:Url type="text/html" method="GET" template="http://www.google.com/search?q={searchTerms}&amp;sitesearch=ubuntuforums.org">
</os:Url></SearchPlugin>

```I think the important part you missed was "</SearchPlugin>" at the end...
I saved the file as "ubuntuforums.xml" in the folder you suggested and restarted firefox.

---

### Post by sdennie on 2009-01-11
> **jocko said:**
> I think the important part you missed was "</SearchPlugin>" at the end...
I saved the file as "ubuntuforums.xml" in the folder you suggested and restarted firefox.

Ooops.  Forgot the closing XML tag.  ;)

---

### Post by Joeb454 on 2009-01-11
> **sdennie said:**
> Ooops.  Forgot the closing XML tag.  ;)

Now be a good forum user and correct your post ;)

---

### Post by sdennie on 2009-01-11
> **Joeb454 said:**
> Now be a good forum user and correct your post ;)

/me mumbles something mean about Joeb454

---

### Post by Joeb454 on 2009-01-11
> **sdennie said:**
> /me mumbles something mean about Joeb454

* ChanServ gives channel operator status to Joeb454

---

### Post by The Question on 2009-01-11
Thank you for the suggestions.  drs305's seems like the easiest and I was able to get it to work.  Maybe I'll mess with making an xml file a bit later. ;)

mc4man I assume is talking about google advanced search in his post?  I see no option for advanced search on the ubuntu forums search page, nor does keyword+keyword work from there.

---

### Post by drs305 on 2009-01-11
> **The Question said:**
> I see no option for advanced search on the ubuntu forums search page, nor does keyword+keyword work from there.

The Advanced Search options are available when you select the Search link at the very top of the page. It allows search options that are fairly specific, and unique, to the ubuntu forums. The advance search options don't include the type of search you were looking for but do offer very useful tools for defining forum-specific searches for users, specific forums, etc.

---

### Post by mc4man on 2009-01-13
> The advance search options don't include the type of search
Well it does use the + with some limitations but can narrow the results.
If seems to use the whole thread as a basis for results and with more than 2 keywords may return once 2 are present.
You can to some extent alter that with quotes included..

for instance 
black white video
[http://ubuntuforums.org/search.php?searchid=54409044](http://ubuntuforums.org/search.php?searchid=54409044)

black+white+video
[http://ubuntuforums.org/search.php?searchid=54408462](http://ubuntuforums.org/search.php?searchid=54408462)

"black and white"+video
[http://ubuntuforums.org/search.php?searchid=54409735](http://ubuntuforums.org/search.php?searchid=54409735)

---

