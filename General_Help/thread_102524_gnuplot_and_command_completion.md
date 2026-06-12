---
title: "gnuplot and command completion"
date: 2005-12-12
forum: General Help
---

### Post by jeremytaylor on 2005-12-12
Hi there, 
I use gnuplot all the time. On the machines in my lab it can complete filenames and commands using the TAB key but on my laptop with breezy it can't. 
how can I turn this feature on?
thanks
Jeremy

---

### Post by jrings on 2006-11-02
Sorry if I ping this, but I have a similar problem and can't figure out where to search for help.
I have gnuplot 4.0, and tab completion of file names works fine. I have also installed gnuplot-4.2 for testing and no tab completion there.
Anyone knowing how tab completion in gnuplot is done, or why it wouldn't work?

---

### Post by Rui Pais on 2006-12-26
hi,
i was searching the net for a answer to this one too...

regrettably i find [this one]("http://ubuntuforums.org/showthread.php?p=1553021#post1601356") ([post #8]("http://ubuntuforums.org/showpost.php?p=1601356&postcount=8")), that i'm presume is correct :(

---

### Post by Dyqik on 2007-03-13
You could install gnuplot yourself, manually, with readline enabled.

Assuming you already have various compilers,
Uninstall gnuplot, gnuplot-x11, gnuplot-nox
Install build-essentials, readline5-dev and texinfo using apt (or your favourite frontend).  
Then download gnuplot 4.2 from [www.gnuplot.info]("http://www.gnuplot.info/"), untar it, change into the new gnuplot-4.2.0 directory and run
```
./configure --prefix=/usr
make
sudo su
make install
```

The --prefix=/usr option to configure makes sure that gnuplot gets installed in the same place as the ubuntu package puts it.  For some reason the default /usr/local/bin doesn't work for me on edgy.

Since we're not going to distribute the package, this is all legal.

---

### Post by Rui Pais on 2007-03-13
Hi, Dyqik, thanks for your suggestion.

Regrettably i have already tried that option, with several different options on autocompletion at ./configure but none with success :(


I ended doing my commands on text files and call them with the gnuplot command and it works quiet satisfactorily (at least i can reuse my plots code).

Anyway, i will try again at edgy (i tried at dapper) and with the new 4.2 to see if i can make it work.

---

### Post by Rui Pais on 2007-03-13
Hey, the new 4.2 with your suggestion ./configure --prefix=/usr work out beautifully :)
If anyone want to try, it should work at least on edgy.

Btw, checkinstall work correctly with this gnuplot, so it's better to use then make install (since it produce a manageable deb package).

Many thanks.

Rui.

---

### Post by jeremytaylor on 2007-03-13
My frustration with gnuplot led me to switch to python and matplotlib. Worth looking at. Pretty much as simple to use as gnuplot, even if you don't know python, and the plots are much much higher quality.
jeremy

---

### Post by tyusoff on 2007-03-27
> **Dyqik said:**
> You could install gnuplot yourself, manually, with readline enabled.

Assuming you already have various compilers,
Uninstall gnuplot, gnuplot-x11, gnuplot-nox
Install build-essentials, readline5-dev and texinfo using apt (or your favourite frontend).  
Then download gnuplot 4.2 from [www.gnuplot.info]("http://www.gnuplot.info/"), untar it, change into the new gnuplot-4.2.0 directory and run
```
./configure --prefix=/usr
make
sudo su
make install
```

The --prefix=/usr option to configure makes sure that gnuplot gets installed in the same place as the ubuntu package puts it.  For some reason the default /usr/local/bin doesn't work for me on edgy.

Since we're not going to distribute the package, this is all legal.

Hi, I tried this method and successfully installed and come with TAB completion. However, X11, jpeg and png terminal were not installed and I could not plot any graph unless using postscript. I checked output during configure and X libraries, libgd are not available. Is there anyway to solve this? I dont know what libraries are needed for the gnuplot terminals.

Thanks

---

### Post by hubin on 2007-04-03
Hi, I had the same problem in gnuplot and found the following message:

[http://groups.google.com/group/comp.graphics.apps.gnuplot/browse_thread/thread/bbb9a00b75f3d03d/6cc9084b9accc20a?lnk=gst&q=autocomplete&rnum=1#6cc9084b9accc20a](http://groups.google.com/group/comp.graphics.apps.gnuplot/browse_thread/thread/bbb9a00b75f3d03d/6cc9084b9accc20a?lnk=gst&q=autocomplete&rnum=1#6cc9084b9accc20a)

Basically the tab-completion function loss was caused by not using the gnu readline library. One shall compile gnuplot with the option   ./configure --with-readlin=gnu to enable the function. I hope this helps.

---

### Post by tyusoff on 2007-08-29
finally ...I found a way to solve this issue ... the easy way... 

[http://telin.ugent.be/~slippens/drupal/node/158](http://telin.ugent.be/~slippens/drupal/node/158)

oh..dont forget to use "filename" instead of 'filename' as ' wont work...

cheers

---

### Post by Rui Pais on 2007-08-29
> **tyusoff said:**
> finally ...I found a way to solve this issue ... the easy way... 

[http://telin.ugent.be/~slippens/drupal/node/158](http://telin.ugent.be/~slippens/drupal/node/158)

oh..dont forget to use "filename" instead of 'filename' as ' wont work...

cheers

hip hip urraiii!!

Many thanks. That really works!
Besides tab completion, that make the keys delete/end/home work (instead of produce annoying characters...) 
Great!.

A tip for those without practice with alias. You can edit your ~/.bashrc file and add a line with:
```
alias gnuplot='rlwrap -a -c gnuplot' 
```
 to make it work automatically with gnuplot command :)

Again, thanks.

---

### Post by tyusoff on 2007-08-29
> **Rui Pais said:**
> hip hip urraiii!!

Many thanks. That really works!
Besides tab completion, that make the keys delete/end/home work (instead of produce annoying characters...) 
Great!.

A tip for those without practice with alias. You can edit your ~/.bashrc file and add a line with:
```
alias gnuplot='rlwrap -a -c gnuplot' 
```
 to make it work automatically with gnuplot command :)

Again, thanks.

Great :)... however, what does delete/end/home do in gnuplot?? :confused: seems that i dont know much yet about gnuplot

---

### Post by Rui Pais on 2007-08-29
> **tyusoff said:**
> Great :)... however, what does delete/end/home do in gnuplot?? :confused: seems that i dont know much yet about gnuplot

i mean the keys on keyboard, not keywords :) 
They delete the next character, go to the end or begin of line. 
Very useful if one is a little dyslexic typing (like me) or edit long line commands. 
Up and down keys bring history entries so one can edit them to see different parts of graphs, different scales, different rotations or colors, etc.  

