---
title: "Setting up Synchronet BBS with Ubuntu"
date: 2016-11-05
forum: Gaming &amp; Leisure
---

### Post by 4ngrygo4t on 2016-11-05
hI, iim trying setup a synchronet bbs with ubuntu but I cught a snag that is holding me back. 

this is the tutorial that shows you how to setup synchronet bbs with ubuntu 

[https://gist.github.com/phuckewe/897d8559f2f6c287d07a](https://gist.github.com/phuckewe/897d8559f2f6c287d07a)

At the top it says: 

download [http://cvs.synchro.net/cgi-bin/viewcvs.cgi/*checkout*/install/terminfo](http://cvs.synchro.net/cgi-bin/viewcvs.cgi/*checkout*/install/terminfo) 

& 

[http://cvs.synchro.net/cgi-bin/viewcvs.cgi/*checkout*/install/termcap](http://cvs.synchro.net/cgi-bin/viewcvs.cgi/*checkout*/install/termcap)

These are configs that need to created into infoterm.txt & termncap.txt Iso I downloaded geany texted editor for ubuntu 16.4

[https://www.geany.org/Download/Releases](https://www.geany.org/Download/Releases)

but here is the problem. After I copy and paste the infoterm and the infocap into the text editor andt save it to the sbbs directory 

I open up termnail 

joshua@joshua-HP-15-Notebook-PC:/sbbs$ sudo tic terminfo.txt

then type

joshua@joshua-HP-15-Notebook-PC:/# sudo -i 

root@joshua-HP-15-Notebook-PC:/etc# cat termcap >> /etc/termcap

root@joshua-HP-15-Notebook-PC:~# nano sbbs.ini

but its blank nothing to edit do I have to browse over to the /sbbs direcotry to edit this sbbs.ini file I cant find it anywhere on my computer nor can I search for it.

So I fired up geany texted editor and searched for it and found it in the /sbbs/ctrl dir

---

