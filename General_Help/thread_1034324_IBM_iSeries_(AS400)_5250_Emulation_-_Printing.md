---
title: "IBM iSeries (AS/400) 5250 Emulation - Printing"
date: 2009-01-08
forum: General Help
---

### Post by jgc on 2009-01-08
My question relates specifically to lp5250d, and more accurately, how to use / configure it! :D

OS: Intrepid 8.10
Emulation: IBM iSeriesAccess-5.4.0-1.4.i386.rpm (converted to deb with Alien) installed and working.

Creating sessions and print screen works fine.

What I need to do is that which is described here: [http://manpages.ubuntu.com/manpages/gutsy/man1/lp5250d.1.html](http://manpages.ubuntu.com/manpages/gutsy/man1/lp5250d.1.html)

... but am unsure how to configure print outputs to, for example, a network attached HP printer.

Ultimately, production to PDF might be useful.

Can anybody help? :confused:

---

### Post by jgc on 2009-01-12
Anybody? :(

---

### Post by jgc on 2009-07-01
#-o

---

### Post by t4thfavor on 2009-07-01
You lost most of us at AS/400 I have seen jacks labeled AS/400, but I have never actually seen one IRL. 

This looks like the relavent lines.

EXAMPLES

        lp5250d env.DEVNAME=LINPRT1 env.IBMMFRTYPMDL=&#8217;*HP4&#8217; as400sys
               Connect  to  as400sys  as  the printer LINPRT1, using host print
               transform on the AS/400 to print to an HP Laserjet or compatible
               using lpr.
 
        lp5250d  env.DEVNAME=LINPRT1  env.IBMMFRTYPMDL=&#8217;*OKI184IBM&#8217;  outputcom&#8208;
        mand=&#8217;&#8217;scs2ascii | lpr -Poki&#8217; as400sys
               Print to an Okidata Microline 184 Turbo on the local print queue
               named &#8216;oki&#8217;.
 
        lp5250d env.DEVNAME=PSPRT outputcommand=&#8217;scs2ps > scs$$.ps&#8217; as400sys
               Convert spooled files into PostScript® files.

so 
```

lp5250d env.DEVNAME=PRINTERNAME env.IBMMFRTYPMDL=&#8217;*HP4&#8217; as400name

```
Or the second example which looks more usable will connect to the as400 as an Okidata Microline 184 Turbo, and then pipe stuff sent to that printer to the local print queue called oki (this is what varies per machine as the local print queue shouldn't have to be an Okidata printer).

---

