---
title: "Neeed help running The mana world!"
date: 2006-10-28
forum: Gaming &amp; Leisure
---

### Post by searayman on 2006-10-28
after succesfullg compiling the mana world i get this error when i try and un it: 

mike@mike-desktop:~$ tmw
tmw: error while loading shared libraries: libguichan_sdl.so.0: cannot open shared object file: No such file or directory
mike@mike-desktop:~$

---

### Post by Perfect Storm on 2006-10-28
If you have libguichan installed and still complains. Try with a symblink:

eg.
```
sudo ln -s /usr/lib/libguichan_sdl.so.0.0.0 /usr/lib/libguichan_sdl.so.0
```

---

### Post by searayman on 2006-10-28
> **Artificial Intelligence said:**
> If you have libguichan installed and still complains. Try with a symblink:

eg.
```
sudo ln -s /usr/lib/libguichan_sdl.so.0.0.0 /usr/lib/libguichan_sdl.so.0
```

i tried what u wanted but not sure if it did anything:

mike@mike-desktop:~$ sudo ln -s /usr/lib/libguichan_sdl.so.0.0.0 /usr/lib/libguichan_sdl.so.0
Password:
mike@mike-desktop:~$ tmw
tmw: error while loading shared libraries: libguichan_sdl.so.0: cannot open shared object file: No such file or directory
mike@mike-desktop:~$ 


and i installed guichan from source with no problems and same with the mana world, but it wont work, if i go into usr/local/bin i can see the tmw

---

### Post by Bjørn on 2006-10-29
> **searayman said:**
> i tried what u wanted but not sure if it did anything:

mike@mike-desktop:~$ sudo ln -s /usr/lib/libguichan_sdl.so.0.0.0 /usr/lib/libguichan_sdl.so.0
Password:
mike@mike-desktop:~$ tmw
tmw: error while loading shared libraries: libguichan_sdl.so.0: cannot open shared object file: No such file or directory
mike@mike-desktop:~$ 


and i installed guichan from source with no problems and same with the mana world, but it wont work, if i go into usr/local/bin i can see the tmw
Maybe you installed Guichan to /usr/local/ as well? It is not default behaviour for libs to be searched in /usr/local/lib, so if libguichan_sdl.so.0 is there it won't be found unless you either add it to your ld.so.conf (and run ldconfig as root afterwards) or set the LD_LIBRARY_PATH.

Note that for Ubuntu Dapper users we have a repository, check the download page on our website. It also works for me on Edgy.

---

### Post by Josey on 2006-11-12
I'm getting this error after I get in game for a few seconds.

```
The Mana World v0.0.20
Account: 0
Char: 1
0x0119 0 0 0 1eff -50
Id: 1 5 001
Id: 4 3 004
Error: Animation: Could not find graphics/sprites/item004.xml!

```

---

