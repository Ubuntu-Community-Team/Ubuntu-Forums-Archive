---
title: "Running executable"
date: 2005-05-05
forum: Desktop Environments
---

### Post by implicity on 2005-05-05
Hi, All!

After installing Kubuntu, I have downloaded Firefox and then try to install it. But when I click on executable, nothing happens. Then I try to install Eclipse IDE, and have the same problem. Nothing happens when clicking on executable...

Somebody knows why executable files are not running?

---

### Post by wwwolf on 2005-05-05
How did you install it? Did you use Kynaptic? Are you able to call up the commands in the konsole? Are the commands listed in usr/bin ?

More info would be helpfull.  [-X 

HTH,

wwwolf

---

### Post by implicity on 2005-05-05
I just unpack downloaded archive (Firefox) and then click on the executable. Nothing happens... Same procedure was success in Suse. Don't understand why not works in Kubuntu.

---

### Post by johnprgr on 2005-05-05
[QUOTE=implicity]I just unpack downloaded archive (Firefox) and then click on the executable. Nothing happens... Same procedure was success in Suse. Don't understand why not works in Kubuntu.[/QUOTE]
      I can't answer why your having the problem you have.  I agree with you it should work based on the very little information you gave.
     However, a better way to install mozilla-firefox (or really any application in kubuntu) is to use either apt-get or synaptic.  A simple "sudo apt-get install mozilla-firefox" at a konsole prompt will solve your problem as far as running firefox.  I would delete the stuff you downloaded.  That is just my opinion.
     Generaly speaking use synaptic first to attempt an install and then if it doesn't exist in a repository, do a manual install.

     Hope this helps some.

---

### Post by KDE-fan on 2005-05-05
[QUOTE=implicity]Hi, All!

After installing Kubuntu, I have downloaded Firefox and then try to install it. But when I click on executable, nothing happens. Then I try to install Eclipse IDE, and have the same problem. Nothing happens when clicking on executable...

Somebody knows why executable files are not running?[/QUOTE]

You can start executables by writing ./nameofexecutable in the console. You sometimes have to right click the file first and change its properties to "executable".

---

### Post by implicity on 2005-05-06
[QUOTE=johnprgr]I can't answer why your having the problem you have.  I agree with you it should work based on the very little information you gave.
     However, a better way to install mozilla-firefox (or really any application in kubuntu) is to use either apt-get or synaptic.  A simple "sudo apt-get install mozilla-firefox" at a konsole prompt will solve your problem as far as running firefox.  I would delete the stuff you downloaded.  That is just my opinion.
     Generaly speaking use synaptic first to attempt an install and then if it doesn't exist in a repository, do a manual install.

     Hope this helps some.[/QUOTE]
 Thank You, johnprgr, this works!

---

