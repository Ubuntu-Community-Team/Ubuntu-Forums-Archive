---
title: "newbie looking for good college level math program"
date: 2009-03-15
forum: Education &amp; Science
---

### Post by bigbrute123 on 2009-03-15
i am completely new to ubuntu and am looking for any math teaching software i can find.i am currently in pre calculus. is there any software programs that are compatible with ubuntu weather there free or not.thanks

---

### Post by xadder on 2009-03-16
Many options, e.g. geogebra, pylab, wxMaxima, texmacs, octave, ....!

---

### Post by s|fr on 2009-03-22
wxMaxima is great. I've used it only a few times but its really easy to use and at the same time v. powerful.

---

### Post by battlesound on 2009-03-23
**maxima** is very powerful and quick and simple in the terminal.  I mainly use maxima in the command line.  It's quick and simple.  It doesn't take long to go through learning the setup for equations, solving, plotting, differentiating, integrating, etc.  I used it a ton in school where Maple was the standard.

Check the help pages and turorials:
[http://maxima.sourceforge.net/documentation.html]("http://maxima.sourceforge.net/documentation.html")
[http://beshenov.ru/maxima/faq.html]("http://beshenov.ru/maxima/faq.html")


you probably want to install the latest version from source because it's old in the synaptic package manager.

download page: [http://sourceforge.net/project/showfiles.php?group_id=4933&package_id=302886]("http://sourceforge.net/project/showfiles.php?group_id=4933&package_id=302886")
It's still a bit tricky getting it to install.  Install the dependencies you need.  I had to use ```
sudo make install
``` because ```
sudo checkinstall
``` had problems.  help installing: [https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

**wxmaxima** is comparable to maple, but you'll have to get used to the format.  It's also a bit harder to get it installed with the newer version.  I've had problems getting wxmaxima setup again with the latest version.  Get that done and it'd be even better as you'd have a nice maple-like display using maxima.  Good luck.  I may take time to figure that out.  Here's help: [https://help.ubuntu.com/community/wxMaxima]("https://help.ubuntu.com/community/wxMaxima")

check this also for maxima symbolic setup and a quick tutorial:
[http://www.hippasus.com/resources/symmath/maximasym.html]("http://www.hippasus.com/resources/symmath/maximasym.html")

---

