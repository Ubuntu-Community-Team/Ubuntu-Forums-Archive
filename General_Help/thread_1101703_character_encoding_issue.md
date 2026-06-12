---
title: "character encoding issue?"
date: 2009-03-20
forum: General Help
---

### Post by dazmcg on 2009-03-20
Hi, 

I'm writing some scripts to retrieve websites via curl. 

The problem i'm having is that international characters (non-ascii7?) are simply being stored as a black diamond with a question mark inside ("&#65533;") so that when viewing the text via terminal or via a web file via a browser this is all that appears in place of the character.

I can view the original web page fine directly with the character displaying normally (in this case Portuguese "ô")

Is this a platform issue - ie do i need to install some fonts, etc? or is it something curl specific (had the same issue with wget)?

Thanks!

---

### Post by dazmcg on 2009-03-21
Actually after playing around a bit, let me clarify the problem I'm having:

Using Curl /wget in either of the following ways:
<code>wget [http://www.google.com.br/](http://www.google.com.br/)
curl [http://www.google.com.br/](http://www.google.com.br/) > t.txt</code>

I then view either of the text files using text editor (have tried 'vim' and 'text editor') and international characters display 'normally'...eg:
"Preferências"

However when viewed using utilities like 'less' the same word is displayed as: "Prefer<EA>ncias".

Now it's not really 'less' that I have a problem with but when I try to load the text file via PHP, it doesn't correctly load the file - all the international characters display as a black diamond with a question mark in them....

Any ideas why?

---

### Post by dazmcg on 2009-03-21
closed!

I had tried "html_entity_decode" and "htmlspecialchars" functions thinknig they should have handled utf8 issues - solved by applying "utf8_encode($string)" function! DOH!

---

