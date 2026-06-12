---
title: "Longer shortcuts"
date: 2006-09-05
forum: Desktop Environments
---

### Post by SvanteH on 2006-09-05
I am trying to find a script that can be ran that does;

[PHP]cd TransGaming_Drive
cd Program
cd Tibia
cedega --gddb ~/.cedega/.gddb/everquest.gddb Tibia.exe engine 0[/PHP]

I thought of making a sh but it wasn't as easy as I thought, I am quite sure a script that runs it then linking the shortcut to it is the easiest way.
](*,)

---

### Post by Jussi Kukkonen on 2006-09-05
```
#!/bin/sh
cd XXX/TransGaming_Drive/Program/Tibia
cedega --gddb ~/.cedega/.gddb/everquest.gddb Tibia.exe engine 0
```
Replace XXX with the full path to TransGaming_Drive. Save to e.g. ~/bin/Tibia

When you've created the file, make it executable:
```
chmod u+x ~/bin/Tibia
```
Test it from command line first 
```
~/bin/Tibia
```

---

