---
title: "Compiz/Desktop Effects Autostart"
date: 2010-11-25
forum: Desktop Environments
---

### Post by sumski on 2010-11-25
Hi!
Can anyone tell me how does Ubuntu start it's desktop effects automatically?
I'm currently using Maverick , and i installed Compiz 0.9.2 from WebUpd8 PPA, and it runs automatically when gnome session starts( I know where and how they are enabled from GUI), but i'm wondering is there "ubuntus" entry anywhere in gconf , or anywhere else that starts them?

I ask this because my primary OS is Debian Sid , and i would like to aply the same mechanism on that machine, because there i can't turn on 0.9.2 with fusion-icon , and i **don't wannt **to bother with  compiz --replace ,etc...

---

### Post by koleoptero on 2010-11-25
I don't know how ubuntu does it, but you could just create launchers in ~/.config/autostart with "compiz --replace" and whatever else you need to autostart.

---

### Post by pholden on 2010-11-25
Similar to the reply above - you can also create a new startup entry in *System > Preferences > Startup Applications*, as described [here]("http://ubuntuforums.org/showpost.php?p=10161197&postcount=6").

---

### Post by sumski on 2010-11-26
with the "--replace" command it doesn't work for me , it says "no suitable decorator found"

and there isn't emerald for 0.9.2 , at least packaged as .deb, and my previous attempts to compile emerald always failed :(

so, does anybody know what mechanism ubuntu uses for starting compiz?

---

### Post by dzon65 on 2010-11-26
Have you tried installing the fusion icon and adding it to your startup sessions? When you shutdown your rig in a compiz session, it should then automatically start in compiz.
Small edit:If you're not using emerald,set the window decorator to gtk when rightclicking the fusion icon.

---

### Post by sumski on 2010-11-26
> **dzon65 said:**
> Have you tried installing the fusion icon and adding it to your startup sessions? When you shutdown your rig in a compiz session, it should then automatically start in compiz.
Small edit:If you're not using emerald,set the window decorator to gtk when rightclicking the fusion icon.

i can handle compiz 0.8.x + fusion-icon/--replace command , but compiz 0.9.2 + Debian Sid can't handle fusion-icon/--replace command/emerald

i know it's "experimental" version of compiz , but on maverick it starts just fine , **without** fusion-icon , --replace commands and emerald

---

### Post by dzon65 on 2010-11-26
My bad,forgot the debian part.

---

### Post by dzon65 on 2010-11-26
Maybe this helps:[http://www.webupd8.org/2010/11/install-compiz-0921-in-ubuntu-1010.html](http://www.webupd8.org/2010/11/install-compiz-0921-in-ubuntu-1010.html)
And this:[http://forums.debian.net/viewtopic.php?t=16786](http://forums.debian.net/viewtopic.php?t=16786)

---

### Post by sumski on 2010-11-26
thanks for trying to help :p

again:

on Sid , and Maverick/Lucid with compiz 0.8.x and fusion-icon everything runs fine , and **i'm familiar** with "traditional" ways of starting compiz , e.g. f-i, replace command and autostarting them
 
    with 0.9.2 things are different - the "traditional" ways of starting compiz on Sid **are not **working , but on Maverick 0.9.2 it starts automatically **,i don't have **to run fusion-icon and --replace command that's why i'm asking **how does ubuntu starts it's desktop effects?**

---

### Post by dzon65 on 2010-11-26
You didn't read all the way down. You can compile emerald from git. That way compiz will recognize a decorator.

---

### Post by sumski on 2010-11-26
your'e right , i haven't read all the way down ,and now that i have read all the way down i didn't found any comment about compiling emerald

2 things about that: 1. i don't really like emerald:p, i prefer gtk-window-decorator, and 2. i tried compiling both 0.8.4 and 0.9 emerald , and both attempts failed :-( ; i found there was bug reported on gentoo forums, and they have a patch. i have applyed that patch, however i didn't work for me, for not sure what reason 


p.s.
sorry for bad grammar/spelling :p

---

