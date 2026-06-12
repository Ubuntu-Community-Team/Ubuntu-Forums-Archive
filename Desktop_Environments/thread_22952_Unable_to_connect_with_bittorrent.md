---
title: "Unable to connect with bittorrent"
date: 2005-03-30
forum: Desktop Environments
---

### Post by bistrototal on 2005-03-30
I can't seem to connect to peers when trying to download via bittorrent. I've tried both the bittornado GUI and btdownloadheadless. I tried for example to download some ubuntutorrents, but i connect to no peers.

My internet connection seems to work fine except from this, and i have NO idea what the reason for the problem could be...

---

### Post by jeremy on 2005-03-30
Are you using a firewall?

---

### Post by bored2k on 2005-03-30
[QUOTE=bistrototal]I can't seem to connect to peers when trying to download via bittorrent. I've tried both the bittornado GUI and btdownloadheadless. I tried for example to download some ubuntutorrents, but i connect to no peers.

My internet connection seems to work fine except from this, and i have NO idea what the reason for the problem could be...[/QUOTE]
 Bittornado gui usually comes with sloppy ports configured, you have to set it up. I would recommend [http://www.bittorrent.com/dl/BitTorrent-4.0.1.tar.gz](http://www.bittorrent.com/dl/BitTorrent-4.0.1.tar.gz) for the official, latest and arguably best client . It uses 6881-6885 as ports, so make sure 
a) those ports are forwarded in your router [if any] and forwarded in your firewall [if any]
b) the torrent's tracker is still active .

---

### Post by bistrototal on 2005-03-30
Thankyou very much for your quick replies!

I downloaded the latest bittorrent client from the web, but i chose the .deb-package.
After dpkg -i package, i tried to download 

```
btdownloadheadless.py http://stuwww.uvt.nl/ubuntu/hoary/hoary-preview-install-i386.iso.torrent

``` but then i recieve the "classical" python error messages:
```
Traceback (most recent call last):
  File "/usr/bin/btdownloadheadless.py", line 24, in ?
    from BitTorrent.download import Feedback, Multitorrent
ImportError: No module named BitTorrent.download

```
I haven't installed any firewall software, and regarding the ports i have no clue. Is there a simple way to check?

Thanks!

---

### Post by chronusdark on 2005-04-01
please dont flame me but i think azureus is a much nicer bittorrent client

you should check it out

[http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)

---

### Post by bored2k on 2005-04-01
[QUOTE=chronusdark]please dont flame me but i think azureus is a much nicer bittorrent client

you should check it out

[http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)[/QUOTE]
 I dislike it . It has too many configuration options that if done the bad way can crap our your download experience. Bittorrent official, the latest 4 owns them all IMO. I understand the love for Azureus, but its a java resource hog and has just way too many things to deal with .

Not blaming you for liking it though . I wish I had my Windows torrentstorm or a bitcomet port .

---

### Post by LongTooth on 2005-04-01
Well, I've had nothing but good luck with Azureus. While I respect bored2k's expertise and opinion, I have to agree with chronusdark and recommend Azureus. I used the steps out lined in the 'Unofficial Ubuntu 4.10 Starter Guide ( [http://ubuntuguide.org/](http://ubuntuguide.org/) ). Follow the steps and you shouldn't have any problems. I have Hoary on my PC and those instructions worked. You'll have to configure your router if you're using one. The Azureus site also provides those steps to configure it. Good luck.

---

### Post by bored2k on 2005-04-01
Just got owned :( .

Its a matter of taste, they will both use the ports you specify and work depending on the torrent and its tracker. I'm not sure if BT Official supports udp ports, but Azureus does. Its just that I like simplistic applications that work, while keeping a low profile on your MB ram ;). But hey, I was a regular poster and guide @ lokitorrent, and 88% of the users liked azureus the most, so its no different now ;) .

---

### Post by coolaj86 on 2005-08-07
It looks to me like a dependancy problem. That was my issue.

Take a look here and make sure you have `apt-get install`d all of these:
[http://gentoo-portage.com/net-p2p/gnome-btdownload/dep](http://gentoo-portage.com/net-p2p/gnome-btdownload/dep)

Because of a version conflict I had to edit
/usr/lib/python2.4/site-packages/gtk-2.0/gnome/vfs.py
changing 'gnomevfs' to 'gnome.vfs'

BTW: There's a lot of sharing that needs to be going on between Gentoo and Ubuntu. We two communities seem to be the most active out of any of the Linux distros and each have valuable forums, wikis, and other resources that can be cross-referenced.

;-)

---

