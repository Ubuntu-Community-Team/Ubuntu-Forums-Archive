---
title: "unistall ie7 from ubuntu 8.04"
date: 2009-02-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by anujdwivedi on 2009-02-11
Hi...

I am very new to unbuntu 8.04

I have installed IE7 but now I don't need it. I unable to install it.

Can anyone help me please ?

Thanks in advance

anuj:

confused:

---

### Post by x33a on 2009-02-11
did you install it through wine?

---

### Post by anujdwivedi on 2009-02-11
not through wine. I have installed through terminal. 

I have followed the steps from following website:

[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

---

### Post by x33a on 2009-02-11
see this:

[http://www.tatanka.com.br/ies4linux/page/Uninstall](http://www.tatanka.com.br/ies4linux/page/Uninstall)

---

### Post by anujdwivedi on 2009-02-11
yeah that's fine but I want to uninstall, removing files may cuase any problem?
:confused:

---

### Post by x33a on 2009-02-11
as stated on their website, there is no uninstall procedure other than this. so this will not cause any problem.

1. go to your home folder and delete .ies4linux folder.
2. look under /bin or /usr/bin and see for any ies4linux file and delete it.
3. delete any desktop shortcuts.

---

### Post by howlingmadhowie on 2009-02-11
i think you just have to be careful to delete the right things in your ~/bin directory, although it probably only has the ie7 stuff in it.

---

### Post by howlingmadhowie on 2009-02-11
> **x33a said:**
> as stated on their website, there is no uninstall procedure other than this. so this will not cause any problem.

1. go to your home folder and delete .ies4linux folde.
2. look under /bin or /usr/bin and see for any ies4linux file and delte it.
3. delete any desktop shortcuts.

i think the ies4linux scripts install ie to $HOME/bin, not to any other location.

---

### Post by anujdwivedi on 2009-02-11
Thanx a ton! my friends .... I have done it:lolflag:

---