Without readline or your excellent tip: those keys don't work and produce this:
home -> stays on the same position, writes OH
end ->                        same, writes OF
delete ->   do not delete and writes 3~  

so if type:
[FONT="Courier New"]pplot 'my_wonder_super_graph.dat'[/FONT]
you have to go back char by char to begin of line (no home working) and use only backspace to delete the wrong extra "p". Or if habit make you use the delete key you get:
[FONT="Courier New"]3~pplot 'my_wonder_super_graph.dat' [/FONT]
and have to go back again and delete 3 chars :(

---

### Post by tyusoff on 2007-08-29
oh ..thats great :D at least it will help me a lot when using gnuplot ....thanks again ..

---

### Post by Rui Pais on 2007-08-29
> **tyusoff said:**
> oh ..thats great :D at least it will help me a lot when using gnuplot ....thanks again ..

Well, the better way of working with gnuplot is to work with a plain text editor (with all comforts of editing and even autocompletion or color syntax) and run the file with the commands from a console, like: **gnuplot mywork.gnp** (extension could be anything).

Even with your excellent tip, working directly from gnuplot line command could be very hard and if one forget to save at the end of session you will need to retype all again (history, of course, did not persist among gnuplot sessions). 
It's practical to visualize a plot or a function, but behind that is a pain.

I use geany (on repos) it's good and light and have an internal terminal that allow to run gnuplot from there while editing. 
Scite is another good choice. 

A fundamental help site is the:
[Gnuplot - Not so Frequently Asked Questions]("http://t16web.lanl.gov/Kawano/gnuplot/index-e.html")

good luck with your gnuplot learnig and again thanks for sharing your solution
:)

---

### Post by nue-- on 2008-05-15
Some people might want to be able to complete single quoted files too. The problem is that the single quote is not in the default list of break chars, which can easily be circumvented with the rlwrap -b option:

```

 alias gnuplot="rlwrap -a -c -b"\"\'" gnuplot"

```

or, in .bash_aliases / .bashrc,

```

alias gnuplot="rlwrap -a -c -b\"\\\"\\\"\\\'\\\'\" gnuplot"   

```

Notice that then, you have ONLY " and ' (and space) as triggers for completion (which is fin for gnuplot imo).

---

