---
title: "Trying to get fluxbox v1.0rc working with ubuntu"
date: 2006-06-21
forum: Desktop Environments
---

### Post by w1z4rd on 2006-06-21
Im new, so Im doing my best. I can get the standard version of fluxbox working pretty well with my kubuntu setup, the only problem is the lack of tranparency (which you really want with fluxbox!!!)

I think I have gone through just about every tutorial and post on this forum, and the only example I can find, tend to deal with breezy. However, most of the stuff they have in there is relevant, and I was able to solve several earlier steps by reading through them. However, now I am at a point where I am stumped and its a little beyond me.

I download the latest source for fluxbox from fluxbox.org. Currently it happens to be fluxbox v1.0rc. I unpack the file then run this configure command:

```
./configure --enable-imlib2 --enable-xrender --enable-gnome --enable-kde
```

It configures fine, no hassles.

I then type:

```
make
```

And for a while, it seems to compile just fine, until it gets here:

```
-lSM -lICE FbTk/libFbTk.a -lXext -L/usr/local/lib -lXft -lXrender -lfontconfig /usr/local/lib/libfreetype.so -lz -lX11 -Wl,--rpath -Wl,/usr/local/lib -Wl,--rpath -Wl,/usr/local/lib
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libXft.so: undefined reference to `FT_GlyphSlot_Embolden'
collect2: ld returned 1 exit status
make[4]: *** [fluxbox] Error 1
make[4]: Leaving directory `/home/w1z4rd/src/fluxbox-1.0rc/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/w1z4rd/src/fluxbox-1.0rc/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/w1z4rd/src/fluxbox-1.0rc/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/w1z4rd/src/fluxbox-1.0rc'
make: *** [all] Error 2
w1z4rd@b0x:~/src/fluxbox-1.0rc$
```

I have looked everywhere, but I can not seem to find a solution. The only possible thing I can think of is that prehaps my compiler is too new? ( [http://www.linux-noob.com/forums/lofiversion/index.php/t1326.html](http://www.linux-noob.com/forums/lofiversion/index.php/t1326.html) ) but I dont know if thats the case....

Im also not experienced enough to know what any of these : [http://www.google.com/search?q=undefined+reference+to+%60FT_GlyphSlot_Embolden%27&hl=en&lr=&client=firefox&rls=org.mozilla:en-US:unofficial&start=10&sa=N](http://www.google.com/search?q=undefined+reference+to+%60FT_GlyphSlot_Embolden%27&hl=en&lr=&client=firefox&rls=org.mozilla:en-US:unofficial&start=10&sa=N) search results mean. 

Any advice?

---

