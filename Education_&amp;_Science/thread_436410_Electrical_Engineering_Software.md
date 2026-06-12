---
title: "Electrical Engineering Software"
date: 2007-05-07
forum: Education &amp; Science
---

### Post by Pocadotty on 2007-05-07
I wanted to get some opinions on some open source alternatives to a few mainstream applications.

MATLAB, 
I have heard that Scilab is a fairly good alternative, what do you guys think.

PSpice,
I would like something similar to OrCAD capture for designing and simulating analog circuitry.  Hefty component libraries would be nice.

AutoCAD,
I'm just looking for a PC-board layout program that can link layout to a schematic netlist in some way.  And save layouts in AutoCAD file formats.

Xilinx with Modelsim,
I'm looking for a fairly robust digital system design and testing program with VHDL and FPGA support.

HyperTerminal,
general purpose serial communication program that I can use to load firmware into embedded microprocessors over RS232, as well as ASCII text based communications with embedded devices.

I'm trying to transfer all my design software to Open Source, any help would be appreciated.

Thanks

---

### Post by mickbuntu on 2007-05-10
> **Pocadotty said:**
> 

> PSpice,
> I would like something similar to OrCAD capture for designing and   > simulating analog circuitry.  Hefty component libraries would be nice.

Do not want to double post do a search for ktechlab thread of mine. Just noticed your post, but came into this thread late.  Hehe hefty is  really  hard to swallow  word as ktechlab is not done.  Perhaps an odd program if you can understand it  might be good: qucs.

> AutoCAD,
>  I'm just looking for a PC-board layout program that can link layout >  to a schematic netlist in some way.  And save layouts in AutoCAD >  file formats.

1. kicad  easier.   <--- best bet.
2. Geda harder.    <-- Best bet for feature.
3. Oregano.         <---  Just circuits mostly and slight simulator through gnucap.
4. xcircuit.           <---  Extensible but how far?
5. Eagle  for linux??    <--- surely exists.

I use expresspcb personally in windows because of no cost for the program.

Not sure if it (linux programs above) can export, did not care for the feature so was ignorant to it.

> Xilinx with Modelsim,
> I'm looking for a fairly robust digital system design and testing       > program with VHDL and FPGA support.

Not sure of a proram for this perhaps tkgate  such as logic gates???

> HyperTerminal,
>  general purpose serial communication program that I can use to    > load firmware into embedded microprocessors over RS232, as well >  as ASCII text based communications with embedded devices.

Really not sure, was looking for something similar. Linux seems to be just "catching" on in these areas and will take time. Most of the best Engineering / Electronics software is still stuck in windows.

> I'm trying to transfer all my design software to Open Source, any help would be appreciated.

Eh....  Yah.... 

That is a dreaded task your partial friend might be wine. That is  if and when it works correctly still like a gamble.

Thanks



Comments are inside your message.

---

### Post by Pocadotty on 2007-05-10
I installed most of the applications...

Once i get a chance I will evaluate them in several applications as best as I can and make a thread about how well the various programs work in certain applications

most seam to be developed for hobbyist and educational purposes... It will be interesting to see how they work in a professional design

Thanks

---

### Post by finer recliner on 2007-05-10
my experience with pspice has been terrible (version 9.2) i realize the power it has and its potential to be awseome. but the lack of user friendliness and the obsurd amount of bugs i run into makes me want to throw my computer off the desk

</rant>

oh yeah, and thank you micbuntu for those EE recommendations

---

### Post by Pocadotty on 2007-05-11
yeah... pspice isn't very user friendly, but after having to do simulation lab and project at University I got the hag of it.

Better then LTspice though.  LTspice had got to be the least user friendly circuit sim software I have seen

---

### Post by slimdog360 on 2007-05-11
Im a fan of scilab, but if your going to be sharing the code then the linux version of matlab is probably best. Scicos in scilab is pretty good but its interface is a bit dodgy, simulink does a much better job in that department.
Download it and give it a go anyway, you dont loose anything but 20 or so minutes if you don't like it. Get it from their website rather then synaptic, their version is more up to date and is problem free, something which I've never experienced from the Scilab version via apt-get.

---

