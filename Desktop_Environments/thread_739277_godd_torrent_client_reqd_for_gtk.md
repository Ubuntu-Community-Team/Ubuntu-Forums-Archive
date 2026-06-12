---
title: "godd torrent client reqd for gtk"
date: 2008-03-29
forum: Desktop Environments
---

### Post by keratos on 2008-03-29
bittornado: No good! heavy on resource runs separate process per torrent.
azuerez: No good! Eats up 20% memory and too bloated.
deluge: No good! Wants to install about 144 libs (most of them gnome). I steer clear of Gnome & KDE.
transmission: No good! Again, doesnt offer encyption
free-loader: no good! wants to install all the gnome "stuff" (libs etc)

Ideas please good folk.

It MUST have encryption and must *not* require qt/kde. I think a good gtk client would suffice ??

thanks in advance.

---

### Post by Knoeki on 2008-03-29
well, all I can think of is kTorrent, but that's qt, afaik. still a nice program and very much worth it.

---

### Post by keratos on 2008-03-30
> **Knoeki said:**
> well, all I can think of is kTorrent, but that's qt, afaik. still a nice program and very much worth it.

^^^^ It MUST have encryption and **must *not* require qt/kde **^^^^^

thank you

---

### Post by eriqjaffe on 2008-03-30
How about [Transmission]("http://www.transmissionbt.com/index.php")?  GTK and encryption, although I've never used it.

---

### Post by mister_p_1998 on 2008-03-30
Well, I use Dapper with Ktorrent, I love it.

---

### Post by Erunno on 2008-03-30
> **keratos said:**
> transmission: No good! Again, doesnt offer encyption

It does not? I use transmission under Mac OS X and it does support ecryption. Since both the GTK+ and the Cocoa client use the same backend library this is rather strange (unless the GTK+ maintainers thought that encryption might confuse the user).

Anyway, [rTorrent]("http://libtorrent.rakshasa.no/") is a command line client with a ncurses interface and does support encryption according to Wikipedia. Hopefully this is lightweight enough.

---

### Post by keratos on 2008-03-30
okay friends.

I will look at rTorrent and once again at Transmission. When I last installed Transmission, there was no encryption tab/setting. Perhaps their homepage might have a more recent version.

Just to clarify, K<**anything**> is not going on my computer. I intensely dislike anything to do with KDE. PLEASE see above posts.

---

### Post by eriqjaffe on 2008-03-30
Transmission specifically mentions encryption on [this page](http://www.transmissionbt.com/about.php), so I was basing my assumption on that.  ;)

---

### Post by handy on 2008-03-31
Transmission works really well on my iMac, with encryption & very regular updates.

I have just installed it on Arch, it has an option to ignore unencrypted peers.

---

### Post by firmit on 2008-03-31
Transmission works for me.
There is always uTorrent which may be run under wine....

---

### Post by Nythain on 2008-03-31
+1 for rtorrent

---

### Post by keratos on 2008-04-05
thanks for the pointers good people, 

however I am receiving poor download speeds from transmission.

When using the same torrent, tracker and urls in Azures, the download is upto 800Kbps, as I would expect on my line. With transmission its around 50. With other unencrypted clients, the speed is capped to about 50Kbps.

This lends me to believe that transmission is not encrypting the streams.

Azures is very good, but realllly slow.

I am using v1.06(5136) of Transmission. Where is the "force encryption" settings. I can only see one setting on the preferences page relating to "Ignore unencrypted peers" to which I have deselected the option (assuming then it will only use encrypted peers).

The speed is awful.

And yes, the ports are open blah blah otherwise Azures wouldnt be any better !!

Any ideas?

---

