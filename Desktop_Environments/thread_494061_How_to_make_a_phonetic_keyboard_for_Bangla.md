---
title: "How to make a phonetic keyboard for Bangla?"
date: 2007-07-06
forum: Desktop Environments
---

### Post by shafin on 2007-07-06
First of all,I admit I'm a complete noob to linux.

While on windows,I used a phonetic typing software for Bangla,which converted words typed into english into bangla one's,but on linux,I failed to find one.
So,how can I make a phonetic input system in linux?

Bangla contains complex alphabets which makes it quite difficult.For instance,some alphabets can come together to make a completely new symbol.

---

### Post by shamik on 2007-09-19
I am still finding a solution to this problem . Even I am insisting my geek friends to make something . Though no solution yet. 
But there is atleast one solution that one of my geek friends suggested - go to this link [http://www.shabdik.com/](http://www.shabdik.com/) and download the firefox plug-in . Its still in beta and causes a lot of hassle in typing juktakshor still the somewherein layout given in it is relatively stable . 

Hope it will help . Please inform me if you know any other solution .

Regards

---

### Post by shafin on 2007-09-20
Thanks for the reply.

BTW,I am already using Shabdik,but as you have said,it can't render some of the juktakkhors properly.I used the Avro keyboard in Windows,so here I'm sticking with it too,but the double shift switcher is sometimes annoying.Anyway,its better than nothing.

I went to the Avro forum and made a petition to them for making a linux version.They are trying:), and hopefully,a FF plugin for avro will come out soon.

[http://omicronlab.com/forum/Linux-Petition-t995.html](http://omicronlab.com/forum/Linux-Petition-t995.html)

---

### Post by shamik on 2007-09-28
One of my friend a linux geek has made a bangla phonetic text editor for  linux named muktalekhaa ([http://code.google.com/p/muktalekhaa/]("http://code.google.com/p/muktalekhaa/")) . To install it in ubuntu you must have wxpython and subversion installed
> sudo apt-get install python-wxgtk2.8
sudo apt-get install subversion
Next type 
> *svn checkout [http://beditor.googlecode.com/svn/trunk/muktalekhaa](http://beditor.googlecode.com/svn/trunk/muktalekhaa)*  
(including the url) in your terminal . 
To install the editor go to the muktalekhaa directory 
> cd muktalekhaa 
and type 
> sudo ./installer 
you can now run the editor by the command muktalekhaa
Type on the editor and press space to see it being phonectically converted to bangla. To update the editor go to its directory > cd muktalekhaa and type > svn update The editor is stable but on continuous development . So please update regularly.
By the way- the files created by muktalekhaa can be opened and formatted in open office- no need to cut paste - that solves a lot of problems :) especially when you use bangla a lot

---

### Post by shamik on 2007-10-04
[http://code.google.com/p/muktalekhaa/](http://code.google.com/p/muktalekhaa/)

this is a phonetic bangla notepad based on wxpython

---

### Post by shafin on 2007-10-21
Thanks a lot for the detailed help.

---

