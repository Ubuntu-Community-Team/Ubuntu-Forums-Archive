---
title: "libgl1-mesa-glx woes"
date: 2011-09-02
forum: Desktop Environments
---

### Post by libertypo on 2011-09-02
Hi all,

Recently I decided to give a try to the upcoming Aegisub version 2.1.9 and proceeded to install / compile the relative libraries. One of the dependencies is wxwidgets compiled with opengl support which I have downloaded and tried to compile and failed miserably since the ./configure doesn't find the libraries related to opengl. Now, I should mention that all the libraries pertaining to mesa, libgl1 and glut are all installed including the dev packages. Tinkering around and looking at what is installed where, I noticed that the libgl1-mesa-glx and libglut1-mesa libraries haven't installed not even a single file. They are reported as installed by aptitude but there is nothing in the installation, hence the whining from wxwidgets about not finding the libraries. Ok, I said, let's try a downgrade from version 7.12 to version 7.10 of the said libraries but in that case I'm unable to install the dev packages. 
Has anybody else bumped into this?
Any ideas on how to solve this?

Thanks for your time

---

