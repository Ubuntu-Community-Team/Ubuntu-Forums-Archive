---
title: "Print large (A2) document on normal (A4) pages"
date: 2009-05-06
forum: General Help
---

### Post by Arndt on 2009-05-06
I have been sent a document (in PDF) that's meant to be printed on an A2 sheet. I have no such printer here, so I'd like to print it onto four separate A4 pages, and then glue them together. I can convert the document to postscript using acroread, and then rotate (because the document is meant to be printed in landscape mode) and offset using pstops, but I'm not succeeding very well in getting more than the first quadrant out. I thought I was nearly there, but the image is clipped (and my original ps file is not - I can see all of it in 'evince').

How do I use pstops (or some other tool) to do this?

---

### Post by Arndt on 2009-05-06
bump

---

### Post by unutbu on 2009-05-07
Well, there probably is a better way to do this than what I've come up with.

Here is the A2 pdf file I started with:
```

wget http://upload.wikimedia.org/wikipedia/commons/b/bf/Historique-A2.pdf -O input.pdf
```
acroread input.pdf
File>Print
Select from combobox "Page Scaling": "None"
Enable "Choose paper source by PDF page size"
Print to file: input.ps
```

psresize -Pa2 -pa4 input.ps resized.ps
```


If you view resized.ps I think you will find that it is still on a2 sized paper.
It looks like the original image is scaled by 0.5 relative to the lower left-hand corner.
The bounding box is too large.
I haven't found the right command to fix this. Instead, I manually edit the postscript file:

Manually edit resized.ps

Change 
```

%%BoundingBox: 0 0 1191 1684
```

to
```

%%BoundingBox: 0 0 595.5 842
```
```

pstops -d "@2.0(0,0)" resized.ps ll.ps 
pstops -d "@2.0(-1.0w,0)" resized.ps lr.ps 
pstops -d "@2.0(-1.0w,-1.0h)" resized.ps ur.ps 
pstops -d "@2.0(0,-1.0h)" resized.ps ul.ps 
```

The files ll.ps, lr.ps, ur.ps, and ul.ps show the 4 quadrants of input.pdf on A4 paper.

---

### Post by shane2peru on 2009-05-08
well to be honest with you my friend google is the expert on psnup and most things.  :)  I picked his brain a little and he says,
```

sudo apt-get install poster

```

then
```

man poster

```

I can guess you may need something like this:
```

poster -v -mA4 -pA2 -o toprint.ps yourA2.ps

```  That is only a guess, I haven't tried it you probably will have to play around with it a bit to figure it out.  But that certainly looks like what you will want.

Shane

---

### Post by Arndt on 2009-05-09
> **shane2peru said:**
> well to be honest with you my friend google is the expert on psnup and most things.  :) 

Google is sometimes my friend too. Thanks for the suggestions, I'll try them out.

---

### Post by Arndt on 2009-05-11
> **shane2peru said:**
> well to be honest with you my friend google is the expert on psnup and most things.  :)  I picked his brain a little and he says,
```

sudo apt-get install poster

```

then
```

man poster

```

I can guess you may need something like this:
```

poster -v -mA4 -pA2 -o toprint.ps yourA2.ps

```  That is only a guess, I haven't tried it you probably will have to play around with it a bit to figure it out.  But that certainly looks like what you will want.

Shane

Thank you, 'poster' solved my problem.

---

