---
title: "dmesg on desktop howto?"
date: 2005-01-31
forum: Desktop Environments
---

### Post by buellman on 2005-01-31
hi!

one little question: how do i get dmesg on my desktop-background? maybe this sort of question was asked before but i didn't found an answer on it :-/
system: warty+gnome (what else? ;-))

thanks for any hints.
greets. buellman

ps: im from germany so my english maybe is not  good enough to understand what i want so here is an example of what i mean:
[http://thilockdominus.freehomepage.com/images/november.jpg](http://thilockdominus.freehomepage.com/images/november.jpg)
is that "just" e-term without borders?

---

### Post by jerrynew2linux on 2005-01-31
[QUOTE=buellman]hi!

greets. buellman

ps: im from germany so my english maybe is not  good enough to understand what i want so here is an example of what i mean:
[http://thilockdominus.freehomepage.com/images/november.jpg](http://thilockdominus.freehomepage.com/images/november.jpg)
is that "just" e-term without borders?[/QUOTE]

Ich habe keine Antwort fuer Dich, aber ich wuensche unser Deutsch waere so *schlecht* wie Dein Englisch

---

### Post by valadil on 2005-01-31
Yes, that is a term without window manager borders.  I don't know how to tell gnome to ditch borders, so I use Terminal from os-cillation.com

---

### Post by buellman on 2005-02-01
hi!

@jerrynew2linux: danke fürs kompliment ;-)

@valadil: hmmm... i thought something like that. but thanks anyway.

gretts. buellman

---

### Post by friez on 2005-02-05
no that is not an open terminal  :-? 
it 's Torsmo [http://torsmo.sourceforge.net/](http://) it can also be done with gdesklets and Karamba/superKaramba

edit : ok maybe it is  :-#

---

### Post by Perfect Storm on 2005-02-05
W00t! that's one of my screenshots!  :D


```

Eterm -x -0 --trans --buttonbar 0 --scrollbar=off
```

Or you want to start up in a specific place and size.

```

Eterm x -0 --trans --buttonbar 0 --scrollbar=off --geometry=85x23+759+610 -f orange &
```

No need for explaination. I think it's obvious what the diffrent command does. You change it as you pleased.

---

### Post by buellman on 2005-02-20
hi artificial intelligence!

thanks for your help  :grin: 
your desktop looks pretty cool.

greets. buellman

---

### Post by wallijonn on 2005-02-21
Friez,

Your [http://torsmo.sourceforge.net/](http://torsmo.sourceforge.net/) link comes up as [http:///](http:///)

because your code is [http://torsmo.sourceforge.net/](http://) and not 

[TORSMO](http://torsmo.sourceforge.net) or [http:///torsmo.sourceforge.net](http:///torsmo.sourceforge.net)

You are going to have to do a "quote" of this message to see what the code looks like.

---

### Post by piedamaro on 2005-02-21
Also you can have colored output using grc. (like CONNECT message in red, etc.)

[http://melkor.dnp.fmph.uniba.sk/~garabik/grc.html](http://melkor.dnp.fmph.uniba.sk/~garabik/grc.html)

---

### Post by vassalle on 2005-03-14
[QUOTE=Artificial Intelligence]W00t! that's one of my screenshots!  :D


```

Eterm -x -0 --trans --buttonbar 0 --scrollbar=off
```

Or you want to start up in a specific place and size.

```

Eterm x -0 --trans --buttonbar 0 --scrollbar=off --geometry=85x23+759+610 -f orange &
```

No need for explaination. I think it's obvious what the diffrent command does. You change it as you pleased.[/QUOTE]
 how do i change it in the preferred application option ? cant seem to make it happen.. i tried putting the options under exec, but it just won't start eterm the way i want it too.. some help please.. thanks! ;)

---

