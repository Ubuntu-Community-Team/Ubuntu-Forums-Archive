---
title: "rst2pdf not working in 10.04"
date: 2010-11-08
forum: Education &amp; Science
---

### Post by xadder on 2010-11-08
Hi everyone,

I used to have rts2pdf working to make presentations, but now I just get errors. This was installed by synaptic, but still doesn't work for the simplest things. For example:

rst2pdf -h

Traceback (most recent call last):
  File "/usr/bin/rst2pdf", line 9, in <module>
    load_entry_point('rst2pdf==0.12.3', 'console_scripts', 'rst2pdf')()
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 299, in load_entry_point
    return get_distribution(dist).load_entry_point(group, name)
..... etc  etc.


When working, it was a great system, so wonder if anybody knows what is going wrong here?

Thanks

---

### Post by ralsina on 2010-11-08
This i bug #627427 I reported 2 months ago. Basically, as packaged in Ubuntu, rst2pdf is completely useless.

You are better off installing it from Debian, using easy_install, pip or even downloading the sources.

The bug report and explanation is here: [https://bugs.launchpad.net/ubuntu/+source/rst2pdf/+bug/627427](https://bugs.launchpad.net/ubuntu/+source/rst2pdf/+bug/627427)

---

### Post by xadder on 2010-11-09
Thanks, and yes I agree, Ubuntu have done a very poor job here.

I downloaded from debian as you suggested, just using the gdebi option that popped up when I clicked the link. Worked fine :-)

Just curious, is there a way to get rst2pdf working with an ancient "intrepid" Ubuntu? I have an EeePC with this on, with python2.5, and I couldn't install that from debian. The proper solution is to upgrade the eepc, but I have one meeting I need to go to before I risk that.

(My other home computer is using 10.04 as noted, and at work I have 10.10 where rst2pdf worked from synaptic, as it should.)

Very nice package by the way. I plan to make most of my presentations using this in future.

---

### Post by ralsina on 2010-11-09
Sure you can: easy_install rst2pdf should work even with python 2.4. 

However: reportlab 2.3 has several bugs that may bite you, so maybe you should also remove that package and let easy_install take care of it.

---

### Post by xadder on 2010-11-09
Nah, easy_install doesn't work:

Processing reportlab-2.5.tar.gz
Running reportlab-2.5/setup.py -q bdist_egg --dist-dir /tmp/easy_install-JG1iEb/reportlab-2.5/egg-dist-tmp-r6BVTO
################################################
#Attempting install of _rl_accel, sgmlop & pyHnj
#extensions from '/tmp/easy_install-JG1iEb/reportlab-2.5/src/rl_addons/rl_accel'
################################################
################################################
#Attempting install of _renderPM
#extensions from '/tmp/easy_install-JG1iEb/reportlab-2.5/src/rl_addons/renderPM'
# installing with freetype version 21
################################################
Downloading standard T1 font curves
Finished download of standard T1 font curves
/tmp/easy_install-JG1iEb/reportlab-2.5/src/rl_addons/rl_accel/_rl_accel.c:11:20: error: Python.h: No such file or directory
/tmp/easy_install-JG1iEb/reportlab-2.5/src/rl_addons/rl_accel/_rl_accel.c:35: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token



.... followed by loads of similar errors. (This is all on my older intrepid EeePC. As noted above, 10.04 works fine with the debian)

---

### Post by ralsina on 2010-11-09
You mean easy_install of rst2pdf or of reportlab?

The error you show is a reportlab error. There are some reported cases of reportlab not working via easy_install, so you may want to try the sources and "python setup.py install". 

Reportlab works just fine without rl_accel, though (a tad slower).

---

