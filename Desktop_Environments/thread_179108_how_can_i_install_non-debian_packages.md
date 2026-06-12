---
title: "how can i install non-debian packages?"
date: 2006-05-19
forum: Desktop Environments
---

### Post by ec2 on 2006-05-19
sorry if a repost.
i can't install *.tar.tar programs. Is it possible in Ubuntu? I've tried ./configure and make and sudo make install, but nothing works. Are these kind of programs even installable in ubuntu or debian distributions?

if someone has ever completely installed one, please help me. Would you try it out with my given package and explain every thing you do? the package is txt2pdf 9.0 from tucows.com. the url to the mirrors is:
[http://www.tucows.com/get/8955_86133](http://www.tucows.com/get/8955_86133)
if you manage to do it, please write down every step and post it...

---

### Post by matthew on 2006-05-19
Check this out...

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by barbarian on 2006-05-19
Hi, look here:

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by barbarian on 2006-05-19
:-)

---

### Post by matthew on 2006-05-19
:)

---

### Post by badrinarayan on 2006-05-19
Hi ec2,

Turns out that the tar.gz file that you linked to is not a source package which you can "configure and make". You can simply extract it to a directory of your choice and run the executable as
```
./txt2pdf
```
I found that this is a shareware program :( 

While we are at the topic of text to PDF, you may be interested in [LaTeX]("http://www.latex-project.org/"), if you can invest some time to make great looking PDFs. [This PDF document]("http://www.ctan.org/tex-archive/info/lshort/english/lshort.pdf") could be a great tutorial to get you started.

Regards
BAdri

---

### Post by ec2 on 2006-05-19
actualöly, i picked txt2pdf as an random program. i have acroread for PDF files. I just wanted to know how to install source packages.

---

### Post by ec2 on 2006-05-19
actually, [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html) was exactly what i was looking for. thank you barbarian and matthew. tnx alot. you just solved a problem i've benn having since i started using linux.... can't install everything...

---

