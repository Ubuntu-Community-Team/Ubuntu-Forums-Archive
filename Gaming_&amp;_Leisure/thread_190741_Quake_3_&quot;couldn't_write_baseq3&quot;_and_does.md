---
title: "Quake 3 &quot;couldn't write baseq3&quot; and doesn't write to normal resolution at exit"
date: 2006-06-06
forum: Gaming &amp; Leisure
---

### Post by huppy on 2006-06-06
I've got quake 3 working in Dapper just fine - it flies along far more efficiently than windows ever did!  Fantastic stuff.  

However, i keep getting messages up in the console area that the game 'couldn't write baseq3'.  I have given read/write/execute permissions to everyone on the hidden .q3a directory in my home, but doesn't seem to have fixed it.  Is there something I have missed?  

The other problem is that when I exit the game, the desktop resolution doesn't return to the default - i.e. what it was before I went into the game.  I'm guessing I may have to change something but am unsure what!  

Any help would be much appreciated.

(sorry the thread title should 'return' to normal resolution on exit)

---

### Post by huppy on 2006-06-07
Ok, an update, i fixed the "couldn't write baseq3" problem by giving myself ownership of the hidden .q3a directory. 

However, I am still getting the problem that when I quit the screen resolution doesn't go back to what it was.  The error message is:  

X Error of failed request: BadValue (integer parameter out of range for operation)
Major opcode of failed request: 135
Minor opcode of failed request: 10
Serial number of failed request: 95

It has me baffled, any ideas?

---

### Post by matva on 2006-06-07
[QUOTE=huppy]Ok, an update, i fixed the "couldn't write baseq3" problem by giving myself ownership of the hidden .q3a directory. 

However, I am still getting the problem that when I quit the screen resolution doesn't go back to what it was.  The error message is:  

X Error of failed request: BadValue (integer parameter out of range for operation)
Major opcode of failed request: 135
Minor opcode of failed request: 10
Serial number of failed request: 95

It has me baffled, any ideas?[/QUOTE]

edit your xorg.conf so that it only has two resolutions, 1 what you game at, the 2nd what you want your desktop at. just # out the others.

that worked for me.

---

