---
title: "Inkscape can't import .eps and .ai"
date: 2005-11-02
forum: Desktop Environments
---

### Post by burre on 2005-11-02
When I try to import .eps- and .ai-files in Inkscape I get the following message:

> Couldn't load Perl module Image::Magick.  Images will be skipped.
Can't locate Image/Magick.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 1) line 1.
BEGIN failed--compilation aborted at (eval 1) line 1.

Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 115.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 115.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 115.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 115.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 115.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 115.

Any ideas how to solve this problem?

Thanks.

---

### Post by iluminate on 2006-05-28
Hi Burre,

Did you solve it?
I am having the same problemo and getting the same errormessage.
If you have a solution please make a post how you did.

Cheers

---

### Post by TRaiSe on 2006-06-03
You have to install the "perlmagick" package.

---

### Post by nitrofurano on 2006-07-01
ill2svg.pl is plenty of bugs (doesn't closes the <svg> and <g> tags, etc. ) - try ai2svg.py from [http://www15.brinkster.com/nitrofurano/python/](http://www15.brinkster.com/nitrofurano/python/) (is in the .zip file)

the usage is 'python ai2svg.py yourdrawing.ai'

the result will appear as neighbour to it named yourdrawing.ai.svg

it's still missing features like converting text blocks (i'm working on it) as well placed or embedded pictures, but you can convert simple pathes, joined pathes, dashes, etc... - rgb values are inverted cmyk colours (no callibrations yet...)

btw, i think it's better than nothing (or even better than ill2svg.pl...)

---

### Post by kperkins on 2006-07-13
I get this error: 
```

 File "/home/******/ai2svg.py", line 162, in ?
    hxfill_st=hexcmykrgbinv(float(v0_st),float(v1_st),float(v2_st),float(v3_st))0.44eError: invalid literal for float(): f


```
should I extract it to somewhere besides my home folder?

---

### Post by EcliptuX on 2006-07-28
> **TRaiSe said:**
> You have to install the "perlmagick" package.

Hi,

I want to open .ai file in Inkscape too, and I have installed perlmagick package.
But I have another error now :
```
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 318, <> chunk 22.
Argument ""`xcM-^R^gBM-\\M-kJM-^HM-(M-n^TTRLu!2M-^NM-rzM-}^Q6k4M-P..." isn't numeric in printf at /usr/share/inkscape/extensions/ill2svg.pl line 323, <> chunk 22.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 324, <> chunk 22.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 325, <> chunk 22.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 329, <> chunk 22.

```

What's wrong now ?

---

### Post by loyd86 on 2007-01-21
I have the exact same problem. I have installed anything that I can think of that goes with the libmagick. The python script did not work for me either.

---

### Post by glmeece on 2007-02-27
A possible solution (although not as elegant as a direct import) would be to use [Scribus]("http://www.scribus.net/") to import the EPS file, then export it as a SVG file.  My experience is that it doesn't work perfectly all the time, but for most files it works pretty well.

Give it a shot and see if that does it for you.  Obviously, not optimal if you have lots and lots of EPS files to work on, but if you're dealing with just a few - it's manageable.

---

### Post by engine on 2007-04-29
My Ubuntu offers me only Inkscape 0.43, which doesn't even list eps in the available file-types for import. Will installing this perl script you've been talking about help?

---

### Post by radiobuzzer on 2008-06-04
> **burre said:**
> When I try to import .eps- and .ai-files in Inkscape I get the following message:



Any ideas how to solve this problem?

Thanks.

I have installed pstoedit and solved it!

---

