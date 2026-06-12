---
title: "Showing escape codes with watch"
date: 2009-01-05
forum: General Help
---

### Post by zen_cat on 2009-01-05
Hi all,

I'm trying to write a script that will function as a console system monitor on one of the screens I keep open on the command line (with screen). This bit of it is all fine, but I want to include escape codes in the text to colourize it for readability. 

When I activate the script using the watch command, these escape codes are then stripped out. Watch's man page says to use cat -v to see them, but I think that might be for a different purpose, given the garbled text that comes out.

Am I just going to need to put a loop into the script, or is there a way to get the colourization back using watch and something else?


Rafe

PS: Does anyone else have a similar script I could look at; I'm doing this mostly to teach myself about the commands.

PPS: Can anyone recommend any good command line programs that I might not be using (other than ssh, etc) - currently I'm using irssi, rtorrent, mc, and w3m.

---

