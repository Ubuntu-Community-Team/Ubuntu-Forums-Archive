---
title: "VLC no more gtk2?"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Tasu on 2005-10-13
Hi All,

Well, what happend to the vlc package? I've just upgraded and the new wxvlc seems to depend on libgtk1.2... uhm! Will it be restored to the more appealing wxwidgets2.6, or the freeze after Breezy was released will prevents vlc further upgrades? (why upgrading it to a  beta version just before the release of Breezy? 0.8.2 wasn't good enough?)

kisses
Tasu

---

### Post by kent on 2005-10-13
Yeah, I was also surprised by this.

---

### Post by Tasu on 2005-10-13
Wow, looked around the forum, there's a big thread (8 pages O_O [http://ubuntuforums.org/showthread.php?t=74308&highlight=vlc](http://ubuntuforums.org/showthread.php?t=74308&highlight=vlc)) about this, it looks like some stormy thingy happend to vlc, because it depends on some multiverse packages, it was repackaged to support only free codecs, after that a bit of discussion went on (a lot of people wasn't so happy about that! ~_^) and it seems that the package was finally fixed (now I will try mine, if it can play DVDs and divx...), but with a dependency on the old libgtk1.2... (and I can't understand why O_O), anyone can tell us if vlc will depend soon on gtk2 again? Thanks... I know that interface ain't as important as features, but I think it's still important for the integration in the OS look and feel (providing it was already well integrated before last update)! ^_^

Bye... kisses
il Tasu! ^_^

---

### Post by nkessler2000 on 2005-10-14
That's pretty unfortunate. VLC is the only video player I really like for any OS (I use it on windows, linux, and mac). It's not a huge deal, but it is distracting having VLC's interface in Breezy look so old and busted. Are there any plans to fix this, or are we just going to have to wait until 6.04?

---

### Post by deeek on 2005-10-14
Or you can revert back to the old 0.8.2 version.  ;)


[www.umsl.edu/~dmwkt7/vlc_0.8.2-1ubuntu3_i386.deb]("http://www.umsl.edu/~dmwkt7/vlc_0.8.2-1ubuntu3_i386.deb")
[www.umsl.edu/~dmwkt7/wxvlc_0.8.2-1ubuntu3_i386.deb]("http://www.umsl.edu/~dmwkt7/wxvlc_0.8.2-1ubuntu3_i386.deb")

---

### Post by nehalem on 2005-10-14
I was also very upset to see this.  It looks terrible.

---

### Post by kingsidy on 2005-10-14
same here. i reverted back to version 0.82. the new one is crap

---

### Post by Tasu on 2005-10-14
Good, thanks for the old packages, now I would like to try packaging the nightly builds for ubuntu (the one found listed on that thread mentioned before, are just for Debian... dbus-1 dependency... among other things..)... 0_0 ... But is there a way to let devs know that the idea stated on that thread was really good, I mean the idea to put all vlc stuff in multiverse... ain't multiverse some kind of non-US repo? all right, I think that this could do the trick, multiverse is stated as non-free and possibly law infringing repo, at least in US... thus is up to people's choice to download softwares up there.... 

cheeres
il tasu

---

### Post by Raptor Ramjet on 2005-10-19
Well I hate to say it but...

Whilst I'm not keen on most of the "brokenly upgraded" interface I much prefer the "old fashioned" file selection dialogue it has to the new Gnome one.

So whilst I'd like to see VLC get a nicer interface I'd vote to keep this "old style"  file selector 'cause it's so much simpler.  All I ever do in the new Gnome one is press "Ctrl & L" and type in the full file name - with a little help from autocomplete (This saves me wondering how the rest of the interface is going to behave this week :))

---

### Post by Grey on 2005-10-19
About a month or so ago, I built my own VLC from source, so that I could get VC1 (WMV9) support.  If it's of any use to anyone, you can get the package I built [here](people.uleth.ca/~dave.brady/vlc-with-vc1.deb).  The naming system is kinda messed, but it plays everything I've thrown at it, and uses GTK2.  The deb was compiled on a laptop with 686 kernel and Centrino CPU.  It installed fine on my desktop, which has a K8 CPU, and runs 32-bit Ubuntu.

I REALLY wish that Ubuntu wasn't so American-centric... and would give us a distro that wasn't so hamstrung by default.

---

### Post by madjo on 2005-10-26
American-centric? from South Africa?

---

### Post by Kyral on 2005-10-26
[http://www.ubuntuforums.org/showthread.php?t=82025](http://www.ubuntuforums.org/showthread.php?t=82025)

I think that package will be of most interest to you

---

### Post by angrykeyboarder on 2005-10-26
[quote=madjo]American-centric? from South Africa?[/quote]

Ubuntu hails from the UK, not South Africa.

---

