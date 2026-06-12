---
title: "newbie needs help"
date: 2013-04-22
forum: Gaming &amp; Leisure
---

### Post by feralchild on 2013-04-22
Hi Im Dan.
new to computing/gaming but already about to throw laptop out the window.

First, I think I am xubuntu.
Bought Tom Clancy, Rainbow six 3..Raven Shield.
Put disc in slot..Get a message saying 'mounted' and a disc icon on desktop.

Laptop automatically jumps to some media page that says file manager with a dozen icons with little locks on them and thats it..cant get any further.
I just want to put a disc in and play a game..is it too much to ask? Please help.

Thank you for your help and considerations to my now very fragile mental state.

Dan:confused:

---

### Post by nonamedotc on 2013-04-22
> **feralchild said:**
> Hi Im Dan.
new to computing/gaming but already about to throw laptop out the window.

First, I think I am xubuntu.
Bought Tom Clancy, Rainbow six 3..Raven Shield.
Put disc in slot..Get a message saying 'mounted' and a disc icon on desktop.

**Laptop automatically jumps to some media page that says file manager with a dozen icons with little locks on them and thats it..cant get any further.**
I just want to put a disc in and play a game..is it too much to ask? Please help.

Thank you for your help and considerations to my now very fragile mental state.

Dan:confused:

That usually indicates you do not have enough permissions. Are you trying to install the game? **If it is safe**, you can use ***sudo*** to change the permissions and execute the game (assuming it works well in Linux).

Does this help?

---

### Post by oldos2er on 2013-04-22
If the games you bought are Windows games, they will not run natively on Linux. That said, it *may* be possible to get them to run using [Wine]("https://help.ubuntu.com/community/Wine")
I suggest you check the [Wine app database]("http://appdb.winehq.org/") first to see what luck others have had with those particular games. 

Of course if you have a Windows computer handy, that would be the best solution.

---

### Post by feralchild on 2013-04-22
Thank you for reply but I really am new at this. what is sudo. a step by step would help if you not to tired. I got another reply to saying it might be a windows game but I dont think thats the case so im going with the permission thing for starters..so sudo...permission..

1. put disc in.
2.?

Thank you

---

### Post by nonamedotc on 2013-04-22
You can try this - I do not know if this will work though. After you have the disk in, try

```

sudo nautilus /media/{mount point}

```

{mount point} means the location under /media where the CD is mounted. When you type this, you should be prompted for your user password. If I am right, you should not see those lock marks anymore. Try executing the files from there.

**WARNING:** Be **very very** careful when running anything with elevated privileges. You can cause harm to the system!

---

### Post by feralchild on 2013-04-22
Im gonna cause harm to my system in the minute..thank you nonamedotc..will try and get back to you in two shakes of a lambs tail.

---

### Post by QIII on 2013-04-22
Hang on.  Don't go there just yet.

That is a Windows game and, unless it has been ported to Steam, you will need to use Wine.  If it has been ported to Steam, you'll need to use Steam.

It's not as easy as 1, 2, 3.

---

### Post by nonamedotc on 2013-04-22
Oh well! If that's the case, it's going to convoluted!

OP, is it a windows game or a linux game?

---

### Post by CharlesA on 2013-04-22
> **nonamedotc said:**
> Oh well! If that's the case, it's going to convoluted!

OP, is it a windows game or a linux game?

Windows game from the look of it:
[http://en.wikipedia.org/wiki/Tom_Clancy%27s_Rainbow_Six_3:_Raven_Shield](http://en.wikipedia.org/wiki/Tom_Clancy%27s_Rainbow_Six_3:_Raven_Shield)

Looks like it should run in WINE as this says it is Gold rated:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7450&iTestingId=16539](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7450&iTestingId=16539)

---

### Post by nonamedotc on 2013-04-22
Thanks CharlesA - Guess I should not have been so lazy!

feralchild, I suggest you look in to Wine! You should be able to install it from Software Center.... may be.

---

### Post by feralchild on 2013-04-22
Thanks Guys/Gals,
Not as easy as it looks this computer stuff. Thanks for all you ideas and help. will look into wine.
Failing that its back to the xbox. 

cheers. faith in humanity restored.

night all..x

---

### Post by nonamedotc on 2013-04-22
Good luck with that! For some wine works really well! :)

---

### Post by oldrocker99 on 2013-04-22
Wine information is best found at

[http://www.winehq.org](http://www.winehq.org)

They maintain a database of just about every Windows program that has been tried with wine, and you can probably find advice for a installing a specific program with wine by using a search engine.

---

### Post by soloman469 on 2013-04-23
Do you know how to open Terminal? If not, you will need to navigate to the bottom of your screen (you will see a small list of icons). One of them will be Terminal. I will try to get you a sudo script that you can copy and paste into the Terminal to execute the games you wanted. P.S. Are they Windows games?

---

### Post by mastablasta on 2013-04-23
> **feralchild said:**
> Thanks Guys/Gals,
Not as easy as it looks this computer stuff. Thanks for all you ideas and help. will look into wine.
Failing that its back to the xbox. 

cheers. faith in humanity restored.

night all..x

it would be easy if the game was for linux. 

since it is not, you need something like wine to run it. and since you are probably not into command line install play on linux from software center and then use that to install the game. it should be easy enough.

additional note: NEVER use sudo with graphical applicaitons such as 
```
sudo nautilus

```

use grpahical sudo instead for example:
```
gksu nautilus

```

well if you really have xubuntu then you need to replace nautilus with thunar, since thunar is default file browser in xubuntu.

---

