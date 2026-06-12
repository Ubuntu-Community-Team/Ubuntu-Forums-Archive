---
title: "Matlab freezes"
date: 2008-02-07
forum: Education &amp; Science
---

### Post by domherre on 2008-02-07
To get away with matlab gui being only grey windows under compiz I changed /usr/local/bin matlab 
#!/bin/sh
export AWT_TOOLKIT=MToolkit

Now matlab loads up fine and works.. for a while. Until i try something like
doc ones, the documentation window pops up, I close it and now I cant type anything in the program? Am I missing something really simple here?

---

### Post by Trurl on 2008-02-10
I'm getting the same problem. The java fix works to display but whenever anything else is opened (figures, m-files, etc.) I lose the ability to type....

Edit: thought there was another problem, but didn't realize ctrl-Y is the new ctrl-V

---

### Post by domherre on 2008-02-11
I got it working when I used the other workaround presented in some threads.

That is editing /usr/local/bin/matlab to

#!/bin/sh
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/
... etc

---

### Post by StevoSn on 2009-10-19
it seems like this also worked for me, even though it's the same JRE version that I am pointing to now...

---

