---
title: "Running commands on startup?"
date: 2009-02-06
forum: General Help
---

### Post by Gibbs on 2009-02-06
I've got Intrepid and can't figure out how to run commands on startup. I've searched online but nothing seems to work so I'm assuming that's for older versions of Ubuntu.

Basically I want to run LAMPP and a command to kill pulseaudio.

Any help appreciated :)

---

### Post by vojtech.t on 2009-02-06
You can make a simple bash script a add it it to System&#8594;Preferences&#8594;Session

Example of scipt:

```

#!/bin/bash

killall pulseaudio &

"command for lampp"

```

---

### Post by Gibbs on 2009-02-06
Excellent, thanks.

---

### Post by bryncoles on 2009-02-06
seems like a convoluted way of doing things - letting pulse audio boot up and then shutting it down. why not just go to 'sessions' in control panel (assuming you're on gnome) and remove pulseaudio from your start-up programs, and add 'command for lampp' instead? no need for a script at all...

---

