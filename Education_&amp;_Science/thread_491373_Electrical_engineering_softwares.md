---
title: "Electrical engineering softwares?"
date: 2007-07-03
forum: Education &amp; Science
---

### Post by shafin on 2007-07-03
Hi,I'm an Electrical Engineering student,and recently decided to switch to linux.Can you please tell me if there are open source software alternatives available for the following softwares?

PSpice
Matlab
Quartus II

If open source softs are not available,is there any other linux software versions of them?

Thanks,
Shafin

---

### Post by arvevans on 2007-07-03
I just went into the Synaptic Package Manager and did a search for "simulator" and this is what popped up:
-----------------
 Common Lisp RLC Circuit Simulator
cl-rlc provides a simulator for RLC (resistance, inductance, capacitance)
circuits. It is written in Common Lisp and uses the xgraph package for
plotting.
-----------------
VHDL compiler/simulator using GCC technology
(Description from the GHDL home page <http://ghdl.free.fr>):
GHDL is a VHDL simulator, using the GCC technology.
VHDL is a language standardized by the IEEE, intended for developing
electronic systems.
GHDL implements the VHDL language according to the IEEE 1076-1987 or
the IEEE 1076-1993 standard. GHDL compiles VHDL files and creates a
binary which simulates (or executes) your design.
GHDL does not do synthesis: it cannot translate your design into a
netlist.
----------------
GNU Circuit Analysis package
GNUCAP is a general purpose circuit simulator.  It performs nonlinear
dc and transient analyses, Fourier analysis, and ac analysis
linearized at an operating point.  It is fully interactive and
command driven.  It can also be run in batch mode or as a server.
The output is produced as it simulates.  Spice compatible models
for the MOSFET (level 1,2,3) and diode are included in this
release.
---------------
Graphical Intel 8085 simulator, assembler and debugger
GNUSim8085 is a graphical simulator, assembler and debugger for the
Intel 8085 microprocessor.
---------------
Verilog simulator
Cver is a full 1995 IEEE P1364 standard Verilog simulator.  It also
implements some of the 2001 P1364 standard features.  All three
PLI interfaces (tf_, acc_, and vpi_) are implemented as defined
in the IEEE 2001 P1364 LRM.
--------------
Simulator for Microchip's PIC microcontrollers
Gpsim is a full-featured software simulator for Microchip PIC microcontrollers.

Gpsim has been designed to be as accurate as possible. Accuracy includes the
entire PIC - from the core to the I/O pins and including ALL of the internal
peripherals. Thus it's possible to create stimuli and tie them to the I/O pins
and test the PIC the same PIC the same way you would in the real world.
--------------
a waveform viewer eg for spice simulators
gwave - a viewer for the output of spice-like simulators
and other viewing of analog data.
--------------
digital circuit editor and simulator for KDE
KLogic is an application for building and simulating digital circuits
easily.

It provides an easy way to build circuits containing standard
components like AND, OR, XOR and flipflops like RS and JK. To build
more complex and reusable circuits, you can create sub-circuits.
--------------
IDE and simulator for the Xilinx PicoBlaze-3
kpicosim is a development environment for the Xilinx
PicoBlaze-3 soft-core processor for the KDE Desktop (Linux).
The environment has an editor with syntax highlighting, compiler,
simulator and export functions to VHDL, HEX and MEM files.
---------------
circuit simulator for microcontrollers and electronics
KTechlab is a circuit simulator with a nice, clickable and discoverable
interface. It supports many discrete components, logic circuits as well
as PIC programming in its own Basic dialect and some form of assembler.
---------------
Simulator for the Microchip PIC16C84 microcontroller
Nitpic is an X-based simulator for the Microchip PIC family of
microcontrollers.  It currently supports only the PIC16C84.
---------------
Simulator for the Microchip PIC16C84 microcontroller
Nitpic is an X-based simulator for the Microchip PIC family of
microcontrollers.  It currently supports only the PIC16C84.
---------------
Micro-controller simulator for SDCC
uCsim is a microcontroller simulator. It is extensible to support
different microcontroller families. It currently supports Intel
MCS51 family, HC08 and Z80 microcontrollers.
---------------
Atmel AVR simulator
simulavr simulates the Atmel AVR family of micro-controllers,
emulates a gdb remote target, and displays register and memory
information in real time.
---------------
SimulPIC
simulator for Microchip PIC16F84 microcontroller
This software allows to simulate the execution of any program on a Microchip
PIC16F84 microcontroller.
---------------
Event driven digital circuit simulator with Tcl/Tk
TkGate is a event driven digital circuit simulator with a Tcl/Tk-based
graphical editor. TkGate supports a wide range of primitive circuit
elements as well as user-defined modules for hierarchical design. The
distribution comes with a number of tutorial and example circuits which
can be loaded through the "Help" menu. The example circuits include a
simple CPU, programmed to run the Animals game. For more information,
check out the online documentation at [http://www-2.cs.cmu.edu/~hansen/tkgate/](http://www-2.cs.cmu.edu/~hansen/tkgate/)
--------------
Verilog Behavioral Simulation
Verilog is a Hardware Description Language used mostly for digital
circuit design and simulation. This program is a simple
implementation of a Verilog simulator. VBS tries to implement all of
the Verilog behavioral constructs that are synthesizable, but still
allow complex test vectors for simulation.
--------------

The section for Ham Radio software has a good assortment of electronics oriented applications.

Going onto the web (Google) and searching for keywords like "Linux MatLab", and Linux Circuit Simulator" and so forth will get you a lot of additional results.
_._

---

### Post by hboshoff on 2007-07-03
There is a MATLAB clone called octave. It is in the universe section of Ubuntu's repository.

It seems there is also a derivative of SPICE called ngspice [http://ngspice.sourceforge.net/]("http://ngspice.sourceforge.net/"). Not packaged for Ubuntu yet.

---

### Post by huangja on 2007-07-04
There is a Native linux version of Matlab, even though I run Matlab on Wine, heh. An open source alternative for it is GNU Octave, which in my opinion is very good, although it lacks the GUI and some advaned features of matlab. 

At school I used quartus II under RHEL, so im assuming there has to be a native linux version of it. Unless it was running under wine without my knowledge. I really doubt there would be a open source version for it though.

---

### Post by RebounD11 on 2007-07-04
Finally a clear list for this kind of software, I've been looking around a lot for these apps. :D 

Anyway I found another PSpice like program called QUCS, and it seemed pretty accurate and easy to use.

---

### Post by shafin on 2007-07-10
> **huangja said:**
> There is a Native linux version of Matlab, even though I run Matlab on Wine, heh. An open source alternative for it is GNU Octave, which in my opinion is very good, although it lacks the GUI and some advaned features of matlab. 

At school I used quartus II under RHEL, so im assuming there has to be a native linux version of it. Unless it was running under wine without my knowledge. I really doubt there would be a open source version for it though.
Quartus II is there for linux,but only the subscription one,not the web version.

---

### Post by michas_u on 2007-07-10
Hello,

Now ( under Windows) I use LTSpice from Linear Technologie, it is Freeware and now I need a similar Software, which also use Schematic and Libaries from PSPice.

Thank for all answers

Michael

---

### Post by villindesign on 2007-07-17
LTSpice runs great under wine.

---

### Post by nszabolcs on 2007-07-18
instead of matlab i'd recommend scipy if you know python
(i still use matlab under linux because it has some usefull toolboxes)

i also recommend geda (opensource circuit designer)

---

### Post by nemixer on 2007-07-27
Hi,

Does someone knows whether there is a package of spice/ngspice available for ubuntu edgy?
Hi just found it for hoary..

Thank you very much,

---

### Post by shafin on 2007-08-08
I've installed Ghdl and verilog packages from synaptic,how do I use them?

---

### Post by Salman Awan on 2009-08-01
Is there any alternative for Proteus? Or is there any software which can simulate micro-controller circuits? I want a simulator for intel 8051 microcontroller. If any please let me know.

---

