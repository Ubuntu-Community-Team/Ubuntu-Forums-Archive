---
title: "Large amount of data"
date: 2009-06-24
forum: Education &amp; Science
---

### Post by beren.olvar on 2009-06-24
My normal workflow is like:
1- create a program
2- run it and get some results
3- realize I need more calculations
4- modify the program
5- get more results
6- goto 3

so, soon enough, I get a lot of folders with a lot of files. I try to manage them using some sort of log file to track down what I have calculated on each folder, but anyway, it becomes very messy after a little usage.

So I am wandering, how do you manage the output of your calculations? have anyone tried using databases? is that too complicated to link with, lets say, C++? Is there any speed loss compared to only write files? What other suggestions could you make?

The kind of data I deal with is, normally, just raw numbers in columns if it makes any difference.

cheers!

---

### Post by InfernalNeutrino on 2009-06-24
Hi,

I'm not sure what kind of analysis, etc. you are doing, but depending on your personal tastes and needs I can speak of 2 ways of getting out of simple ascii columns.

One, which I'm listing 1st because of your reference to c++, would of be ROOT [(clicky)]("http://root.cern.ch/root/"). It might be a bit of a "sledgehammer driving a tack" sort of thing given that it is an entire analysis framework, but you can simply link to some of its libraries regarding its .root file format if you want to use it. This would be what I'm using for my own simulation work which involves generating rather large amounts of data, looking at it, and generating more with some tweaks. It runs pretty fast. It has a so-called "cint" c++ parser that allows one to write macros (basically turning c++ into a scripting language) which you may or may not like. Personally, I like the PyROOT python bindings better for scripting work and simply including the relevant headers when making compiled code. So it's ridiculously powerful, has a learning curve, and might not be what you want, but you might actually like it.

The other way of handling things that I am aware of in my work is [here]("http://www.scipy.org/Topical_Software#head-e50ca22e28dda363142d1a56a186323e76a66fa5"). Now we are in the realm of scipy and its associated stuff. My understanding is that the database stuff you see in there is more along the lines of an actual database, but I haven't actually had time to use it much myself so I can't comment much on it. Might be interesting to look at though. Perhaps others will have ideas that are more "package independent" as it were, but maybe this'll give you some ideas. Cheers!

---

