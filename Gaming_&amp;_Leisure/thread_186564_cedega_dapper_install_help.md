---
title: "cedega dapper install help"
date: 2006-06-02
forum: Gaming &amp; Leisure
---

### Post by bobbymcsteels on 2006-06-02
ok tried to pitch this on the cedega website but still no answers.... kinda, but I;m trying to install the cedega deb from the site but get an error bout xlibs not used because xkeyboard is being used instead. This is the solution someone else has tried but not sure how to do it "The solution is to download a old package of xlibs for Ubuntu Breezy".
Any help would be great
Cheers

---

### Post by Perfect Storm on 2006-06-02
Or you could do this - [http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63)

---

### Post by bobbymcsteels on 2006-06-02
Excellent, thanx for that... just need to install my nvidia 6600gt drivers which I cant find then I will be happy.

---

### Post by Perfect Storm on 2006-06-02
Tried with the latest driver?
I also have 6600GT x8 agp annd the default nvidia driver from that you can install thtrough apt-get works well with it.

---

### Post by bobbymcsteels on 2006-06-02
yeah just installed it.... took a while tho, poofyhairguy did a how to, just followed that and sorted... just had madden 03 running really fast tho](*,)

---

### Post by stimpack on 2006-06-02
I had the same problem, thanks for the link AI, worked great.

---

### Post by PriceChild on 2006-06-02
I had the same problem.. another work around is to alien the package and then install the resultant deb.

pricey

---

### Post by bobbymcsteels on 2006-06-02
[QUOTE=PriceChild]I had the same problem.. another work around is to alien the package and then install the resultant deb.

pricey[/QUOTE]

I tried that one and still didnt work.

---

### Post by handy on 2006-06-03
[QUOTE=Artificial Intelligence]Or you could do this - [http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63)[/QUOTE]

Thanks **again** AI, that worked perfectly! :KS

---

### Post by PsYsK8eR on 2006-06-17
[QUOTE=Artificial Intelligence]Or you could do this - [http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63)[/QUOTE]

The problem is, this is a workaround that is time consuming, because everytime a ".deb" package is missing "xlibs" you'll have to edit the package.

In dapper (ubuntu 6.06) "xlibs" changed (renamed), and it cannot be recognized by (older) ".deb" installation packages, making it impossible to install one of those packages.

The solution to this is installing a "dummy package", which i have attached to this reply.

good luck! =)

---

### Post by Perfect Storm on 2006-06-18
I know, but it's the right way to do it =)

By the way it's obsolite now, Cedega have released v5.2 which doesn't require hack or fake package.

---

