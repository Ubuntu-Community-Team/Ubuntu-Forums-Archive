---
title: "Forum software adds a space at character position 64"
date: 2015-05-11
forum: Forum Feedback &amp; Help
---

### Post by Scooby-2 on 2015-05-11
If I put the following two lines in code tags, spaces are added at char position 64:

/nfs/Public *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
/nfs/janm *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)

```
/nfs/Public *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
/nfs/janm *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
```[COLOR=#000000]So the first line has a space after letter o in crossmnt and the second line has a space before the word crossmnt. This means that writing a tutorial for people to copy and paste can be difficult. The spaces cannot be removed, at least not by me.

Update: This seems to happen in the text as well, not just in the code sections. And it's intermittent...[/COLOR]

---

### Post by cariboo on 2015-05-11
> **Scooby-2 said:**
> If I put the following two lines in code tags, spaces are added at char position 64:

/nfs/Public *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
/nfs/janm *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)

```
/nfs/Public *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
/nfs/janm *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
```[COLOR=#000000]So the first line has a space after letter o in crossmnt and the second line has a space before the word crossmnt. This means that writing a tutorial for people to copy and paste can be difficult. The spaces cannot be removed, at least not by me.

Update: This seems to happen in the text as well, not just in the code sections. And it's intermittent...[/COLOR]

As you can see if the whole post is quoted, there aren't any spaces added. When reading your post, there aren't any spaces in code blocks, just the unformatted text.

**Edit:** Strange while creating the post there weren't any extra spaces, but once it is posted they reappear.

---

### Post by bapoumba on 2015-05-11
Test.
aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
```
aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
```

Edit : use code tags :)

---

### Post by coffeecat on 2015-05-11
012345678901234567890123456789012345678901234567890123456789

```
012345678901234567890123456789012345678901234567890123456789
```

> 012345678901234567890123456789012345678901234567890123456789

[html]012345678901234567890123456789012345678901234567890123456789[/html]

[php]012345678901234567890123456789012345678901234567890123456789[/php]

At the 51st char space, not 64th, in this experiment. And in post text and in quote tags only. @Scooby-2, if you managed to get spurious spaces in code within code tags you perhaps copy-pasted them from text in which the spaces had already been added? Neither bapoumba and I are getting unwanted spaces in code tags - nor in html and php tags either.

---

### Post by Scooby-2 on 2015-05-12
@all

Thanks for the replies. So the rule is that if you want to print something that people may want to copy and paste. always use CODE/HTML/PHP. The position of the added space depends on the text being printed. In the snip from the /etc/exports file it appears at position 64. Weird.

/nfs/Public *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
/nfs/janm *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
11111111111111111111111111111111111111111111111111111111111111111111111
(((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((
Quote:
> /nfs/Public *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)/nfs/janm *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
11111111111111111111111111111111111111111111111111111111111111111111111
(((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((
Code:
```
/nfs/Public *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)/nfs/janm *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
11111111111111111111111111111111111111111111111111111111111111111111111
(((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((
```
HTML:
[HTML]/nfs/Public *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)/nfs/janm *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)11111111111111111111111111111111111111111111111111111111111111111111111((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((([/HTML]
PHP:
[PHP]/nfs/Public *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)/nfs/janm *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)11111111111111111111111111111111111111111111111111111111111111111111111((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((([/PHP]

/nfs/Public *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)/nfs/janm *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
11111111111111111111111111111111111111111111111111111111111111111111111
(((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((

At least we know how to avoid it, but I found out after people copy-pasted from a post I submitted. BTW font/font size seem to have no effect.

---

### Post by coffeecat on 2015-05-12
I don't know why vbulletin is inserting a space after 50 consecutive printing characters in the body of the text and within quote tags, but I cannot think of a reason why anyone would want more than 50 consecutive printing characters in those two situations.

> **Scooby-2 said:**
> So the rule is that if you want to print something that people may want to copy and paste. always use CODE/HTML/PHP. 

The rule is - use code tags for code, terminal output and contents of configuration files, html tags for html code and php tags for php code. They all preserve formatting by maintaining white-spacing - which the main body text does not - and html and php tags add suitable colour coding to the code.

So, yes, use the appropriate BBCode tags for all posts and howtos. This is recommended not just to aid copy-pasting but to ensure readability. Not using code tags when needed is an all-too common mistake.

---

### Post by bapoumba on 2015-05-12
Just to add I had a look yesterday to see if this was documented and found nothing. I may not have been using the proper search terms because I have no idea if this is a vBulletin thing or something web designers would know about, and no idea how this would be called :)

---

### Post by coffeecat on 2015-06-05
> **bapoumba said:**
> Just to add I had a look yesterday to see if this was documented and found nothing. I may not have been using the proper search terms because I have no idea if this is a vBulletin thing or something web designers would know about, and no idea how this would be called :)

I've found it - and quite by accident. :) It's a vbulletin thing, more specifically I would guess a Ryan thing, a setting made in the dawn of time and quite forgotten since then. It's in ACP under Thread Display Options. It's set to insert a space after 50 characters to allow wrapping. Which makes sense I suppose!

---

### Post by bapoumba on 2015-06-07
Oh thanks coffeecat :)
Is this something that we still need ?

---

### Post by Elfy on 2015-06-07
> **coffeecat said:**
> I've found it - and quite by accident. :) It's a vbulletin thing, more specifically I would guess a Ryan thing, a setting made in the dawn of time and quite forgotten since then. It's in ACP under Thread Display Options. It's set to insert a space after 50 characters to allow wrapping. Which makes sense I suppose!

Looks like 50 is default 

> I also found this property in the ACP (which was already set to 50) ... 

[http://www.vbulletin.org/forum/showpost.php?p=2482883&postcount=4](http://www.vbulletin.org/forum/showpost.php?p=2482883&postcount=4)

---

### Post by coffeecat on 2015-06-07
> **bapoumba said:**
> 
Is this something that we still need ?

> **Elfy said:**
> Looks like 50 is default 

The odd thing is, if I reduce the width of my browser window, I get a horizontal scroll bar long before I have reduced the width to something that won't accommodate 50 consecutive characters, so I'm not sure what it's doing. Be that as it may, since 50 seems to be the default, and it hasn't caused problems in 10+ years, I vote for leaving as is. :)

---

### Post by bapoumba on 2015-06-07
> **coffeecat said:**
> The odd thing is, if I reduce the width of my browser window, I get a horizontal scroll bar long before I have reduced the width to something that won't accommodate 50 consecutive characters, so I'm not sure what it's doing. Be that as it may, since 50 seems to be the default, and it hasn't caused problems in 10+ years, I vote for leaving as is. :)

Yeah, that is the test I ran before posting, thinking browsers or vB software could not handle that at the time :)

---

