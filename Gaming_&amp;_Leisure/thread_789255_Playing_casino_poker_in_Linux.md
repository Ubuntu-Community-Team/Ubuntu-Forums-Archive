---
title: "Playing casino poker in Linux"
date: 2008-05-10
forum: Gaming &amp; Leisure
---

### Post by AmpersUK on 2008-05-10
Greetings,

I have tried my present games in Linux but they have not been satisfactory.

I am asking whether anyone her knows whether any poker gaming website has actually written their access software for the Linux operating system?

---

### Post by Perfect Storm on 2008-05-10
I knoe SimbaPoker support Linux but it's only card casino games: [http://gaming.gwos.org/doku.php/games:alphabetical:s:simbapoker](http://gaming.gwos.org/doku.php/games:alphabetical:s:simbapoker)

---

### Post by AmpersUK on 2008-05-10
> **Artificial Intelligence said:**
> I knoe SimbaPoker support Linux but it's only card casino games: [http://gaming.gwos.org/doku.php/games:alphabetical:s:simbapoker](http://gaming.gwos.org/doku.php/games:alphabetical:s:simbapoker)

Thanks, I went there and downloaded the Linux version but could not open the file at all.

---

### Post by Perfect Storm on 2008-05-10
```
cd ~/Desktop
tar zxfv SimbaPoker.tgz
./SimbaPoker
```

---

### Post by AmpersUK on 2008-05-10
Thanks for that, now working. Bit short of players at present in the play money, but they will come.

---

### Post by fatality_uk on 2008-05-10
Andrew, a fellow poker player :D

If you play for fun, then simbapoker is good but also PokerTH is a fine piece of software. I play there quite a bit [Handle: DevilFish]

If you play for cash, I can usually be found on pokerheaven, partypoker or pokerroom. Let me know if you want a game

---

### Post by Perfect Storm on 2008-05-11
Partypoker is java right? So in theory it should work natively in linux?

---

### Post by AmpersUK on 2008-05-11
If you play for fun, then simbapoker is good but also PokerTH is a fine piece of software. I play there quite a bit [Handle: DevilFish]

I wouldn't want to clean you out, Devilfish! :lolflag:

However, instructions on how to open the Linux PokerTH Zip file and get the files into my computer would be very much appreciated. I notice it is from SuSE so it might not be that straightfoward for a rank beginner.

---

### Post by Perfect Storm on 2008-05-11
getting it and unpacking:
```
cd ~/Desktop
wget http://downloads.sourceforge.net/pokerth/PokerTH-0.6.1-linux.zip?use_mirror=osdn
unzip PokerTH-0.6.1-linux.zip
```

now for playing it:
```
cd ~/Desktop/PokerTH-0.6.1
./pokerth
```

installing bcp if it complaining.
full lib list needed;
```
[size=1]	linux-gate.so.1 =>  (0xffffe000)
	libboost_thread-mt.so => not found
	libboost_filesystem-mt.so => not found
	libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7e76000)
	libmikmod.so.2 => not found
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7e6e000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7e56000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf7e4d000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf7e47000)
	libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf7e42000)
	libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf7e39000)
	libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf7e36000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf7dc6000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf7d9b000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7d8d000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7ca6000)
	librt.so.1 => /lib32/librt.so.1 (0xf7c9d000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7c85000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7c81000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7b8d000)
	libm.so.6 => /lib32/libm.so.6 (0xf7b68000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7b5d000)
	libc.so.6 => /lib32/libc.so.6 (0xf7a0e000)
	libasound.so.2 => /usr/lib32/libasound.so.2 (0xf794b000)
	libdirectfb-1.0.so.0 => /usr/lib32/libdirectfb-1.0.so.0 (0xf78e8000)
	libfusion-1.0.so.0 => /usr/lib32/libfusion-1.0.so.0 (0xf78df000)
	libdirect-1.0.so.0 => /usr/lib32/libdirect-1.0.so.0 (0xf78cc000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf78b7000)
	libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf7896000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7893000)
	libxcb-xlib.so.0 => /usr/lib32/libxcb-xlib.so.0 (0xf7890000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf7878000)
	/lib/ld-linux.so.2 (0xf7f24000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7873000)
[/size]
```

---

### Post by AmpersUK on 2008-05-11
Hmmm,

Followed the instructions, tothe letter I think, but alas it hasn't worked for me. I attach a text file of what I did in case there was something I was being silly with.

---

### Post by Perfect Storm on 2008-05-11
```
sudo apt-get update && sudo apt-get-upgrade
sudo apt-get install libboost-thread1.34.1
sudo ln -s /usr/lib/libboost_thread-gcc41-mt-1_34_1.so.1.34.1 /usr/lib/libboost_thread-mt.so
```

Lets take it whole at once;
```
cd ~/Desktop/PokerTH-0.6.1
ldd pokerth
```
post the outcome.

---

### Post by AmpersUK on 2008-05-11
Thanks for that, seems to be working OK now.

---

### Post by Bakon Jarser on 2008-05-13
Pokerstars works very well in wine.  You'll have to read the wine page to get table resize to work.  I haven't used it in a while but Full Tilt Poker used to work really well in wine also.  I think I had to turn off animations but other then that it worked well.  I know they're not native linux apps but still they work well.

---

### Post by dsiembab on 2008-05-13
[http://pokerroom.com]("http://pokerroom.com") works fine if you have java

---

