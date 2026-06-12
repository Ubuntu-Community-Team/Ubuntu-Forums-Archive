---
title: "Creating my own /Usepackage in latex"
date: 2013-03-13
forum: Education &amp; Science
---

### Post by Physics Eskimo on 2013-03-13
Hi guys, I searched this up on the forums and so far some of the solutions have been there (but I dont speak super ubuntu so i dont know how to go about doing those steps)
I use latex for most things if I can, while launguage based articles are not bad, Writing out physics labs can be incredibly long due to all the sub and super scripts, (along with partial differentiators, gradiants laplacians, lagrangian notions ect ect ect ect ) I dont want to write this anymore. I want to work smart not hard. 

My question is: 

How Do I create a style file in latex  (sty file) which i can write all my \newcommand ........  
for all my mathmatical notions,
name that file (ie shortcuts)

 and instead of writing them every time in the preamble of the latex file, simply write

/usepackage{Shortcuts}

I have googled and searched around with a few "tutorials"  but none seem to work. other then tellimg me to write 
```
sudo mkdir /latex/tex/latexy/Maortex file/another sub file/instert extra useless subfile here/ FOO 
```

and then repeating that with cp infront of it again. (why does everyone have a FOO file? does everyone have some long standing mental appreciation to the Foo fighters? )

I see some tutorials calling on MiKTeX (I cant seem to find it in the software center or along those lines) 
others say just save it as a file and load it. (assuming that just...works.. like that)

anyways, I would appreciate any help, Im just converting over to ubuntu and im slowly getting used to all of this. trying to learn as much as I can and sometimes it seems like there is a billion things being tossed at me all at once.

---

### Post by entropy1 on 2013-03-13
If you are running ubuntu, you first need to install a LaTeX system such as texlive (MikTeX is only for Windows); you can install texlive from synaptic or Ubuntu Software Center.  You will also probably want to install texmaker or texstudio to edit and compile latex files.  I prefer TeXstudio.

The next thing you need to do is open a terminal and give the following commands:
```
cd ~
mkdir -p ~/texmf/tex
sudo texhash ~/texmf
```

Now, in the ~/texmf/tex directory is where you should put your shortcuts.sty file, and LaTeX will be able to find it no matter what directory your .tex file is in.

---

### Post by Physics Eskimo on 2013-03-14
Appreciate the help, I have Texlive Full (installed from command line) and both Tex works, and Texmaker (I like Tex works for the quick and dirty stuff)
I have the file's put in and text hashed them. 

Appreciate the Help, Now my only step left is to create the sty file and shove it all in. thanks

PS it works great, thank you very much :)

---

