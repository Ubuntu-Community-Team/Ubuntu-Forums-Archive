---
title: "scilab and octave help required"
date: 2006-06-01
forum: Education &amp; Science
---

### Post by u04f061 on 2006-06-01
i am a matlab user and recently singly booted my pc by formatting xp.so i need some alternative to matlab,like octave and scilab.

i have installed orcave and scilab.orcave is fine except when i open
man orcave ,then i can't close it,rather i have to close terminal.this is actually not a problem with orcave but with me in using ubuntu.

the real problem is with orcave.i don't know exactly in which language it is displaying its command line commands.i can't read what i have written on command window of scilab.however when i type commands of matlab for plotting,i get the required result.but what to do with font or language in which it displays alphabets?
  i am attatching a screenshot of my scilab

 



i googled through scilab  and found that xmllab combined with octave is useful for many purpose and provides excellent gui tools much similar to matlab.
but it is not available in apt-get. to use it it requires scilab 4.0 and apt  provides 3.2.i tried to download octave ,it was in tar.gz which is format blocked by our proxy server. how to overcome this?
can't i get one from apt?

---

### Post by Sutekh on 2006-06-02
[quote=u04f061]
i have installed orcave and scilab.orcave is fine except when i open
man orcave ,then i can't close it,rather i have to close terminal.this is actually not a problem with orcave but with me in using ubuntu.[/quote] To quit a man page, use the 'q' button.
[quote=u04f061]
the real problem is with orcave.i don't know exactly in which language it is displaying its command line commands.[/quote] Octave uses very similar commands to MATLAB.  When I was at Uni, we used to use MATLAB in engineering, and Octave on UNIX machines in maths.  I found them to be quite similar.

Arrays and matrices are entered exactly the same, and operations on them are the same. Even functions follow the same format, and alot of commands are similar.

You should probably start with the [Octave Online Manual]("http://www.gnu.org/software/octave/doc/interpreter/") for more help.

You might also want to install [GNUPlot]("http://www.gnuplot.info/"), which is also available in the universe repository (where you should have gotten Octave)

I don't know much about xmllab, sorry.

---

### Post by ekravche on 2006-11-17
Looks like a good application

---

### Post by slimdog360 on 2006-11-17
make sure you install the octave-forge package also. Personally I just write everything in a text file, open and run it using koctave. Koctave for me is almost useless except for providing an easy way to run files. If you want a matlab clone use octave as scilab uses some different commands. Octave is much more matlab compatible.

```
sudo apt-get install octave-forge gnuplot koctave
```

---

