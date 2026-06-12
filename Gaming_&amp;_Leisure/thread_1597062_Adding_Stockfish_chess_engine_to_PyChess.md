---
title: "Adding Stockfish chess engine to PyChess"
date: 2010-10-14
forum: Gaming &amp; Leisure
---

### Post by PC_load_letter on 2010-10-14
1. Download the latest Stockfish source + opening book from here:
[http://www.stockfishchess.com/download/](http://www.stockfishchess.com/download/)

2. Unzip the file in a folder say ~/Stockfish

3. Open a terminal in this folder and type: 
```
make profile-build ARCH=x86-64    %(This is for 64-bit systems)

```

or

```
make profile-build ARCH=x86-32    %(This is for 32-bit systems)
```

4. Once compiled successfully, and while in the same directory from the terminal, install by typing: 
```
sudo checkinstall
```
Note: you will get an error that "Stockfish" has uppercase letters and that dpkg doesn't like that so it will change the binary name to "stockfish".
Also, you will get asked to write a short description for the deb package, you can skip that if you don't want to bother.

5. When done, use your favorite xml editor (I used Geany) to open **~/.pychess/engines.xml **

6. Once the file is open, add the following two lines: 
```
<engine binname="stockfish" protocol="uci" protover="1">
<meta><country>us</country></meta></engine>
```

7. That's it, launch PyChess (mine was version Staunton 0.10beta1 running on Karmic 64bit), and you'll see Stockfish in the engines list. Enjoy!

---

### Post by NeoAndersen on 2011-05-13
As I already had Stockfish installed I just had to follow the steps 5 and 6...
I don't have an favourite xml editor as I'm not a programer... But I like the look of Geany...
I just had to figure it out alone how to open this .xml file with Geany...
The first thing I tried worked very well and it was to type this on terminal:
[COLOR="Red"]"Geany ~/.pychess/engines.xml"[/COLOR] 
Then as I know a little about html I just added these lines before the last tag (</engines>):
<engine binname="stockfish" protocol="uci" protover="1">
<meta><country>us</country></meta></engine>

Thank you for the help!

---

