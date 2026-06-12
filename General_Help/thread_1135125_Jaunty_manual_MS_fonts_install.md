---
title: "Jaunty manual MS fonts install"
date: 2009-04-24
forum: General Help
---

### Post by ivanhelguera on 2009-04-24
I was trying to install MS fonts manually (no, MSTTcorefonts is not enough). 
I created /usr/share/fonts/MS, and copied the ttfs from my ipod. (which came from a win partition). 

```

sudo cp /media/IPOD/TECZKA/MS\ Fonts/* . 

espace@acer-ubuntu:/usr/share/fonts/MS$ ls
arialbd.ttf  ebtmi5.ttf    georgiai.ttf  palabi.ttf    timroub.ttf
arialbi.ttf  ebtmi7.ttf    georgia.ttf   palab.ttf     timroui.ttf
ariali.ttf   ebtr10.ttf    georgiaz.ttf  palai.ttf     timrou.ttf
arial.ttf    ebtr5.ttf     impact.ttf    pala.ttf      trebucbd.ttf
ariblk.ttf   ebtr7.ttf     kartika.ttf   ply_____.ttf  trebucbi.ttf
comicbd.ttf  ebtsl10.ttf   l_10646.ttf   raavi.ttf     trebucit.ttf
comic.ttf    ebtsy10.ttf   latha.ttf     shruti.ttf    trebuc.ttf
courbd.ttf   ebtsy5.ttf    lsansdi.ttf   sylfaen.ttf   tunga.ttf
courbi.ttf   ebtsy7.ttf    lsansd.ttf    symbol.ttf    verdanab.ttf
couri.ttf    ebtti10.ttf   lsansi.ttf    tahomabd.ttf  verdanai.ttf
cour.ttf     ebttt10.ttf   lsans.ttf     tahoma.ttf    verdana.ttf
ebtbx10.ttf  estre.ttf     lucon.ttf     timesbd.ttf   verdanaz.ttf
ebtbx5.ttf   framdit.ttf   mangal.ttf    timesbi.ttf   vrinda.ttf
ebtbx7.ttf   framd.ttf     marlett.ttf   timesi.ttf    webdings.ttf
ebtex10.ttf  gautami.ttf   micross.ttf   times.ttf     wingding.ttf
ebtmi10.ttf  georgiab.ttf  mvboli.ttf    timroubi.ttf
espace@acer-ubuntu:/usr/share/fonts/MS$ sudo fc-cache -fv
/usr/share/fonts: caching, new cache contents: 0 fonts, 5 dirs
/usr/share/fonts/MS: caching, new cache contents: 79 fonts, 0 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 2 fonts, 13 dirs
/usr/share/fonts/truetype/arphic: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 60 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/sazanami: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, new cache contents: 51 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-arabeyes: caching, new cache contents: 39 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-liberation: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/ttf: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/espace/.fonts: skipping, no such directory
/usr/share/fonts/truetype/ttf-malayalam-fonts: skipping, no such directory
/var/cache/fontconfig: cleaning cache directory
/home/espace/.fontconfig: cleaning cache directory
fc-cache: succeeded


```
That sounds quite cool, especially 
```

/usr/share/fonts/MS: caching, new cache contents: 79 fonts, 0 dirs
```
which seems to indicate that the fonts in the directory I created were found and cached. 
However, when I open FF, it ***fails to render any windows font***, making much of the websites garbage. 
Am I doing something wrong? Any ideas?

---

### Post by coffeecat on 2009-04-24
That *should* have worked. Have you checked in OpenOffice or another app to see whether they are available there? Because if they are, this would be a Firefox problem.

The only other thing I can suggest is to create a ~/.fonts folder and copy all your MS fonts into there. You don't have to run fc-cache if you do that, but the fonts are only available to your account, not system wide of course.

---

### Post by prshah on 2009-04-24
> **ivanhelguera said:**
> 
```

sudo cp /media/IPOD/TECZKA/MS\ Fonts/* . 

```

Considering that you've used sudo to copy the fonts, I'd guess a permissions issue; please check if the fonts are readable by others. If they are not a simple```
sudo chmod o+r /usr/share/fonts/MS/*
``` will make all fonts readable by everybody.

---

### Post by ivanhelguera on 2009-04-24
> **coffeecat said:**
> 
The only other thing I can suggest is to create a ~/.fonts folder and copy all your MS fonts into there. You don't have to run fc-cache if you do that, but the fonts are only available to your account, not system wide of course.

Well, copying to .fonts did work. 
> **prshah said:**
> Considering that you've used sudo to copy the fonts, I'd guess a permissions issue; 
It seems really to be a permissions issue. The fonts do dot have -r for others, so are not user - readable. 
However, changing the permissions did not eliminate all the problems. ***Some*** fonts are rendered as garbage when use systemwide - installed fonts with chmod o+r
With ~/.fonts- installed ttfs all seems fine. 
I will explore the topic, and report the findings. 
Thanks for help!
EDIT
After another fonts cache update th pages render OK. Great!
Thanks for help again.

---

