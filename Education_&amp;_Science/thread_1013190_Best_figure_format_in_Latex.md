---
title: "Best figure format in Latex"
date: 2008-12-16
forum: Education &amp; Science
---

### Post by Glenn Jones on 2008-12-16
Hi 

Just a quick question what do people think is the best image format for importing figures into Latex? 

I've been using .eps and it seems that the re-scaling seems when importing it into my Latex document deteriorates the quality of the image. Axis labels etc seem fuzzy etc. Any recomendations?

Thanks

---

### Post by hugmenot on 2008-12-16
For Pdftex the best vector format ist PDF. Many programs can output PDF. Inkscape for example has good PDF output. As for raster images PNG is the best as long as you don&#8217;t include photopraphs, then it&#8217;s good old JPEG.
In plain Latex you can only include EPS, but it depends on how the EPS was generated. EPS can contain both vector and raster images. It&#8217;s basically only a container format.

---

### Post by samden on 2008-12-16
I use pdftex the whole time, and use pdf images. That works well for me, no problems with scaling so far and pdf is generally recognised more widely than eps.

---

### Post by eldragon on 2008-12-16
if you save vector graphics with eps, you will preserve their vectorness and they will scale properly.

ive been exporting from inkscape to eps, and had no problems so far.

from gimp on the other hand...... unless the image is big enough.... :(

---

### Post by Glenn Jones on 2008-12-17
I generate my images using matlab or as of a few days pythons matplotlib library and save them as .eps files. I then use gimp to crop the .eps images. I've had no problem with inkscape and .eps files. I guess if I can crop the images without using gimp then my problems may be solved? Or equally I can use pdf latex.

Cheers

---

### Post by ppm on 2008-12-17
Weird if you have problems with eps-format, because as stated before in this thread the quality should not deteriorate due to scaling. For me, the question about the best image format boils down to which way you are declined to produce the output document. If you use [FONT="Courier New"]latex->dvipdfm[/FONT] you should stick to eps-format. If you prefer [FONT="Courier New"]pdflatex[/FONT], you should (must) produce images in pdf-format.

---

### Post by skintythe1andonly on 2008-12-17
You can crop the .eps figures in latex, the problem is that .eps may not contain any info on the bounding box like a jpeg does. you need to include the bounding box option when you insert the .eps figure. I cant remember exactly off the top of my head how to do it but I used to do it ages ago when working with them.

---

### Post by eldragon on 2008-12-17
> **Glenn Jones said:**
> I generate my images using matlab or as of a few days pythons matplotlib library and save them as .eps files. I then use gimp to crop the .eps images. I've had no problem with inkscape and .eps files. I guess if I can crop the images without using gimp then my problems may be solved? Or equally I can use pdf latex.

Cheers

hmm, if you used the matlab eps directly, you would not have exporting issues. have you tried opening them with inkscape? never tried myself, but could work.

---

### Post by ssam on 2008-12-17
> **Glenn Jones said:**
> I generate my images using matlab or as of a few days pythons matplotlib library and save them as .eps files. I then use gimp to crop the .eps images. I've had no problem with inkscape and .eps files. I guess if I can crop the images without using gimp then my problems may be solved? Or equally I can use pdf latex.


That would be the problem. gimp will convert the eps data into a bit map when you open it, and then put the bitmap in the eps when you save it. so you loose the scalability of vectors. 

you could have a look at [http://pdfcrop.sourceforge.net/](http://pdfcrop.sourceforge.net/)

---

### Post by hugmenot on 2008-12-17
Ah, Matlab! That is informative. My current favorite solution to getting figures out of Matlab is this great SVG export script from Matlab File Exchange.

[http://www.mathworks.com/matlabcentral/fileexchange/7401](http://www.mathworks.com/matlabcentral/fileexchange/7401)

It is really poor that Mathworks never implemented SVG support and the EPS they generate is also a poor man&#8217;s solution. They basically route the printer file through an embedded Ghostscript they ship. You only have to zoom very far into the EPS output to see that for example a line plot has not a smooth line, but jagged line segments. Worst of all the EPS is not so clean, so touching up the plots is a pain. The plot has a lot of clipping masks and the characters are not preserved, etc.

So, instead try the SVG script above. It was written by a user, so it has to be run seprately, you cannot just use "Save Figure as". However, the output quality is worth it. You can load the resulting SVG in Inkscape, edit the plot to your hearts content, and /then/ export to EPS or PDF, dependign on whether you use plain (DVI-based) Latex or pdfTeX. I&#8217;d suggest the latter. It&#8217;s more efficient / less work.

---

### Post by skintythe1andonly on 2008-12-17
You can crop the .eps figures in latex, the problem is that .eps may not contain any info on the bounding box like a jpeg does. you need to include the bounding box option when you insert the .eps figure. From what i remember you did it like this

```
\includegraphics*[viewport= Lx Ly Rx Ry]{image.eps}
```

You can determine the points Lx Ly Rx Ry by opening the images in any ps viewer. You can also open the .eps file in a text editor and edit the bounding box there.

---

### Post by Glenn Jones on 2008-12-17
Thanks guys,

I'm currently giving pdfLatex a go. Things seem to be going well so far with the images imput as .png and .pdf files

---

### Post by samden on 2008-12-17
If you're intending to produce .pdf files as the end result, just use pdfLaTeX. Should fix all your problems. Good luck!

---

### Post by euler_fan on 2008-12-19
> **samden said:**
> I use pdftex the whole time, and use pdf images. That works well for me, no problems with scaling so far and pdf is generally recognised more widely than eps.
+1

As a suggestion, if you're using images which are outputs from some analysis (say in R), a best practice is to have it (if possible) output EPS and use gimp to scale it to the size you want it then convert it to JPEG or PDF in order to get the best look in the final document.

Otherwise you have to worry about sizing the images out of the gate and this can be sub-optimal.

---

### Post by hzambran_cl on 2008-12-19
> **Glenn Jones said:**
> Thanks guys,

I'm currently giving pdfLatex a go. Things seem to be going well so far with the images imput as .png and .pdf files

I'm also using pdflatex (in **Texmaker**) and I haven't had any scaling problems with PNG images. For me, PNG images are easier to manage and visualize than PDF files, because sometimes I add some minor details to the figures, and I can do it directly with Gimp. Also, if I need it the PDF format, I can use **inkscape** (with GUI) or **sam2p** (from the command line) to convert the PNGs into PDFs. However, if the images are really heavy (e.g., some maps), I choose the lightest between PNG or PDF format. 
At the end, for me both PNG and PDF, work fine with pdflatex.

---

### Post by hugmenot on 2008-12-19
> **euler_fan said:**
> 
As a suggestion, if you're using images which are outputs from some analysis (say in R), a best practice is to have it (if possible) output EPS and use gimp to scale it to the size you want it then convert it to JPEG or PDF in order to get the best look in the final document.

Sorry, that&#8217;s not actually the best practice. First you suggest to output EPS, when PDF is actually the better solution for TeX. You can output PDF from both Matlab and also R with the pdf() output device. Then you suggest to use Gimp to scale the images. This is wrong, Gimp will convert the nice clean vectors into a bitmap raster image, increasing the file size. JPG should not be used with plots because it uses compression unsuitable for line art.

---

### Post by hugmenot on 2008-12-19
> **hzambran_cl said:**
> I'm also using pdflatex (in **Texmaker**) and I haven't had any scaling problems with PNG images. For me, PNG images are easier to manage and visualize than PDF files, because sometimes I add some minor details to the figures, and I can do it directly with Gimp. Also, if I need it the PDF format, I can use **inkscape** (with GUI) or **sam2p** (from the command line) to convert the PNGs into PDFs. However, if the images are really heavy (e.g., some maps), I choose the lightest between PNG or PDF format. 
At the end, for me both PNG and PDF, work fine with pdflatex.

Making some edits to your graphics is much cleaner and easier with Inkscape because the edits are not destructive. If you stay with vectors throughout, you can edit your files over and over again, and e.g. change your earlier changes. Also, you cannot convert PNG to PDF properly, doing so will just embed the PNG into the PDF. This does not give you any gain at all.

---

### Post by Glenn Jones on 2008-12-27
Thanks guys for the suggestions. I have moved to using pdflatex and I'm using .png files as my figures. I thought I'd share this with you guys. I'm using ImageMagick command line tools to crop my images. The auto-crop function is very powerful:

```
convert image.png -trim image_crop.png
```

Cheers

---

### Post by grj23 on 2009-09-09
> **Glenn Jones said:**
> I generate my images using matlab or as of a few days pythons matplotlib library and save them as .eps files. I then use gimp to crop the .eps images. I've had no problem with inkscape and .eps files. I guess if I can crop the images without using gimp then my problems may be solved? Or equally I can use pdf latex.

Cheers

You can clip the .eps (and other formats) inside LaTeX.  Which I've always found handy.

E.g.

\includegraphics[bb=50 250 545 595, clip, width=8cm]{file}

where bb defines the bounding box (the first two numbers are the x,y-coords of the lower left corner, and the last two are the x,y-coords of the upper right corner (you can get these by mousing over the relevant spots in gsview and reading off from the bottom of the screen));
clip means include only those bits, ie cut away the rest of the eps;
then you can scale it if you wish, by width or height or a few other options in whatever units you want, inches if you must or pixels.

The other thing I tend to do is leave of the .eps extention.  So "file" not "file.eps".  That way, you can put file.eps and file.png or whatever in the same directory, and a postscript run will read the former and pdftex will read the latter.  I think that's right.

---

### Post by ahmatti on 2009-09-10
> **euler_fan said:**
> +1

As a suggestion, if you're using images which are outputs from some analysis (say in R), a best practice is to have it (if possible) output EPS and use gimp to scale it to the size you want it then convert it to JPEG or PDF in order to get the best look in the final document.


That can't be good for quality! If you use R you are much better of specifying the output size and the fonts etc. in R rather than taking the additional step using gimp. Or you could even use TikZ Device [http://r-forge.r-project.org/projects/tikzdevice/](http://r-forge.r-project.org/projects/tikzdevice/)

I don't think gimp can output vector graphics anyway so even the pdf will be of lesser quality...

---

### Post by hugmenot on 2009-09-10
Yeah, tikZDevice for R rocks my socks. Meanwhile there is also an extension for Inkscape that exports to a tikzpicture envirinment.

You realize that this thread had been lieing dead almost a year and you resurrected it?

---

### Post by germanium on 2009-09-20
I have a workflow for preparing (including cropping) vector images for inclusion in LaTeX documents that I'm pretty happy with.  (The cropping tip near the end of this post is probably the most useful thing I have to say.)

I produce documents via pdfLaTeX that contain numerous electronic circuit diagrams.  I create the individual circuit diagrams with XCircuit.  They export as postscript files.  Then I convert them individually to pdf's.  I use Adobe Acrobat's conversion capabilities, it provides a handy convert-ps-to-pdf option when I right click on a .ps file.  But I can just as well convert with something like Gsview.

If my document is to contain say 5 individual circuit diagrams I import all 5 individual (now pdf) circuit diagrams into a single inkscape page, using the File>Import... menu option. The 5 bare circuit diagrams are scattered about the page ready to be edited.  In my case I usually add some text to each circuit like component values, or add some arrows with labels pointing to some particular feature of the diagram that I want to highlight.  The plugin TeXText is great for using LaTeX markup for text in Inkscape.

I save the page as an Inkscape SVG that I can re-edit in the future if needed.

But then I'm ready to prepare each of the 5 polished circuit diagrams as its own individual pdf for inclusion in my LaTeX document.  I want the pdf to be only as large as the circuit diagram, no larger.  I don't want any unnecessary white space around the image.

So here's my cropping tip.  Within Inkscape I select the circuit diagram I want to export.  (I do the usual click-and-drag with the pointer tool to "select" all the elements of that one diagram.) Then, while selected, I choose the menu option File>DocumentProperties.  The DocumentProperties window opens.  There I click the button that says "Fit Page to Selection".  That reduces the page to the size of that one diagram.  (Don't worry, I don't lose the other 4 diagrams, because I don't overwrite the main .svg that contains the full set of 5.)  Then I use Save As... to save the selection as a pdf by selecting "PDF via Cairo" from the list of output file types in the Save As popup window, and giving it a unique name.  Voila.  I have a pdf of my vector image painlessly cropped to the minimum size possible.  No manual cropping.

At the Save As step I'm careful not to overwrite the main .svg file I'm working with.  I still want to be able to go back and export the other 4 circuit diagrams as individual pdfs, and keep that .svg around in case I need to re-edit a diagram.

I certainly recommend keeping vector images in a vector format throughout the process.  I do any scaling of the pdf image as an option when I call on the pdf from LaTeX; for example, \includegraphics[scale=0.6]{Circuit_1}.  This seems to work flawlessly.

I'd be happy to read the details of others' image preparation workflow.  It's a real bugaboo I've grappled with in various ways for a long time.  Take care.

---

### Post by raman_raja on 2011-01-26
I creaed a vector figure in Inkscape and saved it as a PDF file. But when I compiled it with Pdflatex I got the infamous 'bounding box not defined' error message. No forum could satisfactorily address this. Finally I found the answer by trial and error. This is my tex file with tips to solve the problem :
 
% Embedding vector graphics in Latex
% Create the vector graphics in InkScape
% Save it as PDF file, say myfigure.pdf
% Choose the option Export Area is Drawing at the second step of saving
% usepackage[pdftex]{graphicx} is important
% includegraphics{myfigure} without the .pdf extension is important
\documentclass{article}
\usepackage[pdftex]{graphicx}
\begin{document}
Hello world!
\begin{figure*}[t]
\centering
\includegraphics{myfigure}
\caption{Test}
\end{figure*}
\end{document}

---

### Post by xadder on 2011-01-31
I think that using eps2eps (or ps2ps) solves a lot of the problems discussed above. It takes an input .ps or .eps file, and creates a "distilled" .eps file which latex can handle (and scale!) without problems.

Usage:

eps2eps  original.eps   output.eps

(Also takes original.ps and produces an .eps)

Far faster than going through gimp or suchlike.

---

### Post by ppm on 2011-02-02
I guess xadder suggest that you export the file from inkscape first as eps. But, I guess you can not use eps files with pdflatex. If you choose to export as eps, I think you have to run: ```
epstopdf input.eps --outfile output.pdf
```.

---

### Post by FreeTheBee on 2011-02-02
You can load epstopdf in the tex file and convert eps to pdf on the fly, using

\usepackage[update]{epstopdf}
    \epstopdfsetup{suffix=}

The [update] option tells the package to convert only when the eps file that is encountered is newer than the accompanying pdf file. It speeds up compilation when the eps files have not changed.
The empty suffix option disables the default prefix that is added to the pfd filename. It is just a personal preference.

When using this package you need to compile, using the --shell-escape option, or \write18 needs to be enabled, since it calls epstopdf. I vaguely recall some restricted \write18 is enabled as a default in tl2010, but I'm, not sure.

---

### Post by xadder on 2011-02-03
Just a response to ppm

I was responding to the first post asking how to use .eps files. Inkscape came into the discussions later,as did R etc. There are so many options here, but sometimes I see recommendations to upload eg eps into gimp or inkscape and then re-export just to avoid BB problems. I prefer more direct solutions, that can be used on lots of files at once with a script if needed.

convert is also a very nice tool, as noted above.

---

