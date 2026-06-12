---
title: "Using Python to output LaTeX equations"
date: 2011-03-16
forum: Education &amp; Science
---

### Post by wesg on 2011-03-16
I have a file filled with LaTeX equations that I'd like to output into high quality PNG files. I've tried manually, but that's super tedious and annoying. A number of graphics output libraries have been brought to my attention, but none seem to go right to PNG or include basic equations.

Anyone have any suggestions?

---

### Post by chandra on 2011-03-16
> **wesg said:**
> I have a file filled with LaTeX equations that I'd like to output into high quality PNG files. I've tried manually, but that's super tedious and annoying. A number of graphics output libraries have been brought to my attention, but none seem to go right to PNG or include basic equations.

Anyone have any suggestions?

It depends on what exactly you want.

If you have TeXLive 2010 installed and are aware of the standalone class and the preview package, you can get your entire file of equations come out as a single PDF that may be converted into a PNG file of suitable resolution using the convert utility of the ImageMagick suite.

Note that the TeXLive 2010 is not available as a .deb package but must be installed following instructions here:

[http://www.tug.org/texlive/](http://www.tug.org/texlive/)

The ImageMagick suite is available as a .deb file from the repos.

If you need each equation to be a standalone image, you might need to partition your single file into n files and process each with pdflatex and convert using a simple bash script.

If you can provide more details, I might be able to assist more.

---

### Post by wesg on 2011-03-16
Ideally I'd like to loop through a file with equations, and have each output as a separate image. By using Python, I'm hoping to be able to output multiple sized images in the same script. 

If you have any more pointers, I'm kind of stuck on actually outputting anything from LaTeX in Python.

---

### Post by chandra on 2011-03-22
Dear wesg,

I have here a proof of concept demo. I am not fluent in python and therefore must leave it to you to pythonize the bash workflow I have indicated here.

There are basically two steps:

1. Use pdflatex and the preview package to generate one equation per page from your file of LaTeX equations. Here is sample file with two equations:

```
% equations.tex
% Provides multiple equations in a single file
% Compile with pdflatex to get as many pages as there are equations
% BUG: there is leading white space in page for each equation
% Current workaround is to use pdfcrop to crop each page of equations.pdf
% Usage:
% pdflatex equations; pdfcrop equations.pdf
%
\documentclass[12pt,a4paper]{article}
\usepackage[active,displaymath,tightpage]{preview}
\begin{document}
% First equation
\[
e^{-\pi i} + 1 = 0
\]
% Second equation
\[
\sin\frac{\pi}{6} = 0.5
\]
\end{document}
```
2. Execute this bash script:
```
#! /bin/bash
# Demo script to illustrate creation of 
# individual images from individual LaTeX equations
# Requires the following Open source/libre software
# 1. pdflatex, preview package, and pdfcrop utility, all  preferably from TeXlive 2010
# 2. ImageMagick 7 suite
# 3. pdftk 1.41
# 
# Please tweak parameters and file names to suit your purpose
# May be made into a bash loop; pythonized; perlized etc.
#
pdflatex equations
pdfcrop equations.pdf
pdftk equations-crop.pdf burst output equation_%02d.pdf
convert -units pixelsperinch -density 1200 -resize 900 equation_01.pdf equation_01.png
convert -units pixelsperinch -density 1200 -resize 900 equation_02.pdf equation_02.png
```
You need bash and the the packages listed above.

If you do not have bash, you might try to pythonize the above script.

Let me know how you fare.

---

### Post by daviesk24 on 2011-04-02
wesg,

I was just now trying to solve the same problem.  Here is what I did:
1. used the extract package to extract all "equation" and "align" environments into a separate document named equations.tex (without preamble or begin/end document).
2. wrote and ran a Python script that:
a) splits the file into separate files each with one equation
b) runs PDFLaTeX on each one
c) runs pdfcrop to trim the PDFs
d) runs ImageMagick to convert the PDFs to PNGs

I hope it helps you.

Kevin  

Here is an example tex document with some equations:
```

\documentclass[11pt]{article}

\usepackage{amsmath}
\usepackage[active,header=false,handles=false,copydocumentclass=false,generate=equations,extract-env={equation,align}]{extract} % Extract equations to a separate file.

\begin{document}

State space equations \ldots \emph{This text won't appear with the extracted equations.} 
\begin{subequations}%
\begin{align}%
\dot{x} &= A\times x + B\times u \\
y &= C\times x + D\times u
\label{eq:StateSpace}
\end{align}
\end{subequations}

Controllability matrix \ldots Equation \ref{eq:ControllabilityMatrix} \ldots:
\begin{equation}
K = \begin{bmatrix}B & A\times B & A^2\times B & \ldots & A^{n-1}\times B\end{bmatrix}
\label{eq:ControllabilityMatrix}
\end{equation}

Observability matrix \ldots Equation \ref{eq:ObservabilityMatrix} \ldots:
\begin{equation}
L = \begin{bmatrix}
	    C\\ 
	    C\times A\\
	    C\times A^2\\
	    \vdots\\
	    C\times A^{n-1}
      \end{bmatrix}
\label{eq:ObservabilityMatrix}
\end{equation}

\end{document}
```

