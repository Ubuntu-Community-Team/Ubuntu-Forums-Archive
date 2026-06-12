---
title: "Error Codes Collection"
date: 2006-04-27
forum: Desktop Environments
---

### Post by ububaba on 2006-04-27
I have tried but could not find it. Is there a collection of all **error codes** at some place, 
from where one can get clear-cut [COLOR="Teal"]instructions/suggestions[/COLOR] about solving those problems?
I believe, it can save a lot of bother, if someone who masters the situation, kindly
volunteers to do that. Thanking in anticipation.:mrgreen:

---

### Post by jazzmuzik on 2006-04-27
Linux is made of a collection of programs. The kernal being the core of the OS. Each program, including the kernal, can have a bunch of error codes and there are thousands of programs. Multiply those two together and you get so many error codes your head would spin. To make things manageable, which program's error codes are interested in?

Sometimes what looks like an error is just a warning and not really a problem. Sometimes you get a ton of output when you install a program, but it's not really an error or a warning, more of a verbose way of telling you what's happening.

---

### Post by ububaba on 2006-04-27
[QUOTE=jazzmuzik]Linux is made of a collection of programs. The kernal being the core of the OS. Each program, including the kernal, can have a bunch of error codes and there are thousands of programs. Multiply those two together and you get so many error codes your head would spin. To make things manageable, which program's error codes are interested in?

Sometimes what looks like an error is just a warning and not really a problem. Sometimes you get a ton of output when you install a program, but it's not really an error, more of a verbose way of telling you what's happening.[/QUOTE]
I fully agree, that the total volume of error messages could be enormous, and would be 
a Herculean task to deal with each of them in a master collection.  However, the touch of
fatalism is sligthly annoying.  Once one gets an error message, one would obviously like 
to solve it or get rid of the irritant.  It is hardly comforting to know that one may not be able 
to deal with it and best bet is to ignore.  For me the very essence of this forum is to better
the programmmes, i.e. to lessen the number of errors, with every passing day.  Perfection 
could be impossible to achieve, but at least one could keep on going in that direction.

Was trying to install **libbz2-1.0** and got this: [COLOR="RoyalBlue"]
All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

---

### Post by jazzmuzik on 2006-04-27
Good point. Learning to overcome errors is a very good thing. I just want to say that you can't worry about everything. You'll go crazy. It's strange that for computers to work they need to be error free, but achieving that 100% is difficult if not impossible. At some point you just have to let go and do the best you can do in order to preserve your sanity.

In your example installation errors are something that bother me. It's important that things go right during an install. I don't know the specific answer to this problem, but generally when you install programs with dpkg (or apt-get) sometimes scripts are executed before and/or after the actual program is installed. In your case the post-installation script returned an error of some kind. Exit status '1' looks like a general error. At least it gives the program/package that had the problem: msttcorefonts (microsoft truetype core fonts).

Hmm. My thought is an error with a font package is probably not all that serious. If I wanted to find out more I'd start searching this forum for a similar question or I'd get on Google and do a search.

Sorry I can't be more help.

---

