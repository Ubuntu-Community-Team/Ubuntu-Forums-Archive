---
title: "Hex Editor for Gnome"
date: 2010-02-21
forum: Desktop Environments
---

### Post by pi/roman on 2010-02-21
I am looking for a gui hex editor for gnome. I have tried both GHex and Bless and they both look very similar but they do not provide all the options I want.  Does anyone have any suggestions for a powerful hex editor I can use in gnome? Thanx.

---

### Post by SecretCode on 2010-02-21
I've been meaning to try out wxHexEditor from getdeb.net.

What features do you need that are not in GHex?

---

### Post by pi/roman on 2010-02-21
I've become a bit spoiled by some of the features in M$ editors. Even the opensource ones are more rich in features. Many of them have options to change colors of text and backgrounds and some even allow you to change the shade of the offset based on it's value which is a very nice feature for eyeballing the code. Some of them have more options for checksum configuration while the gnome editors both offer the same little endian and big endian options. Some have options for grouping the offsets by two's or four's and changing the output text but they all seem to have something extra to offer. Basically I would be interested in any hex editor with any extra features rather than just the bland get the job done type like these two.

---

### Post by pi/roman on 2010-02-21
wxHexEditor does look promising but when I try to run it noting happens except I get an empty file with a name that looks like this:
x&#65533;S@@8@@@ (invalid encoding)

I'm going to try to make it work.

I'm guessing maybe I have to install some libraries but not sure which one.

---

### Post by pi/roman on 2010-02-21
Ok i got this installed by using the getdeb package here:
[[COLOR=Blue]http://www.getdeb.net/software/wxHexEditor[/COLOR]]("http://www.getdeb.net/software/wxHexEditor")
I first had to install the getdeb installer here:
[[COLOR=Blue]http://www.getdeb.net/updates/Ubuntu/all#how_to_install[/COLOR]]("http://www.getdeb.net/updates/Ubuntu/all#how_to_install")

My first impression is that it has a nice search feature in the toolbar where you can search for text or hex and replace it too.  Other than that I don't notice a whole lot of other cool features.  One problem I see is that when getting the checksum on a selection, if the selection ends at a zero byte the all of the checksums change to zero (see screenshot).

---

### Post by puppywhacker on 2010-02-21
I have been praying and waiting for UltraEdit on linux. I'm using the windows version a lot in the office, so I bought the $50 shareware license as soon as I could, although they offer a month of trial period. The hexeditor is maybe not the main feature but it works well, and it searches replaces. The current version 1.1.0.0 is still lacking a few features the windows version has, but it is still the best texteditor. I normally don't plug software like this, but they saved my live a couple of times =)

---

### Post by pi/roman on 2010-02-21
I've looked at the checksums again in Ghex and Bless and it looks like they all use the same checksum engine.  If the last byte is zero then they print out the checksum as zero.  Surely that can't be the right way to calculate it because it would cause way too many to report as zero.  I took screenshots of this problem and will attach them.
So basically if anyone knows of an editor that doesn't calculate zero checksums like this I would be interested.

---

### Post by erdem_a on 2010-02-22
> **pi/roman said:**
> I've looked at the checksums again in Ghex and Bless and it looks like they all use the same checksum engine.  If the last byte is zero then they print out the checksum as zero.  Surely that can't be the right way to calculate it because it would cause way too many to report as zero.  I took screenshots of this problem and will attach them.
So basically if anyone knows of an editor that doesn't calculate zero checksums like this I would be interested.

Hi, this is [wxHexEditor]("http://wxhexeditor.sourceforge.net")'s author.
As I can see at other hex editors, those outputs are perfectly normal. Data interpretations (I think you call this as "checksum", which reminds me CRC like functions ) are calculated by "cursor location" NOT by selection. It's default behavior of all hex editors that I use.
Tip: If you make that selection from end to beginning, you see what you want :)

@roman Do you find an error at my prog? You have better to report that bug at tracker :). Because I can open every file & device with it. I think you needed to compile that wxhexeditor from source. You can use "static compiled tarballs" too. Because there is no libwxgtk-dev > 2.8.9 for ubuntu at OpenSUSE compile farm, I cannot compile this app for ubuntu yet. I will try to put deb packages those compiled with 9.10 until weekend.

the program that I made alone, for myself. If you require some options, than you can feedback via "tracker" at the sf.net and I can think on them and implement them later If I can. 

Thanks.

---

### Post by pi/roman on 2010-02-22
erdem_a, thanks for your response. It's not very often I have the chance to speak with the developer of a piece of software I use.  I was able to install wxHexEditor by a package installer from getdeb successfully as SecretCode suggested. It ran well for me and I found no errors with it.  I can see now as you explained how the checksum is being calculated and that it is not actually on the selection.  I guess getting a checksum on selection is one of the feedback requests that I would make but I would not want to sound to demanding as the software has been provided for free and I do appreciate that.

---

### Post by pi/roman on 2010-03-13
I'm using HxD through Wine now and it seems to work pretty well so I'll mark this as solved.

---

