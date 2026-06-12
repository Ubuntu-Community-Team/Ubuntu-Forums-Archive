---
title: "Scapy-Syntax error"
date: 2009-06-10
forum: General Help
---

### Post by sky811 on 2009-06-10
Hi all,

I have installed Ubuntu 9.04, and would like to install Scapy package into it. I checked from Synaptic Package Manager that python-scapy 2.0.0.5-1 have been installed, but when I run the python script (which need to import scapy as lib), the following error occurred:

Traceback (most recent call last):
  File "./arp.py", line 9, in <module>
    from scapy import Ether,ARP,conf,srp
  File "/home/xxxx/Desktop/scripts/scapy.py", line 114
    tr = map(lambda x: Gnuplot.Data(x,with="lines"), trt.values())
                                         ^
SyntaxError: invalid syntax

Anyone can give me a hint how to fix the issue? Very thanks!!!

---

### Post by brainsonfire on 2009-08-22
from [http://nahidulkibria.blogspot.com/2009/08/error-while-running-wifizoo-in-ubuntu.html](http://nahidulkibria.blogspot.com/2009/08/error-while-running-wifizoo-in-ubuntu.html)


replace "with" with "with_" in scapy.py:

tr = map(lambda x: Gnuplot.Data(x,with="lines"), trt.values())
tr = map(lambda x: Gnuplot.Data(x,with_="lines"), trt.values())

and

world = Gnuplot.File(conf.gnuplot_world,with="lines")
world = Gnuplot.File(conf.gnuplot_world,with_="lines")

---

### Post by digivore on 2009-08-31
Thanks brainsonfire, that worked for me!  is it something easy to explain?   what does the "_" do?

---

### Post by Symmetric on 2009-09-23
Thanks a for the tip, this helped me out a lot :)

---

