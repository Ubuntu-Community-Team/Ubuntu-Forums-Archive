---
title: "Weird characters displaying - encoding issue?"
date: 2009-03-17
forum: General Help
---

### Post by steenbras on 2009-03-17
Hi - I've noticed that periodically I get a weird character displaying in a firefox web page. An example of such a page is here: [http://www.codinghorror.com/blog/archives/000425.html](http://www.codinghorror.com/blog/archives/000425.html)

I'm attaching a snippet of a screenshot so you can see how it displays in my browser:
[IMG]http://xs137.xs.to/xs137/09122/codinghorror824.png[/IMG]

I don't believe it's just a browser issue, though. If I look at the source, and even do a wget of the resource, looking at the raw text in gedit shows the same character.

How can I change my setting so that I can see the original character?

---

### Post by steenbras on 2009-03-18
Am I the only person experiencing this?

---

### Post by SteveDee on 2009-03-18
> **steenbras said:**
> Am I the only person experiencing this?

No you are not the only person....but its not a Linux/'Buntu problem.

The character shows an ASCII code that is a non-printable character (in your example; 08Hex=backspace). So Firefox displays this as a box with the hex value on both 'buntu and Windows.

IE on Windows displays an empty box, and Opera 10 on Debian just shows a space.

If you want to see what happens with other OS/browser combinations go to: [http://browsershots.org/](http://browsershots.org/)

---