### Post by ivanhelguera on 2009-04-24
Now, the thing is that i've done that many times before - I've installed many ubuntus for friends and family, and providing windows fonts (especially Veridana, not included in MSTT) was a key factor for proper www rendering. 
I'm pretty sure I never had to resort to chmod. It seems to me that the problem appeared in Jaunty. 
[https://wiki.ubuntu.com/Fonts]("https://wiki.ubuntu.com/Fonts")
does not contain any info about permissions problem with fonts.

---

### Post by prshah on 2009-04-24
> **ivanhelguera said:**
> Well, copying to .fonts did work. 


Yes, copying to ~/.fonts will work, but only for the user whose home directory it is. Other users will be left out.

What you have done earlier is better; the fonts will be available to all users.

---

### Post by ivanhelguera on 2009-04-24
> **prshah said:**
> What you have done earlier is better; the fonts will be available to all users.
I did manage to make them available through /usr/share/bin, having changed the permissions the way you suggested. Cache clear did not work at first attempt for some reason, but the second attempt did the trick. 
Thanks!

---

### Post by turezky on 2009-04-25
Hi, everybody!
I've just installed Jaunty and have this annoying font problem. Installing-reintalling msttcorefonts / ttf-mscorefonts-installer wouldn't work for me.
I tried installing fonts manually by creating a folder in /usr/share/fonts, adding fonts I've copied from Windows there, chmoding files o+r and refreshing the font cache (2 times :)) and the fonts still wouldn't appear.
What did I do wrong? Could you please write step by step what do I have to do?
Thanks in advance!

---

### Post by ivanhelguera on 2009-04-25
> **turezky said:**
> Hi, everybody!
I've just installed Jaunty and have this annoying font problem. Installing-reintalling msttcorefonts / ttf-mscorefonts-installer wouldn't work for me.
What do you mean?
> 
I tried installing fonts manually by creating a folder in /usr/share/fonts, adding fonts I've copied from Windows there, chmoding files o+r and refreshing the font cache (2 times ) and the fonts still wouldn't appear.
The method seems right. 
Try creating a ~/.fonts directory, and copying the MS fonts into that folder. If the problem arose from permissions, you should have your fonts available (single-user only, though).

---

### Post by turezky on 2009-04-25
```
turezky@turezky-laptop:/usr/share/fonts$ ls -l MS
total 29408
-rw-r--r-- 1 root root   352224 2009-04-25 14:43 arialbd.ttf
-rw-r--r-- 1 root root   226748 2009-04-25 14:43 arialbi.ttf
-rw-r--r-- 1 root root   207808 2009-04-25 14:43 ariali.ttf
-rw-r--r-- 1 root root   178316 2009-04-25 14:43 ARIALNBI.TTF
-rw-r--r-- 1 root root   178864 2009-04-25 14:43 ARIALNB.TTF
-rw-r--r-- 1 root root   179368 2009-04-25 14:43 ARIALNI.TTF
-rw-r--r-- 1 root root   173936 2009-04-25 14:43 ARIALN.TTF
-rw-r--r-- 1 root root   367112 2009-04-25 14:43 arial.ttf
-rw-r--r-- 1 root root 23275812 2009-04-25 14:43 ARIALUNI.TTF
-rw-r--r-- 1 root root   118832 2009-04-25 14:43 ariblk.ttf
-rw-r--r-- 1 root root    45260 2009-04-25 14:43 ARLRDBD.TTF
-rw-r--r-- 1 root root   312920 2009-04-25 14:43 courbd.ttf
-rw-r--r-- 1 root root   236148 2009-04-25 14:43 courbi.ttf
-rw-r--r-- 1 root root   245032 2009-04-25 14:43 couri.ttf
-rw-r--r-- 1 root root   303296 2009-04-25 14:43 cour.ttf
-rw-r--r-- 1 root root   141032 2009-04-25 14:43 georgiab.ttf
-rw-r--r-- 1 root root   157388 2009-04-25 14:43 georgiai.ttf
-rw-r--r-- 1 root root   155068 2009-04-25 14:43 georgia.ttf
-rw-r--r-- 1 root root   159736 2009-04-25 14:43 georgiaz.ttf
-rw-r--r-- 1 root root   355680 2009-04-25 14:43 tahomabd.ttf
-rw-r--r-- 1 root root   383804 2009-04-25 14:43 tahoma.ttf
-rw-r--r-- 1 root root   398372 2009-04-25 14:43 timesbd.ttf
-rw-r--r-- 1 root root   239692 2009-04-25 14:43 timesbi.ttf
-rw-r--r-- 1 root root   248368 2009-04-25 14:43 timesi.ttf
-rw-r--r-- 1 root root   409280 2009-04-25 14:43 times.ttf
-rw-r--r-- 1 root root   123096 2009-04-25 14:43 trebucbd.ttf
-rw-r--r-- 1 root root   131188 2009-04-25 14:43 trebucbi.ttf
-rw-r--r-- 1 root root   134108 2009-04-25 14:43 trebuc.ttf
-rw-r--r-- 1 root root   137616 2009-04-25 14:43 verdanab.ttf
-rw-r--r-- 1 root root   155076 2009-04-25 14:43 verdanai.ttf
-rw-r--r-- 1 root root   171792 2009-04-25 14:43 verdana.ttf
-rw-r--r-- 1 root root   154800 2009-04-25 14:43 verdanaz.ttf
```
Above is the list of the fonts in /usr/share/fonts/MS
Both fonts and MS folder are accessible by "others"...
I also copied the fonts into ~/.fonts directory. Both directly pasted in there, and then pasted a directory inside the ~/.fonts (which actually crashed my fonts completely, so I removed the directory)

Here's also what the font cache refreshing outputs:
```

turezky@turezky-laptop:/usr/share/fonts$ sudo fc-cache -f -v
/usr/share/fonts: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/MS: caching, new cache contents: 32 fonts, 0 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 43 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 2 fonts, 13 dirs
/usr/share/fonts/truetype/arphic: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 60 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/sazanami: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, new cache contents: 51 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-arabeyes: caching, new cache contents: 39 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 6 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-liberation: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/turezky/.fonts: caching, new cache contents: 32 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-malayalam-fonts: skipping, no such directory
/var/cache/fontconfig: cleaning cache directory
/home/turezky/.fontconfig: cleaning cache directory
fc-cache: succeeded

```

---

