---
title: "Electronic simulating softwares for gnu/linux????"
date: 2008-02-03
forum: Education &amp; Science
---

### Post by srikar on 2008-02-03
Please give me a list of electronic simulating opensource softwares that run on gnu/linux.

ex:- multisim(its a circuit simulator - a proprietary one that runs on windows)
      So i need alternatives of such softwares.

---

### Post by srikar on 2008-02-03
I had googled a lot , but dint find a perfect alternative.At present we have ktechlab(good opensource electronic simulator). I just want to know whether there are better electronic simulating softwares than ktechlab. plzz do help me : )

---

### Post by y-lee on 2008-02-03
I responded to this by message this morning as I was headed out the door and didn't have time for a good response.

> **y-lee]Bunch of stuff here but I don't have time to look, heading off to work.

Hope ya find what ya looking for

[Linux/electronics]("http://www.linuxlinks.com/Software/Scientific/Electronic/")[/QUOTE]

Ok now that I have some time to think about this some, here's some suggestions.

[SPICE]("http://bwrc.eecs.berkeley.edu/Classes/IcBook/SPICE/") seems pretty popular, it is a general-purpose circuit simulation program for nonlinear dc, nonlinear transient, and linear ac analysis. SPICE originates from the EECS Department of the University of California at Berkeley, tho it seems maybe development has been [discontinued]("http://embedded.eecs.berkeley.edu/pubs/downloads/").

[The gEDA]("http://www.geda.seul.org/")  project has produced and continues working on a full GPL'd suite of Electronic Design Automation tools

[Qucs]("http://qucs.sourceforge.net/") is an integrated circuit simulator which means you are able to setup a circuit with a graphical user interface (GUI) and simulate the large-signal, small-signal and noise behavior of the circuit. After that simulation has finished you can view the simulation results on a presentation page or window. THO note "So far Qucs is not yet finished... but it is on the road."

Also note some software is said to run under wine, [URL="http://www.linear.com/designtools/software/index.jsp"]SwitcherCAD&#8482 said:**
>  for example is supposed to work in wine, It "is a high performance Spice III simulator, schematic capture and waveform viewer with enhancements and models for easing the simulation of switching regulators"

Also there is a long list of linux apps, some free some commercial found here: [Electrical & Related Software]("http://sal.jyu.fi/Z/1/index.shtml")

It seems srikar is trying to build a linux distro specialized around the needs of electrical engineers. 

[QUOTE=srikar]Thanks for ur support.

Actually we are under a project.
[B]
About project:-[/B]
The project aims at building a debian based operating system for engineering(graduate) students.So to the basic debian OS we have to add best opensource softwares that meet the proprietary standards.

A rather note worth thing to do :)

And as such [Scibuntu]("http://scibuntu.sourceforge.net/") may also be of interest.

Note I have not tried any of this software yet just stuff I've looked at before. Let us know how it goes.

---

### Post by srikar on 2008-02-04
thanks for the info.I will let u know which ones are good after we test them.

---

### Post by Kellobyte on 2008-11-21
Oregano - is a GNOME application for schematic capture and printing of electronic circuits. It can simulate the circuits using Gnucap, ng-spice or Berkeley spice.

Qucs - is an integrated circuit simulator which means you are able to setup a circuit with a graphical user interface (GUI) and simulate the large-signal, small-signal and noise behaviour of the circuit. After that simulation has finished you can view the simulation results on a presentation page or window.

TkGate - is a event driven digital circuit simulator with a Tcl/Tk-based graphical editor. TkGate supports a wide range of primitive circuit elements as well as user-defined modules for hierarchical design.

KSimus - is an application for simulating networks with boolean and floating point data type. Some more data types are planned. Currently there exists only a few components, but because of the modular character of KSimus extensions are easy to develop.

KLogic - is an application for building and simulating digital circuits easily.
It provides an easy way to build circuits containing standard components like AND, OR, XOR and flipflops like RS and JK. To build more complex and reusable circuits, you can create sub-circuits.

*all of the programs are listed in the add/remove software

---

### Post by Salman Awan on 2009-08-01
Is there any alternative for Proteus? Or is there any software which can simulate micro-controller circuits? If any please let me know.

---

### Post by Salman Awan on 2009-08-01
I want a simulator for intel 8051 micro-controller.

---

### Post by AJHunter on 2010-03-19
Speaking of KSimus...
Is there some sort of cheat-sheet for all the components and what they do? With illustrations, preferably? Thanks.:cool:

---

### Post by chronos00 on 2010-05-15
> **Salman Awan said:**
> I want a simulator for intel 8051 micro-controller.

For 8051 simulating you can use "MCU 8051 IDE"

It is a very complete IDE for developing Assembler or C programs for a great variety of micro-controlers. It has a built in simulator.

