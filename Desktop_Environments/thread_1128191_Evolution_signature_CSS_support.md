---
title: "Evolution signature CSS support"
date: 2009-04-17
forum: Desktop Environments
---

### Post by jubajuba on 2009-04-17
I work for a company with a standard HTML signature for e-mails. This signature includes CSS formatting.
```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
  <title></title>
<style type="text/css">
  div#signature p { color: #1f497d; font-size: 8pt; font-family: Arial, sans-serif; }
  div#signature a, div#signature a:visited { color: #5b83b6; text-decoration: none; }
  div#signature a:hover { text-decoration: underline; }
  div#signature span.company { font-weight: bold; }
  div#signature span.slogan { color: #c00000; }
</style>

</head>
<body>
<div id="signature">
...
...
...
</body>
</html>

```
When I try to import this signature to evolution the CSS formatting seems to be removed. I've also tried replacing ~/.evoltion/signature/signature-0 with the signature html file, the formatting is removed when I try to use the signature. Anyone know of a way to make CSS work in evolution?

---

### Post by gfe on 2009-04-17
I face exactly the same issue (which is why found your message).

I tried putting the font face in the font tag rather than using CSS, but Evolution filters it out. That's a bit surprising, since the Evolution native format does use the deprecated font tag to indicate size and it doesn't filter out color attributes.

I also tried nesting the font tag within the a=href tag in order to make a colored link (part of the style I'm supposed to follow), but Evolution moves it back outside the link tag.

There are things I like a lot about Evolution. But I'm surprised it doesn't support font changes within the body of a letter. Of if it does, it's far from intuitive.

---

### Post by ashbeats on 2009-04-25
Same here.. I've been trying to insert css into my signature with no
success. Shouldn't there be a way to insert raw html? 

Maybe a plug-in.... hmm :-({|=

```

<h3 style="background:#1A1A1A url(http://linkfuu.com/img/linkfuu_h2_bg.png) no-repeat scroll right center; border-left:4px solid #E49938; color:#DDDDDD; font-size:1.5em; font-weight:400; margin:0 0 12px; padding:12px 6px 12px 15px;">
LinkFuU</h3>

```


- John

---

### Post by nosarembo on 2009-05-21
No minimize to tray, no CSS signatures, why do they expect anyone to use this terrible client?

Oh well, back to crashy old Thunderbird + Lightning.

---

### Post by max3903 on 2009-08-03
Bug open since 2003 : [http://bugzilla.gnome.org/show_bug.cgi?id=247564](http://bugzilla.gnome.org/show_bug.cgi?id=247564)

---

### Post by rerooting on 2010-12-09
> **ashbeats said:**
> Same here.. I've been trying to insert css into my signature with no
success. Shouldn't there be a way to insert raw html? 

Maybe a plug-in.... hmm :-({|=


Actually, there is most certainly a way to insert raw html.  However, it rejects any inline CSS you add to it.  gtkhtml has posted a WONTFIX on CSS, i am sorry to say.  there is still a good amount that could be done, but alas.

anyways, the way to insert raw html is kind of strange, but is possibly a roundabout way of dealing with gtkhtml.  open a text editor and create an .html file with the html markup you want to insert.  dont worry about body, header, title or type tags.  just worry about the exact html you want to insert into the signature (in my case it was a remote image).

then, in the signature editor, go to insert > html file and select that file from a browser.  done!

this is definately something evolution needs to work on down the road!

---

