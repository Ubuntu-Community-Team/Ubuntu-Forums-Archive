---
title: "problem with flash in one particular site"
date: 2009-04-19
forum: General Help
---

### Post by jakupl on 2009-04-19
I was wondering if you guys can see this video, and if you have any idea of why I cant.

[http://www.portal.fo/?page=kykmyndir&km=498](http://www.portal.fo/?page=kykmyndir&km=498)

---

### Post by fdrake on 2009-04-19
i can see the video.I am using firefox.did u install the flash plug-in for firefox?

---

### Post by jakupl on 2009-04-19
> **fdrake said:**
> i can see the video.I am using firefox.did u install the flash plug-in for firefox?

no. I installed ubuntu-restricted-extras
Where do I find the add-on?

---

### Post by fdrake on 2009-04-19
at that url firefox should give u a message bar by asking you to installe the missing plug in. if it doesn't go to the adobe-linux site.[Click Here]("http://get.adobe.com/flashplayer/") On the version bar select Deb.Ubuntu version.Download it. And run it. The installatio will start automatically as a debian package.
ps. i suggest u to do a fresh update for your firefox version.

---

### Post by jakupl on 2009-04-19
> **fdrake said:**
> at that url firefox should give u a message bar by asking you to installe the missing plug in. if it doesn't go to the adobe-linux site.[Click Here]("http://get.adobe.com/flashplayer/") On the version bar select Deb.Ubuntu version.Download it. And run it. The installatio will start automatically as a debian package.


when I was going to install the package, it told me that a newer package was available in the repositories, so I just did  ```
sudo apt-get install adobe-flashplugin

```
but it still doesnt work.

> **fdrake said:**
> 
ps. i suggest u to do a fresh update for your firefox version.

what do you mean?

---

### Post by fdrake on 2009-04-19
1.close firefox 

2.use the terminal :
sudo apt-get install firefox

3.now in the terminal:
firefox [http://www.portal.fo/?page=kykmyndir&km=498](http://www.portal.fo/?page=kykmyndir&km=498)

---

### Post by jakupl on 2009-04-19
> **fdrake said:**
> 1.close firefox 

2.use the terminal :
sudo apt-get install firefox

3.now in the terminal:
firefox [http://www.portal.fo/?page=kykmyndir&km=498](http://www.portal.fo/?page=kykmyndir&km=498)

well i used  ```
sudo apt-get install --reinstall firefox
``` but it did not work.

---

### Post by fdrake on 2009-04-19
do u have problems just for this flash site..?

---

### Post by jakupl on 2009-04-19
> **fdrake said:**
> do u have problems just for this flash site..?

yeah. everything else works great. but this site used to work as well.

---

### Post by fdrake on 2009-04-19
type in the terminal:

firefox [http://www.portal.fo/kykmyndir/kykmyndaplayer.php?km=498](http://www.portal.fo/kykmyndir/kykmyndaplayer.php?km=498)

and copy and paste here the output of the terminal.

---

### Post by jakupl on 2009-04-19
> **fdrake said:**
> type in the terminal:

firefox [http://www.portal.fo/kykmyndir/kykmyndaplayer.php?km=498](http://www.portal.fo/kykmyndir/kykmyndaplayer.php?km=498)

and copy and paste here the output of the terminal.

Nothing interesting i think.

```
jakup@bobby:~$ firefox http://www.portal.fo/?page=kykmyndir&km=498
[1] 8665
jakup@bobby:~$ ** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

```

---

### Post by fdrake on 2009-04-19
do u have a 64-bit?

---

### Post by jakupl on 2009-04-19
> **fdrake said:**
> do u have a 64-bit?

nope.

---

### Post by fdrake on 2009-04-19
it looks like there is something wrong with your flash-player, because i don't get any of your outputs . I am not sure what exactly.. . 
you said before you were able to see the video. did u do any update/grade that maybe caused this? hope someone with more knowledge can help u.

---

### Post by jakupl on 2009-04-19
> **fdrake said:**
> 
you said before you were able to see the video. did u do any update/grade that maybe caused this?

Not that I know of.

---