[http://mcu8051ide.sf.net/](http://mcu8051ide.sf.net/)
[http://en.wikipedia.org/wiki/MCU_8051_IDE](http://en.wikipedia.org/wiki/MCU_8051_IDE)

---

### Post by Das Goat on 2010-07-24
Multisim SEAMS to install under Wine with just a little futzing with the Wine extras to get a missing DLL, but I can't apply the license because the license manager will not run do to a missing DLL. Anyone know how to cram a DLL into wine?

---

### Post by fmcgorenc on 2011-08-09
Is there something similar to EWB Electronics workbench? :confused:

---

### Post by fmcgorenc on 2011-08-09
I'm trying to install qucs from source.

edit: no go :(   are there any apps packaged for ubuntu natty?

---

### Post by pjd99 on 2011-08-11
**CIRCUIT SIMULATION/MODELLING**

Simulink (part of Matlab, so not open/free) has native 32 and 64 bit builds. 
Add Xilinx blockset for Simulink based FPGA design and simulation.

octave -> like Matlab, good for modelling a system if you can provide a transfer function.
ocatve-ocs -> circuit simulator

nec2++ -> antenna modelling.

qucs -> universal circuit simulator

tkgate -> Simulator, graphical editor

oregano -> Circuit capture using SPICE or gnucap

ngspice -> SPICE simulator
gspiceui/easyspice -> SPICE gui's

gnucap -> General purpose circuit simulator

cl-rlc -> Simulate RLC circuits

Linsmith -> Smith charting

**EMULATORS**

spim -> MIPS emulator

emu8051 -> Intel 8051 emulator.

tiemu -> Texas instruments calculator emulator. TI-89/92/92+/V200PLT

Want more? sudo apt-cache search emulator | more

**MICROCONTOLLER DEVELOPMENT**

avrdude/avr-gcc -> For ATMEL microcontrollers

Arduino IDE -> Arduino development environment

simulavr -> Atmel avr simulator
 
 gpsim -> PIC microcontroller simulator


To name a few that should exist in the repos.

---

### Post by chronos00 on 2011-08-13
> **pjd99 said:**
> **CIRCUIT SIMULATION/MODELLING**

Simulink (part of Matlab, so not open/free) has native 32 and 64 bit builds. 
Add Xilinx blockset for Simulink based FPGA design and simulation.

octave -> like Matlab, good for modelling a system if you can provide a transfer function.
ocatve-ocs -> circuit simulator

nec2++ -> antenna modelling.

qucs -> universal circuit simulator

tkgate -> Simulator, graphical editor

oregano -> Circuit capture using SPICE or gnucap

ngspice -> SPICE simulator
gspiceui/easyspice -> SPICE gui's

gnucap -> General purpose circuit simulator

cl-rlc -> Simulate RLC circuits

Linsmith -> Smith charting

**EMULATORS**

spim -> MIPS emulator

emu8051 -> Intel 8051 emulator.

tiemu -> Texas instruments calculator emulator. TI-89/92/92+/V200PLT

Want more? sudo apt-cache search emulator | more

**MICROCONTOLLER DEVELOPMENT**

avrdude/avr-gcc -> For ATMEL microcontrollers

Arduino IDE -> Arduino development environment

simulavr -> Atmel avr simulator
 
 gpsim -> PIC microcontroller simulator


To name a few that should exist in the repos.

This should definitively be a sticky somewhere!
This is a GREAT summary for all electronic users/students

---

### Post by deuxalucard on 2011-10-05
> **pjd99 said:**
> **CIRCUIT SIMULATION/MODELLING**

Simulink (part of Matlab, so not open/free) has native 32 and 64 bit builds. 
Add Xilinx blockset for Simulink based FPGA design and simulation.

octave -> like Matlab, good for modelling a system if you can provide a transfer function.
ocatve-ocs -> circuit simulator

nec2++ -> antenna modelling.

qucs -> universal circuit simulator

tkgate -> Simulator, graphical editor

oregano -> Circuit capture using SPICE or gnucap

ngspice -> SPICE simulator
gspiceui/easyspice -> SPICE gui's

gnucap -> General purpose circuit simulator

cl-rlc -> Simulate RLC circuits

Linsmith -> Smith charting

**EMULATORS**

spim -> MIPS emulator

emu8051 -> Intel 8051 emulator.

tiemu -> Texas instruments calculator emulator. TI-89/92/92+/V200PLT

Want more? sudo apt-cache search emulator | more

**MICROCONTOLLER DEVELOPMENT**

avrdude/avr-gcc -> For ATMEL microcontrollers

Arduino IDE -> Arduino development environment

simulavr -> Atmel avr simulator
 
 gpsim -> PIC microcontroller simulator


To name a few that should exist in the repos.

Wooooowwwwww thanks!!!

---

