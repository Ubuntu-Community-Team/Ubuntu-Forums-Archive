---
title: "Emerald theme"
date: 2009-01-03
forum: General Help
---

### Post by stmartin on 2009-01-03
I downloaded few .emerald themes. How to apply them to my Ubuntu 8.04? I got Emerald Manager + Compiz Fusion.

Thanks in advance.

---

### Post by HungryMan on 2009-01-03
I think you can drag and drop them to emerald theme manager.
There also is an "Add Theme" button there.

---

### Post by stmartin on 2009-01-03
> **HungryMan said:**
> I think you can drag and drop them to emerald theme manager.
There also is an "Add Theme" button there.

What to do with the emerald theme manager? I want to apply it to my system?

---

### Post by jocko on 2009-01-03
> **stmartin said:**
> What to do with the emerald theme manager? I want to apply it to my system?
Just click the "import" button and browse to the theme you want to import.
Then select the theme you want to apply in the theme manager. You may need to restart emerald to reload the theme. Just press Alt+F2 and type "emerald --replace".

---

### Post by stmartin on 2009-01-03
Again, not working . What' s the prob?

---

### Post by Tom--d on 2009-01-03
To use emerald.

Press ALT+F2 and type in emerald --replace

There is your Emerald :D

OR:

Go into CCSM and under Window Decorations, change the command to emerald --replace

---

### Post by stmartin on 2009-01-03
Again, didn't work. What's the prob? Should I reinstall Emerald and how?

---

### Post by linux_tech on 2009-01-03
There is a easy to follow guide here
[http://hacktivision.com/index.php/2008/06/07/how-to-enhance-ubuntu-8-04-hardy-heron-e?blog=2](http://hacktivision.com/index.php/2008/06/07/how-to-enhance-ubuntu-8-04-hardy-heron-e?blog=2)

Does ```
emerald --replace 
``` in terminal work?
If it does then go into ccsm and under window decoration > then 
emerald --replace

If that command does not work, then you may want to  reinstall compiz, Advanced Desktop Effects Settings, gnome manager

---

### Post by stmartin on 2009-01-03
I solve it. The problem was that in the Appearence, in the Visual Effects tab, there was None selected :D. Now I selected it to Normal, and it works. Thanks for the help.

---

