---
title: "Conky question"
date: 2009-04-28
forum: General Help
---

### Post by mgdew on 2009-04-28
hopefully this is a simple one for you conky experts out there...

I have 5 conky scripts running from a small autostart bash script, everything works lovely. Now, what I would like to do is have one python file which basically gives out some default values to all of my 5 scripts, so I made a file called default.py --

import sys

pname = sys.argv[1]

if pname == "DefaultWidth":
    print 150
elif pname == "Default":
    print 3

in my conkyscript file I want to do the following;

maximum_width ${python ~/.scripts/default.py DefaultWidth}

but, it does not seem to be executing the script for the variable parts of the conky script, only the parts below the TEXT identifier in the script.

Does anyone know if you can actually do what I am trying to do ? or does conky only execute scripts below the TEXT identifier ?

p.s I have tested the python returns fine in both Terminal, and using the same $python call inside a conky script, below the TEXT identifier.

ta
Mart

---

