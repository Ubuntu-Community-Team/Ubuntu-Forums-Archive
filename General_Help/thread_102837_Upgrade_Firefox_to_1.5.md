---
title: "Upgrade Firefox to 1.5"
date: 2005-12-12
forum: General Help
---

### Post by Linux-user on 2005-12-12
How do I do this. I downloaded the package but cant upgrade. I would love some help.

---

### Post by 23meg on 2005-12-12
[http://wiki.ubuntu.com/FirefoxNewVersion](http://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by jarrett.wold on 2005-12-12
Or you could grab the tar ball of the firefox site, put it in your user directory and update the menu and pref. applications accordingly.

---

### Post by bb002 on 2005-12-12
To update to firefox 1.5 on my desktop I followed this guide. [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

On the step "Rename your old profile", I missed that when I first installed 1.5 and i haven't noticed/had any problems. So you can make step optional, I guess. Though to be safe, instead of moving the profile copy it instead by changing "mv" to "cp". That way you have a back up if you run into trouble. If you want to be super safe just ignore everything I said after the url :P


[edit] hehe...Maybe I should quit opening up a bunch of threads in different tabs...I tend to post what's already been posted. oops.

---

### Post by Curlydave on 2005-12-13
Can anyone confirm if the tarball version from Mozilla's website runs faster than upgrading the integrated one using that tutorial? I'm using the tarball version, and it runs MUCH faster than the 1.07 one integrated into Ubuntu. However, I'm not sure if this huge speed increase is due to 1.5 or due to using the tarball instead of an integrated browser. Can anyone clear this up? (yes, I'm too lazy to test for myself right now. and don't want to reinstall the FF package which I removed. :p)

---

### Post by lonetree on 2005-12-13
This might not be relevant but just like to comment a little on FF1.5. I have installed on my Wins machine and notice that the loading has tremendously decreased, and it will hang for a while when downloading starts. I haven't try it on my ubuntu yet and I am going to do it later part of the week. I hope it doesn't appear to be the same as FF1.5 on Wins.

However, can someone comfirm that flash works 100% on FF1.5? I notice that in FF1.0.x many flash website does not work 100%, some flash website only display half page and some dun even load at all.

Thanks

Regards,

---

### Post by 23meg on 2005-12-13
[QUOTE=Curlydave]Can anyone confirm if the tarball version from Mozilla's website runs faster than upgrading the integrated one using that tutorial? I'm using the tarball version, and it runs MUCH faster than the 1.07 one integrated into Ubuntu. However, I'm not sure if this huge speed increase is due to 1.5 or due to using the tarball instead of an integrated browser. Can anyone clear this up? (yes, I'm too lazy to test for myself right now. and don't want to reinstall the FF package which I removed. :p)[/QUOTE]The tutorial in the wiki uses nothing other than the tarball from mozilla.org . And once you've made the dpkg-divert as stated there, 1.5 isn't any more "integrated" than 1.07.

---

### Post by 23meg on 2005-12-13
[QUOTE=lonetree]This might not be relevant but just like to comment a little on FF1.5. I have installed on my Wins machine and notice that the loading has tremendously decreased, and it will hang for a while when downloading starts. I haven't try it on my ubuntu yet and I am going to do it later part of the week. I hope it doesn't appear to be the same as FF1.5 on Wins.[/quote]Did you disable IPv6?
[QUOTE=lonetree]
However, can someone comfirm that flash works 100% on FF1.5? I notice that in FF1.0.x many flash website does not work 100%, some flash website only display half page and some dun even load at all.[/QUOTE]All of those I've visited work for me; I've not noticed any difference in Flash operation between 1.07 and 1.5 .

---

### Post by lonetree on 2005-12-13
[QUOTE=23meg]Did you disable IPv6?
All of those I've visited work for me; I've not noticed any difference in Flash operation between 1.07 and 1.5 .[/QUOTE]

yes 23meg, I have disable that. I think it has got nothing to do with that (in Wins context), basically it is the software's problem. 

For the flash part, would appreciate if you could help to check it out on this website. [http://www.fantasy-interactive.com/](http://www.fantasy-interactive.com/)

:-)
regards,

---

### Post by 23meg on 2005-12-13
[QUOTE=lonetree]yes 23meg, I have disable that. I think it has got nothing to do with that (in Wins context), basically it is the software's problem. 
[/QUOTE]What's Wins? What I mean is that you should disable it in network.dns.disableIPv6 under Firefox's about:config .
[QUOTE=lonetree]
For the flash part, would appreciate if you could help to check it out on this website. [http://www.fantasy-interactive.com/](http://www.fantasy-interactive.com/)[/QUOTE]That site looks the same to me under 1.5 and 1.07.

---

### Post by lonetree on 2005-12-13
Hi 23meg,
Wins = Windows

So you said it looks the same as your 1.0.7, does it mean you have a 100% page loaded?

---

### Post by 23meg on 2005-12-13
Yes, all loaded and looking the same in both, also looking the same in Epiphany. Maybe it has something to do with your resolution setting being incorrect; make sure you have your system resolution (the one selected in System / Preferences / Font / Details) selected in Preferences / Content / Fonts & Colors / Advanced / Display Resolution in Firefox.

---

### Post by Ferrat on 2005-12-13
Hmm I just more or less replaced my old Firefox with the 1.5v (cut and paste from the tar), should be said Im running it in chroot 32bit since my system is 64 so I still have 2 installed but everything works just as well in 1.5 as in 1.0.7 only 1.5 looks much better :)

---

### Post by lonetree on 2005-12-13
[QUOTE=23meg]Yes, all loaded and looking the same in both, also looking the same in Epiphany. Maybe it has something to do with your resolution setting being incorrect; make sure you have your system resolution (the one selected in System / Preferences / Font / Details) selected in Preferences / Content / Fonts & Colors / Advanced / Display Resolution in Firefox.[/QUOTE]

I'm suprised, you can load the whole page. Try this, [http://www.phong.com](http://www.phong.com)

---

### Post by pt123 on 2005-12-13
Are the planning to officially release it on Ubuntu?

---

