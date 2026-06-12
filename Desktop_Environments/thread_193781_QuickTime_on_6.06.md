---
title: "QuickTime on 6.06"
date: 2006-06-10
forum: Desktop Environments
---

### Post by nami on 2006-06-10
Hi

When I used to use Ubuntu 5.10, I was able to get QuickTime configured very easily using the into on the wiki's!

But on 6.06 I cant seem to get it to work?

For example, I would like to play the trailers on the following site: [http://www.apple.com/trailers/](http://www.apple.com/trailers/)

On ubuntu 5.10 firefox used some mplayer plugin, but it does not seem to be available on ubuntu 6.06?

Can anyone help?

nami

---

### Post by kaamos on 2006-06-10
> On ubuntu 5.10 firefox used some mplayer plugin, but it does not seem to be available on ubuntu 6.06?
install the package "mozilla-mplayer".

---

### Post by nami on 2006-06-10
I did a search in synaptic package manager for mozilla-mplayer and nothing came up.  I think I have everything enabled as you can see from my sources.list

> 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main


---

### Post by ZipoTe on 2006-06-10
I did the same. I look for mozilla-mplayer but... in does not exists :(

---

### Post by nami on 2006-06-10
It DID exist when I had ubuntu 5.10 installed, but for some reason, lots of things are missing with ubuntu 6.06 ???

---

### Post by kaamos on 2006-06-10
You are missing multiverse from your sources.list

---

### Post by nami on 2006-06-10
How do I add it?

---

### Post by kaamos on 2006-06-10
```

deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
```

---

### Post by nami on 2006-06-10
Thanks!

I just figured out how to enable it through synaptic package manager!

---

### Post by abbot on 2006-06-10
totem-xine plays those quicktime video's just fine.  what you need is a neat little firefox plugin called [_MediaPlayerConnectivity_](https://addons.mozilla.org/firefox/446/) that lets you play any and all imbeded video in an external player outside of the browser (so you can resize it and stuff too).  i've never had the best luck with just the totem-xine-firefox-plugin, but you also have to have that installed to use that MediaPlayerConnectivity extension.  If you would rather use mplayer though, go ahead and do what you're doin.

---

### Post by nami on 2006-06-10
Thanks

---

