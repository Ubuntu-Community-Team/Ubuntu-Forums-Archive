---
title: "[urgent] how can I keep a software running on ubuntu without login"
date: 2008-07-25
forum: Desktop Environments
---

### Post by mr.eng6 on 2008-07-25
hello guys

I have a ubuntu Desktop 7.04 LTS installed on my server
and I connect to the server using [NX client]("http://help.ovh.co.uk/UbuntuDeskGeneralities") 

and the problem is:

I want to make a software keep running without my account are still logged on 
Because I want to download and upload torrent using my server , and the only torrent web client available is (torrentFlux) and it's very horrible, so I use [Azues]("http://www.azeus.com/en/") or bittorent

BUT the problem is this software unlike webmin (apache , mysql ..ect) the don't keep running unless my account is still logged in 

if I close the connection all normal software close 

what I want is to find a method to accomplish one of this goals :

1. make a bittorrent [software] client keep running on the server without me logging ... like apache and ftp

OR 
2. find the best method to make my server seedbox on ubuntu without using (torrentFlux) , because it crash a lot , can't download and upload lot of torrent and have many issues and problem !


and thank you:)

---

### Post by Yannick Le Saint kyncani on 2008-07-25
> **mr.eng6 said:**
> I want to make a software keep running without my account are still logged on

Hi mr.eng6,

You could use screen, which will keep console sessions alive when you're not connected.

Of course, that would mean using a console bittorrent client, like bittornado, bittorrent or ctorrent. I have not tried any of those though.

Cheers.

---

### Post by evets25 on 2008-07-25
another good commandline torrent client is rtorrent. If you run it from a console, it should stay alive, even when not logged in. That is, if you run it from the console that you get when you press ctrl+alt+f1 and not gnome-terminal. :)

---

### Post by loboc on 2008-07-25
> **Yannick Le Saint kyncani said:**
> Hi mr.eng6,

You could use screen, which will keep console sessions alive when you're not connected.

Of course, that would mean using a console bittorrent client, like bittornado, bittorrent or ctorrent. I have not tried any of those though.

Cheers.

[http://www.slac.stanford.edu/comp/unix/package/epics/extensions/iocConsole/screen.1.html](http://www.slac.stanford.edu/comp/unix/package/epics/extensions/iocConsole/screen.1.html)

Here is the man page of screen basically what you are most interested in is the following.

```

screen

```

screen will start up and it will look like a normal terminal with a little window bar at the bottom.

```

bittorrentclient foo 

```

run your bit torrent client then hit 
CTL+a
d

To detach from screen and you can log out

when you log back in run sreen to reattch to the session

```

screen -r

```

---

### Post by mojorising on 2008-07-25
Hi, I would just use the standard Unix nohup signal with a command line Bittorrent client. This way, any command you run will stay running after you exit your console session. You don't need to install anything extra to do this. 


Example command line input:
```

$ nohup bittorrentclient &
exit

```

See [http://en.wikipedia.org/wiki/Nohup](http://en.wikipedia.org/wiki/Nohup)


Mike

---

### Post by loboc on 2008-07-27
> **mojorising said:**
> Hi, I would just use the standard Unix nohup signal with a command line Bittorrent client. This way, any command you run will stay running after you exit your console session. You don't need to install anything extra to do this. 


Example command line input:
```

$ nohup bittorrentclient &
exit

```

See [http://en.wikipedia.org/wiki/Nohup](http://en.wikipedia.org/wiki/Nohup)


Mike

nohup is fine if you want the program to run to completion or it does not require any interactive elements.

[http://en.wikipedia.org/wiki/Nohup](http://en.wikipedia.org/wiki/Nohup)
 
screen allows interactive things.

---

