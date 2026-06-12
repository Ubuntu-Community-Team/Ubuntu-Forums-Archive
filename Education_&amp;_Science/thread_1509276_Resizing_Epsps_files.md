---
title: "Resizing Eps/ps files"
date: 2010-06-14
forum: Education &amp; Science
---

### Post by vancheese on 2010-06-14
Hi people

To publish a scientific article, I need to rescale all my eps figures to the appropriate size. I've tried googling around for ghostscript solution not no avail. Importing into inkscape isn't an option as it doesn't successfully import the figure

Does anyone have any suggestions or recipes

Cheers

Andy

---

### Post by Chronon on 2010-06-14
If you're using LaTeX it's trivial.  Just do something like this:

```
  \includegraphics[width=60mm]{myfig.eps}
```

---

### Post by vancheese on 2010-06-14
Yes, I know, but the journal wants the picture files submitted in the right size!
For 95% of the time, that would work perfectly :D

---

### Post by Chronon on 2010-06-14
What do you mean by the right size?  Do you mean the embedded preview image?  Or are they not able to process eps files?  

I don't really understand why setting the width of the graphic isn't acceptable here.

---

### Post by anglican on 2010-06-14
> **vancheese said:**
> Yes, I know, but the journal wants the picture files submitted in the right size!
For 95% of the time, that would work perfectly :D
How about something like:
```
pstops 1:0@0.8 infile.ps outfile.ps
```which would resize all pages in infile.ps to 80% of their original size in outfile.ps.

H

---

### Post by Chronon on 2010-06-14
Oh, that's a good program to know about.

Still, I don't get why scaling inside of the LaTeX document isn't acceptable.  I haven't heard of this before.  Asking you to scale the EPS sounds a lot like someone asking you to scale a TrueType font.

---

### Post by ppm on 2010-06-16
Maybe Image Magick would be an option for the job. Open your image

```
display myimage.eps
```

Resize and export it as a eps file.

---

### Post by vancheese on 2010-06-16
I found that I can do this all in scribus so I have!
I will try out these tips too!

Thanks

Andy

---

### Post by vancheese on 2010-06-16
> **Chronon said:**
> .

Still, I don't get why scaling inside of the LaTeX document isn't acceptable.  I haven't heard of this before.  Asking you to scale the EPS sounds a lot like someone asking you to scale a TrueType font.

I know, But this journal is a bit silly, I am using their latex style file and it differs from what they ask from in the authors' guidelines

---

### Post by Margaret Dumont on 2012-01-24
Good day!

Chronon, you're completely right that it's a stupid  thing to do, but nevertheless some scientific publications require you  to do it, [like the Journal of Chemical Physics]("http://jcp.aip.org/authors/information_for_contributors/how_to_prepare_illustrations"). Which frankly seems to me like a useless pain in the *ss for all of us.  :P

I  guess they want to make sure that, even if authors work in oversized  graphs, at least  in this last step they will realise that the text they  put in them is way too small to be read in the real size. At least,  that's the only logical explanation that occurred to me.  :)

I also find myself now on the need of resizing the EPS files again for this same reason. 

In  the past, I used some kind of graphics program to import the EPS,  resize it, and then export it again. Sometimes converting first the EPS  file to PDF format, because some programs import it better. Although I  could make this solution work, I wasn't very happy about it: some  programs mess it up when importing EPS or don't export them in very good  quality.

So, since I knew that EPS graphs where defined using  the Postscript programming language, I thought that it would be much  neater to directly modify the code that generates the graph, to obtain  the image in the required size. I explain here how I did it, in case  someone finds it useful.

[LIST=1]
[*]Install some kind of hexadecimal editor (I went with Midnight Commander).
[*]Open the EPS file with it and add the following line after the EPS header (where sx and sy are the factor values you need to  rescale the image to the required size). ```
sx sy scale
```
[*]Edit the x and y values in the following line to define  the corresponding new page size (otherwise your graph will have useless  blank space or the image will be cropped). ```
%%BoundingBox 0 0 x y
```
In one of the graphs there was this extra line and I also had to change the x and y values. ```
%%PageBoundingBox 0 0 x y
```
[/LIST]
I don't know whether the experts will be horrified, but it worked perfectly for me.   :)

Cheers!

---

### Post by KLuwak on 2012-11-15
> **ppm said:**
> Maybe Image Magick would be an option for the job. Open your image

```
display myimage.eps
```

Resize and export it as a eps file.

I'm pretty sure that will rasterize the file, which is probably not what you want.

---

### Post by cayun on 2012-11-17
I have same problomes with you,but now solved

---

### Post by frisket on 2012-12-11
> **vancheese said:**
> Hi people

To publish a scientific article, I need to rescale all my eps figures to the appropriate size. I've tried googling around for ghostscript solution not no avail. Importing into inkscape isn't an option as it doesn't successfully import the figure

Does anyone have any suggestions or recipes

Cheers

Andy

Install ImageMagick and type

convert myfile.eps -resize 75% myfile-smaller.eps

(or whatever)

---

### Post by nishant1234 on 2012-12-14
Is any type of mathematics articles can be posted here.

---

