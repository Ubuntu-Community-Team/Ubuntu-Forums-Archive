---
title: "Libreoffice calc - leading zeros with dec2bin"
date: 2013-12-22
forum: Education &amp; Science
---

### Post by kurja on 2013-12-22
I'm converting a ten base number to two base with =dec2bin() but how do I add leading zeros so I could end up with a distinct n bit number? Like, 0010 instead of 10. Goal is to then merge two of those into an eight bit number, so that 0010 and 0100 would make 00100100, now I'm getting just 100100 which isn't quite the same thing :/

---

### Post by rewyllys on 2013-12-22
You may in fact be getting the eight-bit number you seek; your difficulty may be simply a matter of the format of the cell(s) containing the result.

Try this: In Libre Office, click on Format -> Cells -> Numbers, and then ensure that the "Leading zeroes" option is set to 8.

---

### Post by kurja on 2013-12-22
Increasing number of leading zeroes in cell formatting does nothing for a cell with =DEC2BIN() in it, it seems. I also tried \0000 in the formatting field but that doesn't do anything either :/

That is, both methods give me 0010 if I've typed 10 into that cell, or used =() to a cell with ten base 10 in it, but when I have =DEC2BIN() in either cell I just get 10.

---

### Post by steeldriver on 2013-12-22
There is a second argument to the dec2bin function that sets the number of digits to display e.g.

```

dec2bin(A1,**8**)

```

[ATTACH=CONFIG]248807[/ATTACH]

---

### Post by kurja on 2013-12-22
Yay, that does exactly what I wanted =)

---

