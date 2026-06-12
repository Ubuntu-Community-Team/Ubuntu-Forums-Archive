---
title: "Unable to run tkl script . Help !"
date: 2009-04-29
forum: General Help
---

### Post by blue1dot on 2009-04-29
Hello All, 

I am trying to run this script below, which is saved as first.tcl and is located in one of the dir's in home.

#!/usr/bin/wish
button .b -text "Welcome to the world of WIDGETS" -command exit
pack .b
.b configure -background red

I do chmod u+x first.tcl to make this an executable and then run this from the bash shell by typing ./first.tcl

On this, the op i get is 

./first.tcl: line 5: button: command not found
./first.tcl: line 6: pack: command not found
./first.tcl: line 7: .b: command not found

This shows that the wish shell is not being invoked in spite of #!/usr/bin/wish

Whereas on typing wish first.tcl the script runs without a problem.

Could please someone explain why this is happening ?

Thanks,

---

