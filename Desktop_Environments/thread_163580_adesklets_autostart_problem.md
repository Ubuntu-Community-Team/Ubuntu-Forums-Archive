---
title: "adesklets autostart problem"
date: 2006-04-21
forum: Desktop Environments
---

### Post by feanor_arcamenel on 2006-04-21
I added adesklets into preferences > sessions and tried with different orders. every time I get this result. What do those icons beside adesklets mean?

[[IMG]http://img118.imageshack.us/img118/1897/adesklets9li.th.jpg[/IMG]](http://img118.imageshack.us/my.php?image=adesklets9li.jpg)

by the way if I run adesklets manually after startup, my yab bar starts with no errors.

---

### Post by louis_nichols on 2006-04-21
Did you write the adesklets start command as

*adesklets --nautilus*  ?

Thats how it should be started under gnome

---

### Post by feanor_arcamenel on 2006-04-21
oops :roll: 
so that's what I learned today, thanks :)

---

### Post by feanor_arcamenel on 2006-04-21
nope, it still shows that trash icon for adesklets
I also tried manually opening the bar desklet and when logging out checked "save this session" box

---

### Post by art on 2006-04-21
Firts of all, put it to start at 50, and put just adesklets. How do you start desklets? You need to go into the directory where you put it, and then ran Let's say you ran the weather desklet. You go to directory weather-0.04, then ran ./weather.py &, and then close the terminal, and in another one ran adesklets. The weather should come up again. Next time you log in it should be there,

---

### Post by feanor_arcamenel on 2006-04-21
no difference. somehow it manages to reset ~/.adesklets file every time I log in.  
Isn't this file supposed to store the possitions of desklets.

---

### Post by louis_nichols on 2006-04-21
For me, simply running "adesklets" never worked, be it from terminal or as a startup program.

as for registering desklets, you just run the scipt and press r for registering.

the trash icon might just be cuz adesklets runs once to start deslets and the exits (it's also why you have to put it in startup programs and it's not automatically remembered by gnome session manger).

you may also want to visit [http://adesklets.sf.net](http://adesklets.sf.net) for help. they have a great forum and sylvain is always very helpfull.

---

### Post by NobodySpecial on 2006-06-09
Answer:

```
adesklets -d 5 --nautilus
```

Use the delay ("-d") option to delay startup for 5-10 seconds.

---

