---
title: "how to convert pdf to eps?"
date: 2009-05-14
forum: General Help
---

### Post by subjugater on 2009-05-14
Anybody know how could I convert a pdf figure into a eps one? Any console command, just like [COLOR="Red"]epstopdf[/COLOR]?

---

### Post by spcwingo on 2009-05-14
You can use the convert command, but each page will be created as a new document.  To run this command, say you have a file named "file.pdf" in your home directory that you want converted.  Open a terminal and type this command:

```
convert ~/file.pdf ~/file.eps
```

---

### Post by mbsullivan on 2009-05-14
> Anybody know how could I convert a pdf figure into a eps one? Any console command, just like epstopdf? 

Hmm... Well, there exist commands for PDF -> PS, and PS -> EPS.

So, you could try:

```
sudo aptitude install ps2eps
pdf2ps [file].pdf
ps2eps [newfile].ps
```

It'll probably do something strange, but give it a try.

Let me know how it works if you try it!
Mike

PS: There's another program for PDF -> PS called "pdftops". You could try both of them. I'm not sure what the difference is. Maybe you could tell me.

-----------------------------

PPS: Wait, there seems to be a simpler way... the "pdftops" command has a "-eps" switch. So try:

```
pdftops -eps [file].pdf
```

---

### Post by subjugater on 2009-05-15
> **spcwingo said:**
> You can use the convert command, but each page will be created as a new document.  To run this command, say you have a file named "file.pdf" in your home directory that you want converted.  Open a terminal and type this command:

```
convert ~/file.pdf ~/file.eps
```

Thank you at first. But I dont have the convert package and I can not even find it thru terminal or synaptic. Any further suggestion?

---

### Post by spcwingo on 2009-05-15
I'm exactly sure, but I think it is packaged with poppler-utils.

---

### Post by kaibob on 2009-05-15
Convert is a part of the Imagemagick package, which is in the repo's.

[http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)

---

### Post by subjugater on 2009-05-15
> **mbsullivan said:**
> Hmm... Well, there exist commands for PDF -> PS, and PS -> EPS.

So, you could try:

```
sudo aptitude install ps2eps
pdf2ps [file].pdf
ps2eps [newfile].ps
```

It'll probably do something strange, but give it a try.

Let me know how it works if you try it!
Mike

PS: There's another program for PDF -> PS called "pdftops". You could try both of them. I'm not sure what the difference is. Maybe you could tell me.

-----------------------------

PPS: Wait, there seems to be a simpler way... the "pdftops" command has a "-eps" switch. So try:

```
pdftops -eps [file].pdf
```

Buddy, thanks a lot. You know, you first suggestion aces your second one, though the latter one sounds simpler.

The thing is the second method loses a lot of effect of the original figure. The first method does too, but not as much as the first one.

Again, thanks.

---

### Post by subjugater on 2009-05-15
> **kaibob said:**
> Convert is a part of the Imagemagick package, which is in the repo's.

[http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)

Thank you so much, buddy. This software package seems fabulous! It is so versatile that I couldn't even imagine. Bravo~

---

### Post by tinwelint on 2010-07-27
I have to report that the 'convert' command from Imagemagick might not do exacly what you expect.

The default behaviour (in my installation at least) seems to be to convert the pdf to an eps with embedded bitmap graphics.
That's not what I wanted.

edit:
'pdftops -eps [file].pdf' made it for me though (but it couldn't take multiple files like 'pdftops -eps *.pdf').

edit2:
'for f in *.pdf; do pdftops -eps $f; done' solved the second problem.

---

### Post by whosane21 on 2011-11-14
Thanks for the great tips!  pdftops worked great and the imagemagick package was already pre-installed (I think it comes with Inkscape...?).

---

### Post by oldos2er on 2011-11-14
Closed, necromancy.

---