Save this to "equations_preamble.tex":
```

\documentclass[11pt]{article}

\pagestyle{empty} % No page numbers

\usepackage{amsmath}

% Don't display equation numbers. (This is a hack.)
\usepackage{mathtools}  
\mathtoolsset{showonlyrefs}
```

Compile the main tex file.  Then run this Python code on the "equations.tex" file created by the extract package and the "equations_preamble.tex" file above.
```
#!/usr/bin/env python
# Pull individual LaTeX environments from a file, attach a preamble, and compile
# the results into PDF and PNG files.
#
# Requires the following open source/free software:
# 1. pdflatex and pdfcrop utility
# 2. ImageMagick suite
#
# Created by Kevin Davies, 4/1/11

import os, shutil, re

## Settings 
preamble = 'equations_preamble.tex' # Name of file containing the preamble (just short of \begin{document})
src_fname = 'equations.tex' # Path and filename of the source
dest = 'Extractions' # Destination directory
env_names = ['equation', 'align'] # Names of LaTeX environments to look for (The starred versions will be searched as well.)
out_prefix = "eq" # Prefix for the compiled files.


## Procedure

# Read the source file.
src = open(os.path.join(src_fname), 'r')
src_tex = src.read()
src.close()

# Copy the source to destination directory (for reference).
if not os.path.exists(dest):
    os.mkdir(dest)
shutil.copy(src_fname, os.path.join(dest, os.path.basename(src_fname)))
    
# Find occurances of the environments.
occurances = []
for env_name in env_names:
    occurances.extend([m.start() for m in re.finditer('begin{' + env_name + '}', src_tex)])
    occurances.extend([m.start() for m in re.finditer('begin{' + env_name + '\*}', src_tex)])
occurances.sort()

# Compile the environments.
for i in xrange(len(occurances)):
    base = out_prefix + str(i+1) # Base filename of the working files
    shutil.copy(preamble, base + '.tex') # Copy the preamble file.
    
    # Add the environment to the working file.
    work = open(base + '.tex', 'a')
    work.write('\n\\begin{document}' + '\n\n')
    if i < len(occurances) - 1:
        work.write(src_tex[occurances[i]-1:occurances[i+1]-2] + '\n')
    else:
        work.write(src_tex[occurances[i]-1::] + '\n')
    work.write('\end{document}' + '\n')
    work.close()

    # Run LaTeX on the file and process the images.	
    #os.system('latex ' + str(fnum) + '.tex') # Create DVI
    #os.system('dvipng -D 600 ' + str(fnum) + '.dvi') # Create PNG.
    #os.system('dvipdf ' + str(fnum) + '.dvi') # Create PDF.
    os.system('pdflatex ' + base + '.tex') # Create PDF.
    os.system('pdfcrop ' + base + '.pdf ' + base + '.pdf') # Crop white space around equation.
    os.system('convert -units pixelsperinch -density 1200 -resize 900 ' + base + '.pdf ' + base + '.png') # Convert to PNG.
    
    # Move the files and clean up.    
    os.rename(base + '.pdf', os.path.join(dest, base + '.pdf'))
    os.rename(base + '.png', os.path.join(dest, base + '.png'))    
    for ext in ['tex','abo','aux','glo','log','mao','xdy']:
        os.remove(base + '.' + ext)
    print "Created " + base + ".pdf and " + base + ".png"

```

---

### Post by daviesk24 on 2011-04-02
I'm sorry.  You'll need to change this line:
> for ext in ['tex','abo','aux','glo','log','mao','xdy']:to this:
> for ext in ['tex','aux','log']:
in the Python code.

---

### Post by wesg on 2011-05-10
Thanks for the input, everybody. I just found this thread again after searching for a slightly different solution. I solved my original problem by using a bash script that includes the pdftex functions. It seems to do the job nicely.

My next challenge is to simplify my job even more by converting LaTeX code to actual c code (as in /frac{1}{2} == 1/2. I don't think Python includes a library for this, so I'll have to take a look at making a rudimentary version myself. If I can do it, it should save me a lot of time over the long run.

---

