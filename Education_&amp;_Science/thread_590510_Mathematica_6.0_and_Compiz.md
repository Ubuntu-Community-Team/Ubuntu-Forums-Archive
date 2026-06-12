---
title: "Mathematica 6.0 and Compiz"
date: 2007-10-24
forum: Education &amp; Science
---

### Post by Gagle on 2007-10-24
I've bought and installed successfully the new version of mathematica 6 on a fresh install of Gutsy Gibbon running Compiz-Fusion with a Nvidia graphics card.

When I start mathematica, a couple of extra blank windows that cannot be dealt with  pop-up .  I've searched this forum, wolfram's and googled for a fix, but no one found a work-around.

Other issues were mentionned and fixed, for example the splashscreen or the keyboard problems.

My question is this :  
Is what is happening to me a known bug that remains un-fixed or did I forget a crucial install step that deals specifically with Ubuntu ?

regards,

Gagle

---

### Post by ravenon on 2007-10-24
I experience the same thing when running compiz and Mathematica 6. Don't know a solution except to turn off compiz.

I have had similar problems with other apps and fixes eventually make it in.

---

### Post by parktownprawn on 2007-10-30
Also have this problem with an ATI card and compiz.

It seems be a known bug with no known fix other than turning off compiz:

[http://forums.wolfram.com/mathgroup/archive/2007/May/msg01501.html](http://forums.wolfram.com/mathgroup/archive/2007/May/msg01501.html)

---

### Post by PoorLeno on 2007-11-04
I have the same problem. Is there a way to disable compiz temporarily with a script, that launches mathematica and restores compiz when it's done? I'm rather fond of both apps, I don't want to switch constantly...

---

### Post by IgnatiusReilly on 2007-11-04
I have exactly the same problem and the suggested script would be the right solution for me.
Moreover, I am really a newbie and I don' even know which is the command to disable Compiz.
Can anyone help us?

Thanks a lot

---

### Post by Loreleye on 2007-11-05
Hello!
I'm about to install Mathematica 6 at home (my school gave us a free student version). I'm hesitating between installing it on Kubuntu or on Windows (XP).
Is it easy to install on Kubuntu? Does it work well? Is there a lot to fix before use?
Thank you for your help! I'm not very good with computers! (my father will install the software)

Bye!

---

### Post by IgnatiusReilly on 2007-11-05
> **Loreleye said:**
> 
I'm about to install Mathematica 6 at home (my school gave us a free student version). I'm hesitating between installing it on Kubuntu or on Windows (XP).
Is it easy to install on Kubuntu? Does it work well? Is there a lot to fix before use?
Thank you for your help! I'm not very good with computers! (my father will install the software)


It is really simple and, apart from the problem with Compiz (but I think you don't have Compiz if you use Kubuntu), it seems to work well.

To install it you must copy the whole CD in a directory, move to the directory where the file MathInstaller is now located, write in the terminal:

```
sudo ./MathInstaller
```

and answer the questions the program asks you. That's all.

Bye

---

### Post by Loreleye on 2007-11-05
Thank you very much ! I'm going to try it and we'll see. I hope I'll be happy with it!

---

### Post by tielie on 2007-11-05
The problem is probadly related to the old crapy Motif Toolkit.

Someone should patch the shity Motif to fix this issues. (Infact Motif sucks alot the fonts looks like hell)

IMHO Wolfram should KILL motif and start write an GUI mathfrontend based on QT or GTK+

---

### Post by argie on 2007-11-07
> **PoorLeno said:**
> I have the same problem. Is there a way to disable compiz temporarily with a script, that launches mathematica and restores compiz when it's done? I'm rather fond of both apps, I don't want to switch constantly...

That should be rather easy to manage. Try this:
```

#!/bin/bash

metacity --replace &
(**pi 400000**; 
compiz --replace)

```
Replace that thing in bold with the command to start Mathematica (currently it switches back after pi is calculated to 400,000 places). That seems to pull all your windows to the current workspace though, unfortunately.

---

### Post by IgnatiusReilly on 2007-11-07
It works. Thanks a lot.

Another issue. Using the default StandardForm for the output cells when 3 and g are index they are displayed by Mathematica 6 as 9.

So, for instance, x^3 looks like x^9. I fixed the problem changing the format type of output cells from StandardForm to TraditionalForm.

Have you experienced the same problem?

---

### Post by marius311 on 2007-12-03
Yeah I've definitley noticed this problem too, along with the fact that the back/forward buttons and search bar do not work under Help. 

Anyway, a quick fix is this: When Mathematica boots, X out of both the ghost windows (this has no immediate effect). Now type the first few letters of some command (e.g. "Int") and hit Ctrl+K to autocomplete. The popup menu with options should appear, and the ghost windows should be gone.

---

### Post by mannheim on 2007-12-04
> **marius311 said:**
> Anyway, a quick fix is this: When Mathematica boots, X out of both the ghost windows (this has no immediate effect). Now type the first few letters of some command (e.g. "Int") and hit Ctrl+K to autocomplete. The popup menu with options should appear, and the ghost windows should be gone.

An alternative way to get rid of the two "extra" windows is to exploit the fact that both these windows have a menu-bar: the menu items are not drawn, but it does respond to mouse-clicks. So click on each of these windows where the "File" menu should be. The File menu appears. Select "Close" from the File menu, and the window does indeed close.

I wish this could be fixed.

---

### Post by mannheim on 2008-01-15
A much better fix is described in the [launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153045") on this. In Mathematica, got to Edit->Preferences->Advanced and click on "Open Option Inspector". Under "Notebook Options", select "Window Properties" and change "WindowFrame" to "Generic".

This works for me, and I haven't noticed any side effects.

---

### Post by dmonkey on 2008-01-16
> **mannheim said:**
> A much better fix is described in the [launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153045") on this. In Mathematica, got to Edit->Preferences->Advanced and click on "Open Option Inspector". Under "Notebook Options", select "Window Properties" and change "WindowFrame" to "Generic".

This works for me, and I haven't noticed any side effects.

Yep, works for me too. An absolute life saver!!

---

### Post by jdeslip on 2008-01-27
Thanks for this solution.  It is fantastic!

---

### Post by BryanFRitt on 2008-02-08
> **mannheim said:**
> A much better fix is described in the [launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153045") on this. In Mathematica, got to Edit->Preferences->Advanced and click on "Open Option Inspector". Under "Notebook Options", select "Window Properties" and change "WindowFrame" to "Generic".

This works for me, and I haven't noticed any side effects.

This work for me, Thanks...
The windows still pop up briefly though, but no biggie.
However; some of the palettes don't seam to work properly.
The Algebraic will type in what it's supposed to then it will delete what it just put down.
(don't know if this problem existed before this fix)

---

### Post by mannheim on 2008-02-15
> **BryanFRitt said:**
> .
The Algebraic will type in what it's supposed to then it will delete what it just put down.

I hadn't come across this bug before; but yes, it happens to me too, now that I try it. On the other hand, it seems to occur whether or not I apply the "fix" for the two extra windows. So it doesn't seem to be related.

---

### Post by pip_134 on 2008-02-15
Hey guys,
I'm trying to installer Mathematica on Gusty but I've run into a problem:

I've copied the files across from the CD and gone to the /Unix/Installer folder but when I run
```
 sudo ./MathInstaller 
```
I get the reply
sudo: ./MathInstaller: command not found
But a quick dir shows the file is there.

Any ideas would be greatly appreciated!

---

### Post by pip_134 on 2008-02-15
Solved my earlier problem:
In the GUI File Browser I clicked on the properties of the MathInstaller. Under Permissions there's an option "Execute: Allow executing file as program" select that then follow the normal instructions and the install will go through fine.

---

### Post by ndb82 on 2008-03-25
> **tielie said:**
> The problem is probadly related to the old crapy Motif Toolkit.

Someone should patch the shity Motif to fix this issues. (Infact Motif sucks alot the fonts looks like hell)

IMHO Wolfram should KILL motif and start write an GUI mathfrontend based on QT or GTK+

They got rid of Motif for version 6.  The use QT now.



The documentation "search" bug can be worked-around by turning on/off numlock (forgot which).  I just updated to 6.0.2 and this bug seems to be gone anyway.

---

### Post by binnaeus on 2008-04-11
> **mannheim said:**
> A much better fix is described in the [launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153045") on this. In Mathematica, got to Edit->Preferences->Advanced and click on "Open Option Inspector". Under "Notebook Options", select "Window Properties" and change "WindowFrame" to "Generic".

This works for me, and I haven't noticed any side effects.

That worked for me too! Thank you very much :)

---

