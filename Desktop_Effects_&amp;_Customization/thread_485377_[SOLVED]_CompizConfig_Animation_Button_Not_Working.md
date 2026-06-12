---
title: "[SOLVED] CompizConfig Animation Button Not Working"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by ReverendJ1 on 2007-06-26
I got Compiz-Fusion working with only one problem. I didn't have titlebars for any windows, then I installed emerald and everything worked fine. For a while. When I was playing around with all my sweet new effects (and I do mean sweet) I started playing around with the animations for minimizing and unminimizing windows. For some reason now I can't get into the animations config. Whenever I try to push the animations button it gets rid of all the icons in CompizConig and won't open up the animations config. Not a big deal, but I was wondering if anyone else had this problem, or new of a way to change the animations from the command line.

---

### Post by bolderbast on 2007-06-27
I have the same problem here. When I run ccsm from the command line, I get the following message:

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 2156, in SelectPlugin
    pluginClass = PluginClass(select, self)
  File "/usr/bin/ccsm", line 1557, in __init__
    groupPage = GroupPage(name, group)
  File "/usr/bin/ccsm", line 1045, in __init__
    sga = SubGroupArea(subGroup, group[subGroup], filter)
  File "/usr/bin/ccsm", line 1001, in __init__
    set.Read()
  File "/usr/bin/ccsm", line 199, in Read
    self._Read()
  File "/usr/bin/ccsm", line 814, in _Read
    self.Checks[setVal-self.minVal][1].set_active(True)
IndexError: list index out of range

---

### Post by ReverendJ1 on 2007-06-27
I decided to post a bug on bugzilla for this so the developer will know. You can find it here:
 [ http://bugs.opencompositing.org/show_bug.cgi?id=91]("http://bugs.opencompositing.org/show_bug.cgi?id=91")

---

### Post by bolderbast on 2007-06-27
Nice! Didn't get around to it yet!

---

### Post by dwebb86 on 2007-07-02
I have the same EXACT problem. Has anyone solved or responded to this yet?

---

### Post by pingpongboss on 2007-07-02
weird! my animations button works, but my Snapping Windows button gets rid of all the icons.

---

### Post by ReverendJ1 on 2007-07-02
Hmmm. There have been updates like every other day to Compiz-Fusion. Hopefully they will get this fixed soon. Although I still haven't heard anything from my bug post. :(

---

### Post by bolderbast on 2007-07-02
A couple of updates further, I now get this when I click the "Animations" button:

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 2519, in ShowPlugin
    pluginClass = PluginClass(select, self)
  File "/usr/bin/ccsm", line 1627, in __init__
    groupPage = GroupPage(name, group)
  File "/usr/bin/ccsm", line 1097, in __init__
    sga = SubGroupArea(subGroup, group[subGroup], filter)
  File "/usr/bin/ccsm", line 1053, in __init__
    set.Read()
  File "/usr/bin/ccsm", line 242, in Read
    self._Read()
  File "/usr/bin/ccsm", line 857, in _Read
    self.Checks[setVal-self.minVal][1].set_active(True)
IndexError: list index out of range
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 63, in UpdateVisibleSettings
    settingWidget.Read()
  File "/usr/bin/ccsm", line 242, in Read
    self._Read()
  File "/usr/bin/ccsm", line 857, in _Read
    self.Checks[setVal-self.minVal][1].set_active(True)
IndexError: list index out of range

---

### Post by dwebb86 on 2007-07-04
bumping thread to see if anyone has solved this yet, it's annoying the hell out of me, my animations are insanely slow and I can't go into that config to speed them up.

---

### Post by edwin.e.johnson on 2007-07-07
i found that if your in ccsm and go to "advanced search" you can reset all of your animation plugins to default except one..... seems to be the source of the problem <close animation> when its set to random.. 

someone please if you have a fit to this problem post it here....

ooh and they have the 3d window plugin now just synaptic search for compiz and install the unsupported plugins for fusion they got some cool sh*t.. it will show up in ccsm

---

### Post by bolderbast on 2007-07-07
The bug, [http://bugs.opencompositing.org/show_bug.cgi?id=91](http://bugs.opencompositing.org/show_bug.cgi?id=91) is fixed now in git. Should be in the repos soon... :)

---

### Post by bolderbast on 2007-07-08
just got the latest update from Treviño's repository. Problem fixed. :)

---

### Post by marsmissionaries on 2007-07-08
I would also like to add that reinstalling the libraries for CompizConfig fixes this issue as well. (i had to do this a week ago)

---

### Post by pingpongboss on 2007-07-08
still not working for me :T

---

### Post by ReverendJ1 on 2007-07-09
@pingpongboss - Hmm. You didn't say, but you did get the updates right? I would have figured that your problem was caused by the same issue, seeing as how it was basically the same problem. Maybe you should try and submit your own bug report here: [http://bugs.opencompositing.org/enter_bug.cgi?product=Compiz%20Fusion]("http://bugs.opencompositing.org/enter_bug.cgi?product=Compiz%20Fusion")
Since this turned out to be a problem in the GConf backend, select that as the component, so you don't get passed off between people. Remember to be as detailed as possible.

---

### Post by pingpongboss on 2007-07-10
i went into ccsm and clicked on every button. Out of like the 50 other buttons, only the Snapping Windows one that does not work and clears all my other icons. Also, i have it unchecked, but my windows still snap to the edges and other windows.

---

### Post by ReverendJ1 on 2007-07-11
I think you should post your own bug report as detailed above. Since this is almost exactly like the problem we were having, the developer will probably be able to fix it right away. From what I gathered from bolderblast's posts when running ccsm from the command-line, it looks like a simple problem with arrays being set to the wrong size. Please post a link to the bug report after you file it in case other people are having the same problem.

---

### Post by animacide on 2007-07-12
Try checking your version of python-compizconfig in synaptic if you are using Trevino's repo.  You may be using an older version that happens to have a newer version number so that it's not getting updated.  If so just use force version to select the newest one.  I was having an identical problem and that fixed it.

---

