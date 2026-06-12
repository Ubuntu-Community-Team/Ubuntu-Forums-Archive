---
title: "double click save(conky)"
date: 2009-08-25
forum: Desktop Environments
---

### Post by glennnf on 2009-08-25
Hi,been editing a new conky & found that if i double click "save" conky blacks out then reappears with the new changes added,i was led to believe that you had to log out & back in for changes to be applied,is this right?Thanks,Glennnf.:)

---

### Post by VCoolio on 2009-08-25
You don't need to logout / in for applying a new config, just restart conky. I'm not sure on the causality of immediate application of changes in conky; it happens sometimes to me too, which is convenient, but it seems haphazardly. Maybe it has to do with the "background no" variable (which in this case does not move the conky process to the background; usually I have it set to yes, which is the default behavior). 
A convenient way to restart conky without the terminal is to make a launcher for this script (if conky is running it will kill it, else it will start it):

```
#!/bin/sh
if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 conky -c path/to/conkyconfig1 &
 exit
fi
```

---

### Post by glennnf on 2009-08-25
Thanks Vcoolio,i will try your script, background was set to yes ,so who knows,it is rather convenient though to be able to duoble click save. Thanks Glennnf.

---

### Post by ben2talk on 2009-09-12
> **glennnf said:**
> Hi,been editing a new conky & found that if i double click "save" conky blacks out then reappears with the new changes added,i was led to believe that you had to log out & back in for changes to be applied,is this right?Thanks,Glennnf.:)

Double click 'save' where? Actually, if your conky window is floating, it's simplest simply to scale the windows (if using conky with scale) and delete the window from there, assuming no decoration - otherwise Alt F2 killall conky does the job nicely...

Generally when editing conky, it's useful to run a couple of terminals (I use Terminator with two panes open) and run the commands 'conky -d -c /home/ben/Apps/short.conky' (Admin being the folder where I stick them) and then 'killall conky' - and in the same folder I have my little startup script which starts things up at a rate which doesn't interfere with the desktop loading too much:

#!/bin/bash
sleep 10;
conky -d -c /home/ben/Admin/short.conky &
sleep 30;
dropbox start -i

---

