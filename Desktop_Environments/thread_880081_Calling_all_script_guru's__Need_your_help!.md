---
title: "Calling all script guru's | Need your help!"
date: 2008-08-04
forum: Desktop Environments
---

### Post by sr_guy on 2008-08-04
Here is the senario. I've been having signal issues with my cable modem. I want a script that runs the below command for my modems diagnostic page 50+ times, and writes the output to a .txt file.

Here is the command:

wget -q -O- [http://192.168.100.1/signaldata.htm](http://192.168.100.1/signaldata.htm) | grep dB
    
output:

<TD>32 dB&nbsp;</TD></TR> ============= > SNR
<TD>-4 dBmV
<TD>43 dBmV  </TD></TR></TBODY></TABLE></CENTER><IMG


What would this script look like?

---

### Post by croto on 2008-08-04
How about something like this?

```

#!/bin/bash

if [[ $# < 1 ]]; then
    echo "Usage:"
    echo "  ./script.sh N"
    echo "     where N is the number of iterations "
    exit 1
fi


for i in `seq 1 $1`; do 
    wget -q -O- http://192.168.100.1/signaldata.htm | grep dB
    echo
done

```

Then you would run it as:

```

./script.sh 50 > log.txt

```

---

