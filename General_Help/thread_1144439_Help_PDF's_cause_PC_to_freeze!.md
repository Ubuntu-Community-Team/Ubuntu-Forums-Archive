---
title: "Help PDF's cause PC to freeze!"
date: 2009-04-30
forum: General Help
---

### Post by mariane_08 on 2009-04-30
I have some PDF's I downloaded. They  are quite large files (maps). When I start scrolling around to view different parts of them I get a total freeze up. Not just the display but the whole PC. This happens every time after 3 or 4 scrolls. 

Then the only option is for me to crash the PC and start again. It's  happening every time I open them. A memory leak perhaps?? Any advice appreciated!

Thanks

Compaq Presario M2000 notebook, AMD64 Turion Proc,
1GB Ram

---

### Post by skymera on 2009-04-30
What is your graphics card?
Do you have desktop effects running?

Could be a driver issue

---

### Post by mariane_08 on 2009-04-30
> **skymera said:**
> What is your graphics card?
Do you have desktop effects running?

Could be a driver issue

I have no desktop effect running. The graphics is ATI Radeon Exp 200
Thanks

---

### Post by mariane_08 on 2009-05-01
Any ideas anyone?

---

### Post by Yashiro on 2009-05-01
You fail to mention which application you are using.

---

### Post by wpshooter on 2009-05-01
Do you have a video driver installed other than the one that is installed by default by the O/S ?

---

### Post by mariane_08 on 2009-05-01
> **Yashiro said:**
> You fail to mention which application you are using.

I'm just using the default Document Viewer

Regarding video drivers: I'm just using the default install one which came with Hardy.

The thing is I never have this problem on ordinary PDF's. Just these large files.

---

### Post by AlexDudko on 2009-05-01
Same problem. Videocard ATI Radeon Xpress 200M, no desktop effects, video driver installed by the O/S.
Evince (and the whole system) freezes only with huge PDF files or those, which have many pictures. 
The only workaround is to convert the files to .djvu - they are simply workable.

---

### Post by e1luca on 2009-05-01
how exatly large are the pdfs? Can you try to rasterize them (in Gimp?) and see them as jpgs until find a better solution?

---

### Post by mariane_08 on 2009-05-01
> **e1luca said:**
> how exatly large are the pdfs? Can you try to rasterize them (in Gimp?) and see them as jpgs until find a better solution?

The PDF's are USGS topo maps, file size 7-12 MB. So they are large but the ISGS web site has a index and download page for all their map so I'd have thought if there was a common problem with them some mention would have been made on the site (at least in win/mac)

Hadn't though about jpegs, will try that, but thats only a tempory fix

---

### Post by wpshooter on 2009-05-01
> **mariane_08 said:**
> The PDF's are USGS topo maps, file size 7-12 MB. So they are large but the ISGS web site has a index and download page for all their map so I'd have thought if there was a common problem with them some mention would have been made on the site (at least in win/mac)

Hadn't though about jpegs, will try that, but thats only a tempory fix

Please give us a link to these MAPS, so someone else can try to view these and see if the problem can be recreated.

Thanks.

---

### Post by mariane_08 on 2009-05-03
> **wpshooter said:**
> Please give us a link to these MAPS, so someone else can try to view these and see if the problem can be recreated.

Thanks.

[http://store.usgs.gov/b2c_usgs/usgs/maplocator/(xcm=r3standardpitrex_prd&layout=6_1_61_75&uiarea=2&ctype=areaDetails&carea=%24ROOT)/.do](http://store.usgs.gov/b2c_usgs/usgs/maplocator/(xcm=r3standardpitrex_prd&layout=6_1_61_75&uiarea=2&ctype=areaDetails&carea=%24ROOT)/.do)

try this. zoom in on the area of interest, follow instructions and you'll get a grid of the maps which you can then download (or purchase for aprox $8 a shot). They download just fine, it;s after that I get the problems.

you need to zoom into a local/county level to use the index grid

eg:
[http://store.usgs.gov/b2c_usgs/usgs/maplocator/(xcm=r3standardpitrex_prd&layout=6_1_61_75&uiarea=2&ctype=areaDetails&carea=%24ROOT)/.do](http://store.usgs.gov/b2c_usgs/usgs/maplocator/(xcm=r3standardpitrex_prd&layout=6_1_61_75&uiarea=2&ctype=areaDetails&carea=%24ROOT)/.do)

---

### Post by wpshooter on 2009-05-03
I can't seem to find anything on this link that you can download without paying $ for it.

---

### Post by unutbu on 2009-05-03
Perhaps try acroread to view the pdfs. 
Use these instructions to enable the Medibuntu repository:
[https://help.ubuntu.com/community/Medibuntu#Adding](https://help.ubuntu.com/community/Medibuntu#Adding) the Repositories

After typing 
```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

(per the instructions above), you should be able to install the acroread package through
Synaptic.

---

### Post by mariane_08 on 2009-05-03
> **wpshooter said:**
> I can't seem to find anything on this link that you can download without paying $ for it.

Yes the downloads are free!
Zoom in to a local level on say your local city. Then follow the instructions on the right under steps 1 and 2. You'll get a grid or a baloon and you can click on the ballon to choose what map you want. In my case the 7.5 minute version. I've downloaded several with the same result

---

### Post by wpshooter on 2009-05-04
> **mariane_08 said:**
> Yes the downloads are free!
Zoom in to a local level on say your local city. Then follow the instructions on the right under steps 1 and 2. You'll get a grid or a baloon and you can click on the ballon to choose what map you want. In my case the 7.5 minute version. I've downloaded several with the same result

Downloaded Roanoke, Virginia and it works just fine on my machine.

---

### Post by mariane_08 on 2009-05-04
> **wpshooter said:**
> Downloaded Roanoke, Virginia and it works just fine on my machine.

Well thanks anyway. I'm suspecting this must be a driver issue with the ATI Video card

---

### Post by yshollande on 2009-05-10
I'm experiencing the same problem with Jaunty and the latest acroread.  Completely freezes the GNOME session; I have to go to a text virtual terminal and kill the acroread process in order to restore some sanity.

Any ideas would be greatly appreciated.

Thanks!

Isaac

---

### Post by torstenaf on 2009-06-28
I'm not sure if this thread is dead or alive, but I'm experiencing the same issues.

Ubuntu 9.04 Jaunty Jackalope
Firefox 3.0.11
acroread 9.1.0

When I open some PDF files, like this one:
[http://www.faucetdirect.com/mediabase/specifications/PFS6036.pdf](http://www.faucetdirect.com/mediabase/specifications/PFS6036.pdf)

My entire gnome session freezes, and I have to use the laptop power button to restart Ubuntu.

My entire desktop should not freeze when opening a file in an application.

Any ideas?

---

### Post by moster on 2009-06-28
If all of you have radeon Xpress 200M I would say it is some rare bug in driver.

I've seen and sense too many issues with that graphic card, this is just one more.

I am not sure if that card is still supported by AMD. If so, you can try install proprietary driver from menu system-administration-hardware drivers.

---

