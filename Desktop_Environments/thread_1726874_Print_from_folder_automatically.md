---
title: "Print from folder automatically"
date: 2011-04-11
forum: Desktop Environments
---

### Post by pangeh on 2011-04-11
Hi,

I need to setup a network scanner which will scan to a folder via the network onto an Ubuntu pc. When the file is scanned I need the Ubuntu pc to automatically print the file to the default printer and then deletes the scanned file.

I haven't been using Ubuntu very long and was not sure how to achieve this. I was wondering if perhaps I should write a script, after learning how to, that checks the folder for any files and then prints them. Once printed it then deletes the files. Would I need to have this script running via a scheduler that runs the script every second? Or is there another way to achieve this?

Any direction on how I should approach this problem is sincerely appreciated.

Many thanks

regards
p.

---

### Post by rosencrantz on 2011-04-11
For periodic repeats, you should check out the cron scheduler or the watch command.
Command-line printing is usually done with lp (lp -d <cups printer name> <filename>).
You might want to use a command-line graphics tool like ImageMagick (convert) or gs to pre-edit the scan and convert it to pdf or ps, so there are no formatting/resolution issues.
A tentative example script:
watch -n 20 printscript.sh
Code for printscript.sh (make it executable)
```

#!/bin/bash
for file in *.jpg; do
   convert -density 300 $file testfile.pdf
   lp -d <cups printer name> testfile.pdf
   rm testfile.pdf $file
done

```
Notes: I assume there's nothing but your scan images in the folder (no other jpg's).
For more sophisticated scheduling use cron.
As an example, I specified a pixel density of 300dpi for convert. You can do other things like adding whitespace to blow up to letter format. Our network printer was a bit puzzled about which tray to use when faced with a non-standard PDF page size and required manual tray selection.

---

### Post by pangeh on 2011-04-17
Hi Roesencrantz,

Thanks so much for your reply and for the example. Its exactly the kind  off stuff I need to put a solution together. The files are converted to  pdf by the scanner so it will just be straight forward printing to the  printer from the shared folder. 

I think the script example you gave is perfect, going to try some  variations for practice this week and will read up more on cron to use  as a scheduler for the script.

Thanks again so much. I really appreciate your help.

Kind regards
P

---

