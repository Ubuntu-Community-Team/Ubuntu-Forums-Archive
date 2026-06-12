---
title: "Compiz active window header is goofy"
date: 2008-12-18
forum: General Help
---

### Post by Niels Olson on 2008-12-18
If I roll over the window header buttons (min, max, close) in the active window, and then roll off those buttons, the window header goes goofy. I did not have this problem in 8.04, but now I have the same issue on both of my computers running ubuntu 8.10, a Dell Latitude D820, and a Dell Inspiron 9300. Appreciate any help . . .

[IMG]http://nielsolson.us/images/Screenshot.png[/IMG]

---

### Post by ellalan on 2008-12-18
Could you try the Emerald window decorator and see whether it makes any difference.

---

### Post by Niels Olson on 2008-12-18
No problem in Emerald, except I can't find an exact replica of the Human theme. That, and it doesn't really fix the problem with the GTK window decorator . . .

---

### Post by Brian Vaughan on 2008-12-18
It's an issue with Nvidia drivers. It's supposed to be fixed in the 180 series driver, but that's still in beta testing. You could try using an older video driver, such as the 96 series driver, but that will have other shortcomings. Most likely, your best bet is to switch the visual effects setting to 'None,' and wait for the driver upgrade.

---

### Post by Niels Olson on 2008-12-18
Brian, very interesting . . . question: how does one find out about such things besides the Ubuntu forum?

---

### Post by bushd on 2008-12-18
I had the same issue.  Use Compiz with Emerald.  Emerald has some nice themes but that human theme isn't really available.  Gnome-look is a good place to start.

---

### Post by Niels Olson on 2008-12-18
actually, I finally found two very good Human clones on beryl-project.org, buried in the third and fourth pages of their Ubuntu themes: [Human-Glass]("http://themes.beryl-project.org/theme_details.php?id=97"), and [ubuntu-humanlooks]("http://themes.beryl-project.org/theme_details.php?id=19")

---

