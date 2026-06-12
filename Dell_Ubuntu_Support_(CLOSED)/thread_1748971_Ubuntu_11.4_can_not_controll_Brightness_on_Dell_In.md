---
title: "Ubuntu 11.4 can not controll Brightness on Dell Inspiron N4010"
date: 2011-05-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by luckysanj on 2011-05-04
**Ubuntu 11.4 can not controll Brightness**             
                                                                Hello Dear All,

[FONT=Times New Roman][SIZE=2]**Brightness Problem ****Dell Inspiron 14R N4010 Problems **[/SIZE][/FONT]             
                                                                [FONT=Times New Roman][SIZE=2]Hey Guys,
I freshly installed **[COLOR=Red]Ubuntu 11.4[/COLOR]** on my  laptop Del Inspirion 14 N4010 but in my laptop there is Brightness  controll problem. I read all of forum posted matter for brightness but  it didnt work.

Brightness up down keys moves the brightness slider around but doesn't  change the actual brightness. I am also not able to change the  brightness using the power management tool also.
This problem is draining my battery life crazy.[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=2]System Information[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2]Model: INSPIRON N4010[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2]Service Tag:97P3ZL1[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2]Express Service Code: 200-564-807-41[/SIZE][/FONT]
[SIZE=2][FONT=Times New Roman]CPU: i3 processor [/FONT][/SIZE]


[SIZE=2]Help will be appreciated Thank You.[/SIZE]


Regards,
Luckysanj
                                                                                                  [IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]                                                                                                                      [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=10766793")

---

### Post by mörgæs on 2011-05-04
How does it work in a 10.10 live boot?

---

### Post by luckysanj on 2011-05-04
In live boot same problem.

---

### Post by mörgæs on 2011-05-05
There are some bug reports on this:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/762670](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/762670)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611)


It is not the same Dell as you, but still there may be some advice.

---

### Post by sleeel on 2011-05-09
I also have the same problem!!

I still wait for a solution

---

### Post by SimonMago on 2011-05-10
> **sleeel said:**
> I also have the same problem!!

I still wait for a solution

I have the same problem on my Dell 1370...
The "old" solution (edit xorg.conf) don't work.

---

### Post by murphyac on 2011-05-10
You might try going to the URL below and seeing if that fix works for you.  It worked with my Inspiron 14R (N4010).  My brightness keys now function perfectly, and I thank the folks in another thread who pointed the way to the fix and especially, Kamal Mostafa, who devised it.

[https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)

Hope this helps.
Angela C. Murphy

---

### Post by SimonMago on 2011-05-12
> **murphyac said:**
> You might try going to the URL below and seeing if that fix works for you.  It worked with my Inspiron 14R (N4010).  My brightness keys now function perfectly, and I thank the folks in another thread who pointed the way to the fix and especially, Kamal Mostafa, who devised it.

[https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)

Hope this helps.
Angela C. Murphy

This procedure works for Radeon users only?

---

