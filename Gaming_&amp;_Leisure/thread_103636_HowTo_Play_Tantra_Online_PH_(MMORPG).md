---
title: "HowTo: Play Tantra Online PH (MMORPG)"
date: 2005-12-14
forum: Gaming &amp; Leisure
---

### Post by jeffreyvergara.NET on 2005-12-14
first all, I did not write this guide I just want to share you what I found.

things you need to compile wine:
> apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev

**Step 1**
Download the Wine source code.

Edit the file dlls/wininet/internet.c

Search for the following:

> BOOL WINAPI InternetReadFileExA(HINTERNET hFile, LPINTERNET_BUFFERSA lpBuffer,
DWORD dwFlags, DWORD dwContext)
{
FIXME("stub\n");
return FALSE;
}

Replace it with this:

> BOOL WINAPI InternetReadFileExA(HINTERNET hFile, LPINTERNET_BUFFERSA lpBuffer,
DWORD dwFlags, DWORD dwContext)
{
return InternetReadFile(hFile, lpBuffer->lpvBuffer,
lpBuffer->dwBufferLength, & lpBuffer->dwBufferLength );
}

Its definately a hack - to get around the fact that the function isn't actually implemented... but it gets you to the login segment ( that is - it doesn't bomb out when tryin to get the dat files and stuff... )...

Next problem is actually getting the login request to send correctly... might look at that later tonight... if so then maybe there will be a step 2 up... and if so - will let ya know what step 3 is for fixing Wine...


**Step 2**
Edit the file dlls/wininet/internet.c

Search for the following:

> client1 = HttpOpenRequestW(client, NULL, path, NULL, NULL, accept, dwFlags, dwContext);

replace it with the following:

> WCHAR foobar[urlComponents.dwUrlPathLength + urlComponents.dwExtraInfoLength + 1];

strcpyW(foobar,urlComponents.lpszUrlPath);
strcpyW(foobar + urlComponents.dwUrlPathLength, urlComponents.lpszExtraInfo);
foobar[urlComponents.dwUrlPathLength + urlComponents.dwExtraInfoLength] = (WCHAR) 0;

client1 = HttpOpenRequestW(client, NULL, foobar, NULL, NULL, accept, dwFlags, dwContext);


Then do :
> 
./configure
make depends
make
make install


If you get a strange message about missing or non-compatible X libraries then you're probably trying to build Wine on and AMD64 or Intel extended memory system... so do:

> make clean
./configure --x-libraries=/usr/X11R6/lib
make depends
make
make install

That modified configure line should work... unless you have your X windows libs in a strange place... if so, then just change the directory to the appropriate one...

And NOW boys n girls... YOU can run Tantra on Linux

you'll get 20hrs free trial upon registering. [www.tantra.ph]("http://www.tantra.ph")

