---
title: "Need help with a script"
date: 2009-05-12
forum: General Help
---

### Post by Gausian on 2009-05-12
Somtimes my wireless bugs out and i have to restart the driver with the following commands to get it back online...

```
sudo modprobe -r iwl4965

sudo modprobe iwl4965
```

Is there anyway to create a script that includes these commands, and can be executed by say double clicking a script file?

Thanks for the help...

---

### Post by kpkeerthi on 2009-05-12
1. Create a file:
```
gksudo gedit /usr/local/bin/reload-wifi
```
2. Paste the below lines:
```

#!/bin/bash

modprobe -r iwl4965
modprobe iwl4965

```
3. Save and Exit
4. Give permission to execute:```
sudo chmod +x /usr/local/bin/reload-wifi
```

To run the script, open a terminal and enter
```
sudo reload-wifi
```

---

### Post by LoloftheRings on 2009-05-12
of course:
```

#!/bin/bash
gksudo modprobe -r iwl4965
gksudo modprobe iwl4965

```

Call it whatever you want, file extensions also don't matter and run the following command:
```

chmod +x /path/to/yourscript

```
where 'yourscript' is the filename of the script.

---

### Post by Gausian on 2009-05-12
Brilliant advice guys!  thanks for the help, works like a charm!

---

