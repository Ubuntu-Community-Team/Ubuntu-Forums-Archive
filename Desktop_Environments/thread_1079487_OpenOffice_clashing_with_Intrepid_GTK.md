---
title: "OpenOffice clashing with Intrepid GTK"
date: 2009-02-24
forum: Desktop Environments
---

### Post by cjohn106 on 2009-02-24
Hi I am using a dark GTK theme for Ubuntu 8.10 but Openoffice org doesnt work well with it, all the of the text is black and virtually invisible. I tried various configurations but as its hard to see exactly what I am changing, I'm stuck. Here is a picture. You can see all the dark text, I'd like it to be white or anything other than black. How do I change this?

---

### Post by Vadi on 2009-02-24
You can't. OOo isn't a native gtk+ app, it's a java one that tries to imiate the gtk look - doesn't work out well always and as you see in your case, quite horrible.

Give [Abiword]("apt:abiword") a try - it's a gtk+ text editor, pretty decent to use actually.

---

### Post by cjohn106 on 2009-02-24
I've seen modifications that go along with dark gtk's like this: [http://www.rebelzero.com/wp-content/uploads/2008/09/ooo_darktheme_default.png](http://www.rebelzero.com/wp-content/uploads/2008/09/ooo_darktheme_default.png)

---

### Post by puffcorn on 2009-03-15
> **Vadi said:**
> You can't. OOo isn't a native gtk+ app, it's a java one that tries to imiate the gtk look - doesn't work out well always and as you see in your case, quite horrible.

Give [Abiword]("apt:abiword") a try - it's a gtk+ text editor, pretty decent to use actually.

Abiword is a great alternative.

One problem, though, is when I have desktop effects enabled, the text is invisible...  (anyone know how to change that?)

---

### Post by Vadi on 2009-03-15
Can you show a screenshot?

---

### Post by puffcorn on 2009-03-16
Abiword **without** desktop effects:

[IMG]http://img.photobucket.com/albums/v458/silvercenturion/screen-wo.png[/IMG]

Abiword **with** desktop effects (Normal) enabled:

[IMG]http://img.photobucket.com/albums/v458/silvercenturion/screen-w.png[/IMG]

---

### Post by Vadi on 2009-03-16
> **puffcorn said:**
> Abiword **without** desktop effects:

[IMG]http://img.photobucket.com/albums/v458/silvercenturion/screen-wo.png[/IMG]

Abiword **with** desktop effects (Normal) enabled:

[IMG]http://img.photobucket.com/albums/v458/silvercenturion/screen-w.png[/IMG]

Compiz people think this is a graphics driver bug, but to be sure, they need more info.

Can you attach your [http://ubuntuforums.org/showpost.php?p=6906805&postcount=6](http://ubuntuforums.org/showpost.php?p=6906805&postcount=6) file, along with the output of the *glxinfo* command?

---

### Post by puffcorn on 2009-03-16
here's the link for glxinfo output:
[http://www.mediafire.com/?sharekey=d5db8fed6558ff99d0d290dca69ceb5ce04e75f6e8ebb871]("http://www.mediafire.com/?sharekey=d5db8fed6558ff99d0d290dca69ceb5ce04e75f6e8ebb871")
(text file; too large to attach it here)

and the link for the abiword file:
[http://www.mediafire.com/?sharekey=d5db8fed6558ff99d0d290dca69ceb5cd69c6691e0ded14e5621d66e282a0ee8]("http://www.mediafire.com/?sharekey=d5db8fed6558ff99d0d290dca69ceb5cd69c6691e0ded14e5621d66e282a0ee8")
(.abw file; can't attach them, so did it this way)

(if this isn't exactly what you were looking for, let me know--and thanks for your help)

---

### Post by Crowder on 2009-04-23
hey guys, I'm having this same problem, but with a different theme. Mine is at least legible, but annoying nonetheless. 

Isn't there just some way to suppress the GTK+ theming for certain apps, and just set it to human or something?

---

### Post by Crowder on 2009-04-23
Hey, I think I actually solved this! Unless you're all talking about something else...

I just went into Tools --> Options ---> OpenOffice.org ---> Appearance and literally only changed two things to suit my needs. It's actually really simple:

Under general, change background from "automatic" to white, or whatever you prefer. Do the same for font color(to black), and you're all set.

Well, that's the first time I ever ended up being the one to give the answers, so I am more than a little suspicious that there's more to it for you. Still, hope this solves your problem!

---

### Post by Vadi on 2009-04-23
Thanks, that does help a bit.

---