### Post by Perfect Storm on 2006-11-12
[http://themanaworld.org/downloads.php#repository](http://themanaworld.org/downloads.php#repository)

---

### Post by Josey on 2006-11-13
Well I can get in game now but it crashes right away or after a minute at best.

```
Couldn't load spriteset!
```

I'm pretty sure this is because I can't seem to get guichan_0.5.0-1_i386.deb to work right in Edgy. The latest in the repository is guichan0.4.0

Can someone point me to a howto for setting up guichan0.5.0? Or a plain howto on compiling from source? Which I suppose I should learn how to do instead of always relying on .deb

Thanks in advance... if not for this forum us newbs wouldn't make it. :D

---

### Post by Josey on 2006-11-14
anyone?

---

### Post by Bjørn on 2006-11-15
It's not able to load a certain spriteset, and that's not because of Guichan. It's either because you haven't updated yet to at least version 0.0.21 (though the repository has 0.0.21.1) or because something went wrong with the updates (try deleting ~/.tmw/updates) or because there's a bug in the game or in the updates (in which case we'd really need to know _which_ spriteset it couldn't load, you could find that in ~/.tmw/tmw.log after the error appeared).

The updating system has no way of verifying the downloaded files yet. This is planned to be added, so that we can at least eliminate the second case.

*Note btw that by now Dapper is no longer supported, since the packages are being built on Edgy.*

---

### Post by Josey on 2006-11-15
Thanks for the reply... yes i have an older version 20.1

Any idea what I am doing wrong after adding this to repositories?
deb [http://bertram.ifrance.com/tmw-dapper](http://bertram.ifrance.com/tmw-dapper) ./

> [http://bertram.ifrance.com/tmw-dapper/./Packages.gz:](http://bertram.ifrance.com/tmw-dapper/./Packages.gz:) 404 Not Found

---

### Post by Josey on 2006-11-15
:(

I'd really like to play this but I have no idea why it isnt working.
Synaptic after adding deb [http://bertram.ifrance.com](http://bertram.ifrance.com) ./ and
 deb-src [http://bertram.ifrance.com](http://bertram.ifrance.com) ./

```
tmw:
  Depends: libcurl3-gnutls (>=7.15.5-1) but 7.15.4-1ubuntu2 is to be installed
  Depends: libxml2 (>=2.6.27) but 2.6.26.dfsg-2ubuntu4 is to be installed
 Depends: tmw-data but it is not going to be installed
```

](*,)

---

### Post by Perfect Storm on 2006-11-16
Which version (x.xx) of ubuntu are you running?

---

### Post by Josey on 2006-11-16
6.10 Edgy

---

### Post by Perfect Storm on 2006-11-16
You have added the wrong source, try go back to the download pages of TMW and re-read it again.

---

### Post by Josey on 2006-11-16
This is the repository I need to add correct?

deb [http://bertram.ifrance.com/tmw-dapper](http://bertram.ifrance.com/tmw-dapper) ./

After adding that with synaptic and hitting reload I get this:

```
http://bertram.ifrance.com/tmw-dapper/./Packages.gz: 404 Not Found 
```

---

### Post by Perfect Storm on 2006-11-16
It might be down at the moment.

---

### Post by Josey on 2006-11-16
Can't wait till it's up :)

My favorite rpg (Final Fantasy Tactics) used job classes. This does something like that doesn't it?

---

### Post by Busch on 2006-11-21
Well this is what i did and it worked.


```
sudo ln -s /usr/local/lib/libguichan_sdl.so.0 /usr/lib
```
 
and after that it will do the same thing for another file and you just do this. 

```
sudo ln -s /usr/local/lib/libguichan.so.0 /usr/lib
```

worked for me  im playing it right now:)

---

### Post by Busch on 2006-11-21
oh wow alot of stuff happened while i was writing up that post.. lol that was the answer to the other question :P.. but yea the ubuntu repository thing doesnt work the link is broke. I just installed the source which worked fine

---

### Post by blind675 on 2006-12-06
help ... 
   what's all this ???

[COLOR="DarkRed"]blind@blind-laptop:~$ tmw
tmw: Symbol `_ZTIN3gcn7TextBoxE' has different size in shared object, consider re-linking
tmw: Symbol `_ZTIN3gcn10ScrollAreaE' has different size in shared object, consider re-linking
tmw: Symbol `_ZTIN3gcn6WindowE' has different size in shared object, consider re-linking
tmw: Symbol `_ZTIN3gcn6ButtonE' has different size in shared object, consider re-linking
tmw: Symbol `_ZTIN3gcn7ListBoxE' has different size in shared object, consider re-linking
tmw: Symbol `_ZTIN3gcn11RadioButtonE' has different size in shared object, consider re-linking
tmw: Symbol `_ZTIN3gcn8CheckBoxE' has different size in shared object, consider re-linking
tmw: Symbol `_ZTIN3gcn9TextFieldE' has different size in shared object, consider re-linking
tmw: Symbol `_ZTIN3gcn6SliderE' has different size in shared object, consider re-linking
The Mana World v0.0.21.1
*** glibc detected *** tmw: free(): invalid pointer: 0x0811a328 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb77c68bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb77c6a44]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7976fc1]
/usr/lib/libguichan.so.0(_ZN3gcn8GraphicsC2Ev+0x360)[0xb79ba010]
[0x81340b8][/COLOR]

   and most important ... how to fix ? :p

---

### Post by Perfect Storm on 2006-12-06
You need the latest version of Mana world to get it to work.

---

