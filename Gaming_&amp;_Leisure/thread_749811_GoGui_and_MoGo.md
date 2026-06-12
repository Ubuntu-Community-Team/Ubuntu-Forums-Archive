---
title: "GoGui and MoGo"
date: 2008-04-08
forum: Gaming &amp; Leisure
---

### Post by mivo on 2008-04-08
I had been trying to get GoGui and MoGo to work in Ubuntu for a while. The documentation of GoGui really didn't apply to Ubuntu (just running install.sh will not do), so now that I got this to work, I wanted to post a note in case someone else encounters the same trouble (and so that I will find it later when/if I reinstall ;)).

GoGui can be found at [http://gogui.sourceforge.net/]("http://gogui.sourceforge.net/"). Download the version of your choice and unzip the contents to a place in your home directory. In the shell, navigate to the GoGui folder and type:

```

sudo bash ./install.sh -p /usr/local -j /usr/lib/jvm/java-6-sun

```

If you use Java 7, just change the number accordingly. If you don't have Java, grab it from the repository. A few moments later the installation is complete and you'll have a GoGui entry in your *Applications -> Games* menu.

The next step is to download MoGu, the probably strongest go engine currently. The site is located at [http://www.lri.fr/~gelly/MoGo.htm]("http://www.lri.fr/~gelly/MoGo.htm"). There are different Linux versions available -- pick the one that sounds best to you, then untar the contents to a location of your choice. I put the three files into a MoGo folder in my home directory.

In GoGui, go to *Program -> New Program*, click on the program path button and select the mogo executable. Add the desired parameters to the line, i.e. --19 --totalTime 1800 for a game on a 19x19 board with a total time of 30 minutes. It should look similar to this:

```

/home/username/programs/MoGo_release3_big64/mogo --19 --totalTime 1800

```

Change the "working directory" to where the executable is located at. Confirm and you're done. Make sure MoGo is the "attached engine".

That's all you need to do. :) You can additionally use GnuGo as well (it's in the repository), in which case the new program line should read *gnugo --mode gtp* (the working directory can be left blank). It is not possible to let both engines play against each other, but you can choose the one you wish to be your opponent.

---

### Post by mivo on 2008-06-06
Quick note: This still works with Hardy (8.04), too. I had originally written the instructions for 7.10, but they also apply to Ubuntu's current version. :)

---

### Post by mivo on 2009-12-06
Update: Just verified that the instructions are still valid for 9.06 and 9.10. :) GoGui has really matured over the past two years and makes a good frontend for a number of engines (MoGo, GnuGo, Fuego, AmiGoGTP and others). It's also a solid SGF editor.

---

