---
title: "error loading .m files on octave"
date: 2012-12-19
forum: Education &amp; Science
---

### Post by fr33c0untry on 2012-12-19
hi guys,
im noob in octave. i get the following error whenever i load a . m file :

" [B]error: load: test_plot.m: inconsistent number of columns near line 3
   error: load: unable to extract matrix size from file `test_plot.m'  [/B]       "

this happens for all the files that I've either downloaded from the internet, cut-copy-paste
or written them myself on emacs.Is there something i've done wrong?

Another question,are there any active communities dedicated to octave?i couldnt find any on google.is it because the coding  is the same as matlab,so most users go to their websites?

---

### Post by steeldriver on 2012-12-19
What are you trying to do exactly? the 'load' command is usually used for data files (e.g. .mat files) not for the .m files themselves

If you want to run a matlab **script **file called *file.m* just type *file *(no .m) at the command line - the syntax is the same whether you are running octave or matlab iirc

---

### Post by fr33c0untry on 2012-12-19
what i'm trying to do i run a .mat file (i realized my mistake .mat not .m, thanks) on octave.

---

### Post by fr33c0untry on 2012-12-19
ok i get it now. to run a .m file which is already saved i just have to enter the file name without the .m .the load command is to  load the saved workspace on the command line.

but can anyone answer my second question.

---

### Post by steeldriver on 2012-12-19
Well speaking personally I find most of what I need in the MATLAB docs online - only resort to trawling for octave-specific info if I need to use a function that has no direct MATLAB equivalent (for example, recently working with optimization and there was an octave function that 'did the same thing' but was called something different and had a different parameter list and setup requirements).

But I am a fairly basic user - ymmv

---

### Post by fr33c0untry on 2012-12-19
what about getting help.is this community fine

---

### Post by steeldriver on 2012-12-19
well you can try - there are sure to be a few users here

maybe try in the Programming Talk subforum - seems to get more traffic than Education + Science

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by fr33c0untry on 2012-12-19
Great thanks for the helphttp://ubuntuforums.org/images/smilies/icon_razz.gif

---

