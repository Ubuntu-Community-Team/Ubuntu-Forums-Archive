---
title: "How to display output values with ngspice?"
date: 2010-11-06
forum: Education &amp; Science
---

### Post by mahela007 on 2010-11-06
I've looked everywhere but there just don't seem to be any decent ngspice tutorials. I've figured out how to create a netlist, load in into ngspice and run it but I'm having trouble displaying the results. I would like to know how to display the magnitude of the current in a simple circuit like a battery and two resistors in series. 
thanks.

---

### Post by stchman on 2011-03-03
I too would be very interested in this.

---

### Post by mahela007 on 2011-03-05
Unfortunately I never found the answer...

---

### Post by stchman on 2011-03-05
I have a lot of old PSpice .cir files that I would like to analyze and current through components would be very nice.

---

### Post by hal8000 on 2011-03-21
NGspice supports all commands of spice 3, but with speed improvements etc.

The command to display your netlist is:
listing
run (to run simulations as defined in netlist)
print or plot to display variables.

The DC analyasis computes the bias point of the circuit, voltages at ALL circuit nodes, and currents through voltage sources only.

Remember that current in a series circuit is the same at all points, so any series resistor, has same current as voltage source.
If however you have series and parallel branches, then add a 0 Volt voltage source in series with the branch.
Hopefully this simple example will demonstrate

ngspice 5 -> listing
	* series dc test

     2 : .global gnd
     3 : v1 1 0 dc 10
     4 : r1 1 2 10k
     5 : v2 2 3 dc 0
     6 : r2 3 0 40k
     7 : .op
     9 : .end
ngspice 6 -> print all
v(1) = 1.000000e+01
v(2) = 8.000000e+00
v(3) = 8.000000e+00
v1#branch = -2.00000e-04
v2#branch = 2.000000e-04


The netlist called seriesrc.cir is below:
* Series DC test
V1 1 0 DC 10
R1 1 2 10k
v2 2 3 DC 0
R2 3 0 40k
.op
.END

The command print all prints all node voltages, just to prove kirchoffs current law, V2 is a 0V voltage source in series with R1. The current through v1# branch is same as v2# branch.

You also have to remember that spice calaculates current flow from positive node of a voltage source to negative node,  which is why the v2#branch is shown as negative.

[http://zone.ni.com/devzone/cda/tut/p/id/5416](http://zone.ni.com/devzone/cda/tut/p/id/5416)

The above link has some basic info and a good description of voltage sources.

---

### Post by ngspice on 2012-07-03
There is an online version of ngspice available at [www.ngspice.com](www.ngspice.com).  Examples circuits are available on the site that show you exactly how to simulate and plot results for some simple circuits.  And if you have additional questions, the forum on that site may be more helpful.

---

### Post by overdrank on 2012-07-03
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

