---
title: "PCF Font woes"
date: 2007-10-26
forum: Desktop Environments
---

### Post by casperlingus on 2007-10-26
I have spent hours trying to get this pcf font installed in Gutsy.  It's impossible.  I've been through all the HowTo's, executed dpkg-reconfigure fontconfig(-config) thousands of times, fc-cache -v -f thousands of times, I have enabled bitmapped fonts and copied vga.pcf and vga.pcf.gz all over the place, and tried everything all over again.  I've opened "fonts:///" in nautilus and dragged them in there to find it overwrites the fonts in my ~/.fonts dir to zero size effectively destroying them.  What???  No matter what I do, I cannot get this font installed.

ARGH!  Why is this so difficult?  I opened fontforge and font looks fine in there, but I can't figure out how to convert it to ttf, and I don't even know if I could get it to work if I succeed to get it to ttf.  There MUST be an easier way.  Someone please tell me there's an easier way.  I can't believe I've wasted so much of my day doing this.

You can download the font from the following location to try them yourself (I don't know whether to use pcf or pcf.gz):
[http://66.16.6.172/share/vga.pcf](http://66.16.6.172/share/vga.pcf)
[http://66.16.6.172/share/vga.pcf.gz](http://66.16.6.172/share/vga.pcf.gz)

Why is there not an easier way to do this??  Can anyone get them to work???
:mad:

---

### Post by casperlingus on 2007-10-27
I apologize.  I'm not usually one to freak out about something like this.  But I was appalled at how difficult this is.  I edited out the angry language in my previous post.  Maybe someone will help me now...?  :-)

Bump.

-Casper

---

### Post by jbo5112 on 2007-12-05
Sorry for being of no help, but I want to bump this problem back up in the forums.  You'd think with all the places I'm finding the problem, dating back to at least 6.06, someone would have fixed this or at least provided a detailed solution.

I use the konsole bitmap fonts a ton for work, making them almost necessary, since I need to be able to quickly scan large amounts of data.  I was thinking of switching from Gentoo to Ubuntu with my new computer, but little things like this are making Ubuntu harder to set up than Gentoo!  Now, I'm contemplating going back to Gentoo on my office workstation.

---

### Post by jbo5112 on 2007-12-05
I just got mine installed.  It could be the options you chose when running 'dpkg-reconfigure fontconfig-config'

Previously I had run these (and most of the commands below), and restarted the x server at various points along the way

1) place fonts under ~/.fonts
2) 'sudo apt-get install xfs'
3) 'xset fp+ ~/.fonts'
4) 'xset fp rehash'

Here's what I did:

1) 'sudo dpkg-reconfigure fontconfig-config'
Chose: Autohinter, Automatic, Yes
2) 'sudo dpkg-reconfigure fontconfig'
3) 'fc-cache -f -v'
4) restart x server

It's probably not necessary to run all of that, but I shouldn't have to run any of it.  The OS should already be set up to use something as useful as bitmapped fonts.  It should also let me play DVD's, but that's another rant for another place.  Still, it didn't work with the vga font for me, but let me know if any of this helps.

---

