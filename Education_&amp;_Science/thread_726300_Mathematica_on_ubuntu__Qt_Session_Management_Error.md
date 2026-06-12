---
title: "Mathematica on ubuntu ::: Qt: Session Management Error"
date: 2008-03-16
forum: Education &amp; Science
---

### Post by steak-sandwich on 2008-03-16
Hey guys,
hopefully someone can help me with this problem.
I installed Mathematica 6 on Ubuntu. During the installation there was no error message at all. 
I switched from Kubuntu to Ubuntu 2 days ago. When I installed Mathematica on Kubuntu everything was fine. But now I get this message when I try to open Mathematica: Qt: Session management error....
Please take a look at the attached screenshot. As you can see, when mathematica opens, it opens 3 windows, 2 of them are meaningless. I can't close them unless I close Mathematica. 
That's really weird since Mathematica worked fine on Kubuntu. 

Thanks,

Ben

---

### Post by amyst on 2008-03-18
Please see the second page of this thread, solution offered by mannheim

[http://ubuntuforums.org/showthread.php?t=590510](http://ubuntuforums.org/showthread.php?t=590510)

In summary, the ghost window is due to a bug in mathematica that makes trouble to Compiz. You can eliminate the ghost window by modify a setting in mathematica: 

In Mathematica, got to Edit->Preferences->Advanced and click on "Open Option Inspector". Under "Notebook Options", select "Window Properties" and change "WindowFrame" to "Generic".

Just a note: you probably would receive a quicker reply if you posted the thread on the right forum, probably General Help :)

---

