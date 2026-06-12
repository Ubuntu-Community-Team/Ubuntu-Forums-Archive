---
title: "HP Printing Errors in Ubuntu"
date: 2009-04-23
forum: General Help
---

### Post by iheartubuntu on 2009-04-23
Im posting this for my dad who is having some interesting problems Ive never seen before. He has two HP printers... the one here at work is an all in one laserjet printer, and his printer at home is just an HP laserjet printer. When he prints here at work, no problems (he has intrepid here on an XP network) and at home he has jaunty with the printer directly connected.

As you can see in the photo below, his printer at home prints these odd black squares every so often, covering up letters. We dont have this problem here at work (im using ubuntu jaunty also networked to that printer).

The only thing I can see really different is an XP network where i had to install a PPD file on our systems, and at his house its direct connect and jaunty found the printer.

Any recommendations? Thanks!

[IMG]http://www.shirtees.net/hp-printer.jpg[/IMG]

---

### Post by iheartubuntu on 2009-04-24
Bump? Anyone? Ideas? Thanks!

---

### Post by iheartubuntu on 2009-04-29
Bump?

---

### Post by LowSky on 2009-04-29
I would look at the driver being used. Also is HPLIP installed, form what I have noticed the one from sourceforge is better than the repo version.

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by Metar on 2009-05-18
I also came across this problem when I upgraded to Jaunty - it used to print fine before, and still prints well on XP, but shows exactly these "blocks"... Odd.

---

### Post by iheartubuntu on 2009-05-23
I fixed this problem on my dads computer by uninstalling the printer (that 9.04 created using their drivers) and creating a new printer with the correct PPD file.

---

### Post by Metar on 2009-05-23
I've actually just fixed it as well, in a slightly different way - and simpler, I think.

In the printer's Properties window, selecting a new driver, I chose the hpijs driver instead of the recommended Foomatic driver - and voila, it worked!
Is there any way to get this into the proper release? Seems the Foomatic drivers don't really work with the Laserjet 2100..

---

### Post by rubbsdecvik on 2009-05-25
Oh, thank you. Switching the driver worked really well for me. Thanks.

---

