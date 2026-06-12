---
title: "xboard custom colors"
date: 2005-11-20
forum: Gaming &amp; Leisure
---

### Post by tedddee on 2005-11-20
I'm trying to set custom colors with xboard via the cmd line.  Something like this.

[IMG]http://www.edcollins.com/chess/winboard27.gif[/IMG]
/whitePieceColor=#ffffff
/blackPieceColor=#1d1d1d
/lightSquareColor=#c0c0c0
/darkSquareColor=#0080c0

I was able to get the example color scheme working from [this man page]("http://linuxcommand.org/man_pages/xboard6.html") with the following command.

xboard -size medium -whitePieceColor gray100 -blackPieceColor gray0 -lightSquareColor gray80 -darkSquareColor gray60 -highlightSquareColor gray100 -premoveHighlightColor gray70

However when I try and enter in the colors from above it does not work. :mad: 

Warning: Color name "ffffff" is not defined
and if I use #ffffff the game doesn't even start, just lists out --help

Anyone know how to go do this the right way?  A .conf file somewhere?

---

### Post by ryu kun on 2006-12-25
it's explained in this post: [http://ubuntuforums.org/showpost.php?p=219066&postcount=22]("http://ubuntuforums.org/showpost.php?p=219066&postcount=22")

also check out this page: [http://vico.kleinplanet.de/xboard.html]("http://vico.kleinplanet.de/xboard.html")

---

