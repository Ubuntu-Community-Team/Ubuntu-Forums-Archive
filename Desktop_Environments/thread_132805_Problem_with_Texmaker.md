---
title: "Problem with Texmaker"
date: 2006-02-13
forum: Desktop Environments
---

### Post by neoflight on 2006-02-13
[QUOTE=dada1958]I'll stick to Gnome with my Compaq Deskpro EN PIII @ 1 GHz, with only 256 MB on RAM it works surprisingly well, playing with TeXMaker and TeXLive ...[/QUOTE]


Hi
Since you have already set up texmaker and texlive... i think you could solve a problem i am having with texmaker.

I have installed everything from texmaker to texlive succesfully. I can run latex commands (almost all; latex, dvips....etc all of them) from the command line or using gedit os anyother editor for that matter EXCEPT texmaker!!!

I have set up the commands from the texmaker config menu. But all i am getting is "log file not found" ... when i run the same tex file from  the shell using latex command it creates all the files needed without any latex errors. i mean i have .log, .dvi, etc in the same folder. 

I tried different ways of putting the commands in the texmaker configuration as shown in its own help such as putting the entire latex path in the command. eg 

/usr/local/texlive/2005/bin/i386-linux/latex %.tex 
[error...a message comes saying "process started" in the bottom message window...then it changes to "Error : could not start the command"]
and
/usr/local/texlive/2005/bin/i386-linux/latex -interaction=nonstopmode %.tex
[same error as above..]
and
latex -interaction=nonstopmode %.tex [error- "log file not found"]
and simply
latex %.tex 
[error "log file not found"]
[-( 
note: once i have the log file in the folder from a command line latex run texmaker runs...but none of the other commands work (the command icons)...but why is texmaker not making log file? why is anyother commands not working?

whats happening here? i have all the PATH variables set etc..
any help would be appreciated...thanks

---

### Post by dada1958 on 2006-02-18
[QUOTE=neoflight]Hi
Since you have already set up texmaker and texlive... i think you could solve a problem i am having with texmaker. etc[/QUOTE]

I'm reading this 4 days later...

TeXMaker does behave strange on my Ubuntu PC now and then though I have to say I'm working with pdfLaTeX which does the job pretty well, the path is entered in the configuration. Previewing is another story, no problems with the default setting but I get that 'Error : could not start the command' when I enter the path to Xpdf in the configuration.

I just did a test file with LaTeX which didn't run at all, with or without path; it just doesn't work. With TeXMaker for the Mac I can do LaTeX and pdfLaTeX runs without further configuration. I can preview the pdf whithout a glitch. I have to typeset the tex file with TeXShop again to see the dvi.

I think I'm going to send the author of TeXMaker a link to this topic one of these days :-)

[edit]
After a reboot I was able to do a LaTeX run with TeXMaker un my Ubuntu PC, strange...

This is the path:
/usr/local/texlive/2005/bin/i386-linux/latex -interaction=nonstopmode %.tex

The same as yours as I can remember.

I had to alter the path to de DVI viewer a little bit:
usr/local/texlive/2005/bin/i386-linux/xdvi-xaw.bin %.dvi
[/edit]

---

### Post by teet on 2006-02-18
I had the same log file error message.

I finally found out that I needed to manually enter in a file extension whenever I saved my file.  So if I opened a new document in texmaker, and then went to "save as", I have to name it something like "test.tex"  if you don't put the .tex part in it will give a log error!  Hope this helps.

As a side note:  I'm using tetex and the tetex-extras from the repositories, the newest texmaker downloaded from the author's website (it's incredibly easy to install), and acroread (i.e. adobe acrobat) as my pdf viewer.

-teet

---

### Post by dada1958 on 2006-02-19
I use Xpdf as previewer when I'm working with TeXMaker because it has the advantage of refreshing the content by hitting 'r' after another LaTeX run. The rendering is quite good, better than Evince and it's faster than Acroread.

---

### Post by neoflight on 2006-02-20
thanks guys for the help.

actually i managed to solve the problem and the frustration was at it height. then decided to share my experience with that how to. 


dada has provided a very nice explanation on installing latest pdftex. 
texmaker is incredibly light and nice. 

i would suggest (as of now) on the look if it is to have the margin size reduced to get much more view in the editor,

and, automatic inclusion of the file extension .tex when you save. i believe kile does that.

it would be nice to have lots of inputs from users of texlive/tetex/texmaker on the [howto]("http://www.ubuntuforums.org/showthread.php?t=131507") to  all of us to set-up an excellent latex env.

thanks a bunch.

---

### Post by zojas on 2006-02-22
[QUOTE=dada1958]I use Xpdf as previewer when I'm working with TeXMaker because it has the advantage of refreshing the content by hitting 'r' after another LaTeX run. [/QUOTE]

I totally love xpdf, but the ubuntu version refuses to show me the table of contents! any idea why?

---

