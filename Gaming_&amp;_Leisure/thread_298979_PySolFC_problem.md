---
title: "PySolFC problem?"
date: 2006-11-13
forum: Gaming &amp; Leisure
---

### Post by cricketshadowolf on 2006-11-13
I downloaded PySolFC from sourceforge.net and I managed to finally get it working and my menu icons up and running. But I also want to install the extra cardsets and the cardset maker program. I can't seem to figure out how to get it to install. The files in the program aren't much help. I am a fairly newbie. I tried the newbie threads and didn't get any help. So I am trying here before I give up. Yes, I have been searching the threads on other games and tar files and haven't got much useful info. Yes I read "How to Install Anything in Ubuntu" and not there either. Or at least I did not see it. Here are the files:
Cardset-Maker-0.1/
data=image files
scripts
  /build.bat
  /create_iss.py
cardset_maker.py
MANIFEST.in
PACKAGE-INFO
README=dependency file
setup.py

PySolFC-Cardsets-1.0/
 cardfiles
 COPYING=public license file

I tried clicking on the executables but maybe I did not do something right.

I really love Pysol and this newest version PysSol Fan Club is awesome I just would like to have my extra bells and whistles with it.

Thanx and if you answer me and we solve the problem the maybe it won't have to solved again. I am sure someone soon is going to try and install it and run into the same brick wasll. Dang it my head hurts.

cricketshadowolf](*,)

---

### Post by cricketshadowolf on 2006-11-16
:p hey y'all it works 100% and it was easy as PY.Once I remembered to PY it. Download the packages. Make sure the dependencies are installed. I could not get the recommended packages to install. Or even the PIL(python imaging library) off the net to work either and it is required, but happily the one in Synaptic works just fine. Python 2.4.Imaging.tk.Just cd to the directory after you extract it to your desktop. sudo cd (drag the file) click the cursor and enter. Type python  setup.py install and hit enter. I kept forgetting to type the all important python first. DUH!!!!!!! So it did not install properly. It worked but not proper. Do the same with Cardset Manager. It will install to /usr/share/PySolFC. If the icons don't install just hand configure them with Alacarte. Cardset-Maker will install to usr/bin/cardset_maker.py the data files will be in /usr/share/PySolFC. I just gotta figure out how to link up the sound server and I will be in Pysol heaven. I added it from the repositories which is I expect the problem.
Hope you try because it is awesome!!!! 

cricketshadowolf

---

### Post by cricketshadowolf on 2006-11-16
Hey it works now. Check out the other post in the newbie section. I forgot to type python before the commands. I guess I was sleep deprived and wired on to much java. Sorry to have bothered you.

Cricketshadowolf

---

