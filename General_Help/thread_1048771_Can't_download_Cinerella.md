---
title: "Can't download Cinerella"
date: 2009-01-23
forum: General Help
---

### Post by ffixcollector on 2009-01-23
I am trying to install Cinerella, and I get this message when I reload the repositories.  

[PHP]W: Failed to fetch http://akirad.hfbk.net/dists/akirad-intrepid/Release.gpg  Could not connect to akirad.hfbk.net:80 (193.174.241.68), connection timed out

W: Failed to fetch http://akirad.hfbk.net/dists/akirad-intrepid/main/i18n/Translation-en_US.bz2  Unable to connect to akirad.hfbk.net http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
[/PHP]

an I am unable to find Cinerella in the package manager.

---

### Post by afbase on 2009-01-23
have you tried this [http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu) ?

---

### Post by ffixcollector on 2009-01-23
yes, I used the .deb file to install the repositories.

---

### Post by afbase on 2009-01-24
I just want to make sure you followed the steps as I explained.


[LIST=1]
[*]Install the Debian package
[*]System > Administration > Synaptic Package Manager
[*]search and install cinelerra.
[/LIST]
I did this on my intrepid ibex with no problems.  Which part are you stuck on exactly?

---

### Post by Cresho on 2009-01-24
WELL, you don't need to install cinellera to use it.  I use one that actually works with high definition videos.  It has some bugs but still is usable.  If you want to try, here it is.

1.  Download this one [http://heroinewarrior.com/](http://heroinewarrior.com/)
[http://heroinewarrior.com/cinelerra.php](http://heroinewarrior.com/cinelerra.php)

then extract your 32bit or 64 bit tar on your desktop.  THen open terminal and cd into the directory.  then you launch like "./cinelerra"  without quotes.  If you are running gnome, you can just open the directory in nautilus and double click on cinelerra "like an exe in windows" and it opens up.  I do get an error but you can ignore it since it doesnt really mean anything.  This version works with high definition videos.  I used it but found one small problem with crossfading audio.  I think I was doing something wrong but it works fine if you ask me.  I think I don't know what I am doing sometimes.  This heroin version is the best one I found so far.

you can put the program folder in your home directory and creats a sh file so you can launch it from the menu item list in gnome.

---

### Post by ffixcollector on 2009-01-24
The problem is that cinerella does not show up in the search. I believe that the repositories are not getting downloaded, and I don't know why.

---

### Post by iBoniek on 2009-01-29
I've got this problem too but i get:
```

sudo apt-get install cinelerra
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
Zostan&#261; zainstalowane nast&#281;puj&#261;ce dodatkowe pakiety:
  akiradnews cinelerracv libguicastcv libmpeg3cv libquicktimecv
  optlibx11-noxcb-6 optlibx11-noxcb-data
Zostan&#261; zainstalowane nast&#281;puj&#261;ce NOWE pakiety:
  akiradnews cinelerra cinelerracv libguicastcv libmpeg3cv libquicktimecv
  optlibx11-noxcb-6 optlibx11-noxcb-data
0 aktualizowanych, 8 nowo instalowanych, 0 usuwanych i 0 nieaktualizowanych.
Konieczne pobranie 14,2MB archiwów.
Po tej operacji zostanie dodatkowo u&#380;yte 31,0MB miejsca na dysku.
Kontynuowa&#263; [T/n]? t
B&#322;&#261;d http://akirad.cinelerra.org akirad-intrepid/main optlibx11-noxcb-data 2:1.1.3-1akirad1
  404 Not Found
B&#322;&#261;d http://akirad.cinelerra.org akirad-intrepid/main optlibx11-noxcb-6 2:1.1.3-1akirad1
  404 Not Found
B&#322;&#261;d http://akirad.cinelerra.org akirad-intrepid/main libguicastcv 2.1.0-git20081029akirad3
  404 Not Found
B&#322;&#261;d http://akirad.cinelerra.org akirad-intrepid/main libmpeg3cv 2.1.0-git20081029akirad3
  404 Not Found
B&#322;&#261;d http://akirad.cinelerra.org akirad-intrepid/main libquicktimecv 2.1.0-git20081029akirad3
  404 Not Found
B&#322;&#261;d http://akirad.cinelerra.org akirad-intrepid/main akiradnews 20081019
  404 Not Found
B&#322;&#261;d http://akirad.cinelerra.org akirad-intrepid/main cinelerracv 2.1.0-git20081029akirad3
  404 Not Found
B&#322;&#261;d http://akirad.cinelerra.org akirad-intrepid/main cinelerra 1:2.1.0-1svn20081017akirad2
  404 Not Found
Nie uda&#322;o si&#281; pobra&#263; http://akirad.cinelerra.org/pool/main-intrepid/optlibx11-noxcb-data_1.1.3-1akirad1_all.deb  404 Not Found
Nie uda&#322;o si&#281; pobra&#263; http://akirad.cinelerra.org/pool/main-intrepid/optlibx11-noxcb-6_1.1.3-1akirad1_i386.deb  404 Not Found
Nie uda&#322;o si&#281; pobra&#263; http://akirad.cinelerra.org/pool/main-intrepid/libguicastcv_2.1.0-git20081029akirad3_i386.deb  404 Not Found
Nie uda&#322;o si&#281; pobra&#263; http://akirad.cinelerra.org/pool/main-intrepid/libmpeg3cv_2.1.0-git20081029akirad3_i386.deb  404 Not Found
Nie uda&#322;o si&#281; pobra&#263; http://akirad.cinelerra.org/pool/main-intrepid/libquicktimecv_2.1.0-git20081029akirad3_i386.deb  404 Not Found
Nie uda&#322;o si&#281; pobra&#263; http://akirad.cinelerra.org/pool/main-intrepid/akiradnews_20081019_all.deb  404 Not Found
Nie uda&#322;o si&#281; pobra&#263; http://akirad.cinelerra.org/pool/main-intrepid/cinelerracv_2.1.0-git20081029akirad3_i386.deb  404 Not Found
Nie uda&#322;o si&#281; pobra&#263; http://akirad.cinelerra.org/pool/main-intrepid/cinelerra_2.1.0-1svn20081017akirad2_i386.deb  404 Not Found
E: Nie uda&#322;o si&#281; pobra&#263; niektórych archiwów, prosz&#281; spróbowa&#263; uruchomi&#263; apt-get update lub u&#380;y&#263; opcji --fix-missing

```

where "Nie uda&#322;o si&#281; pobra&#263;" is "can't download"

---

