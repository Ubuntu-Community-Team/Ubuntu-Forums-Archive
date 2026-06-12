---
title: "Wine and Steam...how do I make an account?"
date: 2005-12-25
forum: Desktop Environments
---

### Post by UltraSonicSite on 2005-12-25
Well maybe it is just a bug on my computer, but when it asks for me to login, I don't know my username or password. So I'm trying to make a new one but when it gets to the license agreement it says I must read it all to the bottom.

Only until I scroll to the bottom can I continue, just one problem, I CANT!

=P

Nothing works, the scroll keys on the side are useless, the arrow keys on my keyboard don't work. And when I try to scroll down by selecting everything it automatically pops right up again.

How in the world did everyone else make an account and I'm the only one that cant?

---

### Post by Evil Whisper on 2005-12-25
UltraSonicSite,

If you don't know your username and or password, You can't re-use your existing CD-Keys.  So you will have to either purchase a new copy of the games you owned or send the original cd case + $10 to valve to get a new key.

--------------------------------------------------------------------------------------
Now onto the problem with creating a new account.  I also had this issue,  the only solution I found was to dig out the windows disc from under 3 feet of dust and install it create the account assign the CD-Key(s) and then quicky reformat and install (K)ubuntu again.

---

### Post by UltraSonicSite on 2005-12-25
I never got a cd key, because I didn't purchase any valve games. I made an account so I could play the half-life 2 demo, but I don't know it anymore. So I'm trying to make a new one but can only do that through Steam itself. Right now I'm downloading an evaluation copy of VMware to see if I can run it perfectly with that.> Now onto the problem with creating a new account. I also had this issue, the only solution I found was to dig out the windows disc from under 3 feet of dust and install it create the account assign the CD-Key(s) and then quicky reformat and install (K)ubuntu again. That could have horrendous results...

---

### Post by UltraSonicSite on 2005-12-25
As of right now vmware seems usless, so I just wasted 700 MB of space downloading it and other crap.

Is there some sort of patch or something? =P

---

### Post by Evil Whisper on 2005-12-25
You could try wine 0.9.4 maybe they fixed somthing in that but you'd have to compile it.

[http://prdownloads.sourceforge.net/wine/wine-0.9.4.tar.bz2](http://prdownloads.sourceforge.net/wine/wine-0.9.4.tar.bz2)

Also Grab the regression patch: 
[http://www.winehq.org/pipermail/wine-patches/2005-December/023021.html](http://www.winehq.org/pipermail/wine-patches/2005-December/023021.html)

Move the patch into your wine source code directory.

Apply using:

```

cd /path/to/your/wine/source/code

```

Then:
```

cat main.patch | patch -p0 

```

To get the things you would need to compile it just add these lines to sources.list:

```

## Official WineHQ Repository
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

```

Then run this:
```

apt-get build-dep wine

```

Then unpack the wine 0.9.4 source code and compile using:
```

./configure --prefix=/usr
make depend && make
sudo checkinstall

```

if you don't have checkinstall installed run this:
```

sudo apt-get install checkinstall

```

---

### Post by UltraSonicSite on 2005-12-25
Alright so far so good, just gotta finish compiling it, and then install the patch.

---

### Post by UltraSonicSite on 2005-12-26
Wheres the wine source code?

---

### Post by Evil Whisper on 2005-12-26
[http://prdownloads.sourceforge.net/wine/wine-0.9.4.tar.bz2](http://prdownloads.sourceforge.net/wine/wine-0.9.4.tar.bz2)

Download that and extract using:

```

 tar --bzip2 -xvf wine-0.9.4.tar.bz2

```

---

### Post by UltraSonicSite on 2005-12-27
Ok, btw, can you explain why compiling takes so damn long? =P

---

### Post by UltraSonicSite on 2005-12-27
Well its done, cept now steam wont even GET to the EULA =P

---

### Post by strikeforce on 2005-12-27
I think you will need to install a web browser e.g. internet explorer or the windows version of firefox then install the activex plugin which is 'windows' only although you can install it in wine.

THe Eula requires this I believe.

---

### Post by UltraSonicSite on 2005-12-27
Hold on lemme try it now, see I got Google Earth to work (except not really cause the menus keep disappearing) and it forced me to install Active X

---

### Post by graveman on 2005-12-28
take a look here maybe it helps

[http://www.linux-gamers.net/modules/wfsection/article.php?page=1&articleid=17](http://www.linux-gamers.net/modules/wfsection/article.php?page=1&articleid=17)

---

### Post by UltraSonicSite on 2005-12-28
Ok I set up an account on another computer, it loads to the main screen and freezes. I'll give you the error, if any, in a few seconds

---

### Post by UltraSonicSite on 2005-12-28
Well it doesnt even start, I get an error that it cant load a DLL file when it starts up. I've seen on the internet that it says that I should start Steam form its main folder, but THATS WHERE I'M GETTING THE ERROR FROM.

=P

---

### Post by silverbolt027 on 2007-02-06
UltraSonicSite, did you ever resolve this problem?  I had the same problem as you, where Wine would crash as I was scrolling down the license agreement (EULA).  Tried a few different things, but I ended up scrolling down using the mouse scrollwheel, line by line, and it made it through...lol strange problem....after it was done installing, I ran sudo wine "c:\Program Files\Steam\Steam.exe", and all is well...right?

Well I had a keyboard issue as well, and after a series of right and left clicking in the textbox, I was able to type....anyways, good luck!

---

