---
title: "'record streaming audio' shortcut"
date: 2006-08-09
forum: Desktop Environments
---

### Post by mozgreen on 2006-08-09
To record an audio stream as an oggs file I do :
            *arecord -f cd -t raw | oggenc - -r -o out.ogg*
and this works briliantly.
However I would like a quick keyboard shotcut to this command or to make a desktop icon that would send the command.
I have tried the right-clik 'desktop launcher' approach but this does not work. :confused:
Any ideas gratefully recieved.

Maurice Green

---

### Post by x64Jimbo on 2006-08-09
you need a shell script. Start like this:
```
 #!/bin/bash
arecord -f cd -t raw | oggenc - -r -o out.ogg
```
then make the script executable
```
chmod +x scriptname
```
then create your desktop shortcut to this script

---

### Post by mozgreen on 2006-08-09
Thanks Jimbo
When I type:
 [I]#!/bin/bash
arecord -f cd -t raw | oggenc - -r -o out.ogg[/I]
the recording just starts.
I then type, in a new terminal:
*chmod +x arecord -f cd -t raw | oggenc - -r -o out.ogg*
and an error message tells me an operand is missing.
I must be doing something wrong (or nothing right).
Excuse the steep command line learning curve, please.

---

### Post by mozgreen on 2006-08-09
I've just twigged (write the script in gedit... doh) and it works! Great!  Thanks a million x64jimbo!

---

### Post by x64Jimbo on 2006-08-09
No problemo, mozgreen. I had to write a similar shell script with a desktop shortcut recently so it was still fresh in my head.

---