> [SIZE="1"]source: [http://forums.tantra.ph/index.php?showtopic=28321&hl=Linux&st=60#](http://forums.tantra.ph/index.php?showtopic=28321&hl=Linux&st=60#)[/SIZE]

---

### Post by alinuxfan on 2006-01-13
never heard of that game before...how is the gameplay?  It looks pretty sweet...
and one more question...how much do you have to pay after those first 20 hrs (I got tired of looking for the answer on the site)

---

### Post by jeffreyvergara.NET on 2006-01-14
hi, its a full 3d MMORPG, it kinda plays like a little bit of Lineage II or if you heard RF (Rising Force) Online. There are 8 Clans of character, and each clan has 2 different race. There is also 3 gods to choose from after you reach lvl 30, There's an event called god wars, where all of the members of the 3 gods battle.

I havn't played this for quite sometime now.

I think you can play the game for a month for only $7 I think... (Php 300, Philippine Peso)

---

### Post by alinuxfan on 2006-01-14
thanks for the info...
I never played Rising Force online but I played it back in the day on my SegaCD
I will have to check it out
thanks

---

### Post by Asraniel on 2006-01-14
you seem to understand wine quite well, why dont you join the developement there? so your improvements will be integrated in the official wine

---

### Post by jeffreyvergara.NET on 2006-01-14
[QUOTE=Asraniel]you seem to understand wine quite well, why dont you join the developement there? so your improvements will be integrated in the official wine[/QUOTE]

oh... i did not find made thatm, I just found it from their game forum. see the source on the first post.
I contacted the man behind this before, but I think he's disappointed on the Tantra PH community.

---

### Post by alinuxfan on 2006-01-14
[QUOTE=jeffreyvergara.NET]
I contacted the man behind this before, but I think he's disappointed on the Tantra PH community.[/QUOTE]


PH = ???
Player Hater?
Phillipines?
something else?

---

### Post by jeffreyvergara.NET on 2006-01-14
lol... Play Hater... something like that.. lol

PH = Philippines. ^_^

---

### Post by werewolfzx8 on 2007-05-22
What version of WINE was this for?

or an update because:
>  BOOL WINAPI InternetReadFileExA(HINTERNET hFile, LPINTERNET_BUFFERSA lpBuffer,
DWORD dwFlags, DWORD dwContext)
{
FIXME("stub\n");
return FALSE;
}

Does not exist in internet.c

I wanna get Tantra Online running without using Virtualbox.

---

### Post by hikaricore on 2007-05-22
Oldest version i can find on sourceforge is:

0.9.19 (2006-08-10 06:46)

As this howto was posted on December 14th, 2005, I would have to guess 0.9.?? or before.

It looks like it's worked for some people:

[http://appdb.winehq.org/appview.php?iVersionId=6388](http://appdb.winehq.org/appview.php?iVersionId=6388)

Have you tried recent versions of wine?

---

### Post by werewolfzx8 on 2007-05-22
Yes, although I'm not that great at programming, it looks pretty simple.

I tried it out in various ways, the source code isn't exactly the same, but looks similar, but alas, it didn't work in the end.

I'll try this version. Thanks


Edit:
[I think I see something that I did wrong in the first attempt on the new version. I'm going to try it again if it works on 0.9.19]

---

### Post by werewolfzx8 on 2007-05-22
OK, I get this on the Make command:
> internet.c:1957: error: expected identifier or ‘(’ before ‘do’
internet.c:1957: error: expected identifier or ‘(’ before ‘while’
internet.c:1958: error: expected identifier or ‘(’ before ‘return’
internet.c:1959: error: expected identifier or ‘(’ before ‘}’ token
internet.c: In function ‘INTERNET_InternetOpenUrlW’:
internet.c:2937: warning: ISO C90 forbids mixed declarations and code
make[2]: *** [internet.o] Error 1
make[2]: Leaving directory `/home/wolf/Desktop/wine-0.9.19/dlls/wininet'
make[1]: *** [wininet] Error 2
make[1]: Leaving directory `/home/wolf/Desktop/wine-0.9.19/dlls'
make: *** [dlls] Error 2


---

### Post by skzo on 2007-06-06
hi, im trying to play tantra on ubuntu 7.10, i could install the game, and update it, i enter the game, but on the login screen i always get password wrong, and that's really weird, cause i can login in the website and, i've tried on a windows machine and i can also login. Does anyone have the same problem ? im using wine 0.9.38, i've also tried crossover, and winex, and i get the same problem :/

---

### Post by werewolfzx8 on 2007-11-01
> **skzo said:**
> hi, im trying to play tantra on ubuntu 7.10, i could install the game, and update it, i enter the game, but on the login screen i always get password wrong, and that's really weird, cause i can login in the website and, i've tried on a windows machine and i can also login. Does anyone have the same problem ? im using wine 0.9.38, i've also tried crossover, and winex, and i get the same problem :/

That's the same issue when I was running 7.04

After I get home tonight, I'm going to tinker around with it and try to get it working if I can.

---

### Post by ihazpower on 2011-09-16
Hi guys!im going to make this post alive again...i have a question. i start the program and initializing to be patched(checking files), i get a program error popup while in the wineappdb, tantra is tested to be running on ubuntu platform
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6388&iTestingId=59408](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6388&iTestingId=59408)

---

### Post by ihazpower on 2011-09-16
Hi guys any help on runnin this program to the current version of linux? i run ubuntu 10.04 :(

---

