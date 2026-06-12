---
title: "Xpdf wants to be blue?"
date: 2005-12-25
forum: General Help
---

### Post by kaamos on 2005-12-25
Hello!

I'm running xfce on an old machine and I use xpdf for reading pdf files. The problem is.. that it's just damn ugly. Don't get me wrong, gtk1 apps are no eyecandy, but xpdf has decided to be blue. And other gtk1 apps like xmms are fine. See screenshot.

Any ideas on this? Is this a xfce or a xpfd thing?
Thanks!

---

### Post by The Warlock on 2005-12-25
[QUOTE=kaamos]Hello!

I'm running xfce on an old machine and I use xpdf for reading pdf files. The problem is.. that it's just damn ugly. Don't get me wrong, gtk1 apps are no eyecandy, but xpdf has decided to be blue. And other gtk1 apps like xmms are fine. See screenshot.

Any ideas on this? Is this a xfce or a xpfd thing?
Thanks![/QUOTE]
Try evince instead. It's really quite nice.

---

### Post by kaamos on 2005-12-25
Evince is brilliant, I have it embedded to firefox on my laptop. However this dell pos is so old that even evince takes a bit too long to start.. :(

---

### Post by The Warlock on 2005-12-25
[QUOTE=kaamos]Evince is brilliant, I have it embedded to firefox on my laptop. However this dell pos is so old that even evince takes a bit too long to start.. :([/QUOTE]
Hmm. Have you tried gpdf? It's essentially just a GTK+ version of xpdf.

---

### Post by kaamos on 2005-12-25
I'll try that, thanks for the suggestion!

---

### Post by markovuc on 2006-01-04
I find evince very usefull, because it is small and fast. I tried to use evince and gpdf, but was not happy because of the amount of resources they take.
I don't like the new blue colour of xpdf too, maybe some tweaking with xresources would help? I would appreciate any suggestion.

---

### Post by markovuc on 2006-01-04
I just found (thanks to google and man pages) that adding the line:

xpdf*Background: gray

to ~/.Xresources file will change the colour back to gray.
There is also one interesting resource for people that use vi(m):

xpdf.viKeys: true

"Enables the &#180;h&#8217;, &#180;l&#8217;, &#180;k&#8217; and &#180;j&#8217; keys for left, right, up, and down scrolling." (quote from man page)

"How to use X RESOURCES" page:

[http://web.mit.edu/answers/xwindows/xwindows_resources.html](http://web.mit.edu/answers/xwindows/xwindows_resources.html)

---

