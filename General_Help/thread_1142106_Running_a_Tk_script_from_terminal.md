---
title: "Running a Tk script from terminal"
date: 2009-04-28
forum: General Help
---

### Post by blue1dot on 2009-04-28
Hello All, 

I am trying to run this script below, which is saved as first.tcl and is located in one of the dir's in home.

[I]#!/usr/bin/wish
button .b -text "Welcome to the world of WIDGETS" -command exit
pack .b
.b configure -background red
[/I]
I do* chmod u+x* first.tcl to make this an executable and then run this from the bash shell by typing    *./first.tcl*

On this, the op i get is 

./first.tcl: line 5: button: command not found
./first.tcl: line 6: pack: command not found
./first.tcl: line 7: .b: command not found

This shows that the wish shell is not being invoked in spite of [I]#!/usr/bin/wish

[/I]Whereas on typing* wish first.tcl *the script runs without a problem.
 
Could please  someone explain why this is happening ?

Thanks,

---

