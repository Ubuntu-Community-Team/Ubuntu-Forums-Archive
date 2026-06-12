---
title: "Unable to play DVDs for some reason"
date: 2005-12-30
forum: Desktop Environments
---

### Post by Goober on 2005-12-30
Hello fellow Ubuntonians!  Or Ubunters ... ?

Anyway, I am having a problem with Ubuntu.  Speaking of which, it has been ticking along just grand for over 3 weeks solid, no restart, and no performance issues.  I am extremely impressed.  Anyway, my problem is that I cannot play DVDs in Ubuntu for some reason.  I know for a fact that my DVD rom drive works, and the DVDs work because they play in Windows without a hitch.  Well, as without a hitch as Windows can get.  

Anyway, I am not sure what the problem is.  I usually play them with VLC, but that doesn't work.  I have tried playing DVDs with Realplayer, Oogle, Totem, VLC, MPlayer, Xine and XMMS, and none of them work.  I usually use VLC for it, simply because I have figured it out, but it doesn't even play them.  It is problem something to do with my DVD encoders, something must have gone haywire, but I am not sure what.  Any suggestions?  And yes, Ubuntu recognizes the fact that it is a DVD, and displays it on the desktop and everything.  It just won't play it.

Thanks in advance for your help!

---

### Post by KrazyPenguin on 2005-12-30
You need the codecs which are not included with Ubuntu because of legal reasons.  Search Automatix and install it and it will install everything for you.
Just amazing! ;-)

---

### Post by darth_vector on 2005-12-31
have a read of this:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Goober on 2005-12-31
It works!  I enables some libdvdcss2 thingie or somethinb, not quite sure what, but it works!!!!!

Thank you guys ever so much.  This means that the sole reason I need Windows is to play games in.  If only NFS worked in Linux ...

---

### Post by styven on 2005-12-31
Hi there,

I have a problem with dvds also, i get the following error message............

Error invoking "dvdnav_get_next_block": Error reading from DVD..

I have libdvdread3, and libdvdnav installed.
I am trying to ply with kaffeine and tried to swap engine to xine but the option is not there.

I have kubuntu running on a thinkpad t20. I have had dvds playing before on this machine in xandros after installing libdvdcss2 and using the xine video player.

In xine i had quite a few setting to play with which enabled me to play dvds, but in kaffeine they seem limited.

If it makes any difference i have tried star wars (rots) and empire strikes back.

Happy new year to you all :razz:

---

### Post by styven on 2005-12-31
Hi again,

I had another go and installed gxine, when i try to play  i get the following error message............

(After it has gone through a couple of disclaimers on the dvd)

Xine error message
Read error from: Error reading from DVD

any ideas?

---

### Post by Goober on 2006-01-01
[QUOTE=styven]Hi again,

I had another go and installed gxine, when i try to play  i get the following error message............

(After it has gone through a couple of disclaimers on the dvd)

Xine error message
Read error from: Error reading from DVD

any ideas?[/QUOTE]

I am not 100% sure what my error message, but typing this into a command terminal worked for me.

```
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh


```

Again, not sure if you tried it, but it worked.  

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

The Restrcited Formats page, also linked above, should help you as well.

---

### Post by dima_e on 2006-05-01
Hi all,

I am having a similar problem playing DVDs. I have installed libdvdread3, and tried all the tips in the Restricted Formats page. The DVD icon does show up on the desktop with the correct title, but just behaves like a file folder. Totem does nothing when I select "play movie x" from the movie menu, and oKle shuts down! What else can I try here?

Dima

---

### Post by darth_vector on 2006-05-02
[QUOTE=dima_e]Hi all,

I am having a similar problem playing DVDs. I have installed libdvdread3, and tried all the tips in the Restricted Formats page. The DVD icon does show up on the desktop with the correct title, but just behaves like a file folder. Totem does nothing when I select "play movie x" from the movie menu, and oKle shuts down! What else can I try here?

Dima[/QUOTE]

have a look in the gnome menu -> System -> Preferences -> Removable Drives and Media, click on the Multimedia tab and check the "Video DVD Discs" section. If you tick "play video DVD discs when inserted" and have the command```
totem %d
```then things should work nicely.

---

### Post by Sanderfox on 2006-05-03
I have every possible plugin installed, but still I'm not able to play dvd's very well. Mplayer works most of the time, but mplayer crashes a lot here for some reason. Totem-gst and Xine are both complaining about not having the right plugins installed. Very weird, since I have. Any clue ?

---

### Post by jrei on 2006-06-03
Hi,

had some trouble getting DVDs to run, on my _new_ Thinkpad.

The problem was, that at least the new Thinkpads have no regioncode set within the DVD drive.
You need to 
```

sudo apt-get install regionset

```

an then start the problem, after inserting a DVD.

regionset will tell you if a region is allready set, so you don't have to reset it the code out of the blue. But you should check if you never saw a DVD with your DVD drive you have a good chance that this is your problem.

Be aware that you can only reset the region code 4 times. You find the region code on the DVDs there is a small globe with a number in it. For example germany has the code 2.

Have a nice day, 
Jörn

---

### Post by scpike on 2006-06-27
changing the region with regionset to 1 on an ibm thinkpad t43 finally let me play dvds.. thanks

---

