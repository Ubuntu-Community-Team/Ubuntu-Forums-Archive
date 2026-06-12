---
title: "Tool for Monitoring Disk/File Activity"
date: 2006-03-12
forum: Desktop Environments
---

### Post by joshuapurcell on 2006-03-12
I'm looking for a simple command-line application that monitors what files have been updated in a certain location (or the whole partition if chosen) and prints out the file path and timestamp of the action. I don't necessarily care if this tool is able to report what is actually being done to the file (adding/modifying/deleting), although that would also be useful. I would be perfectly happy just seeing a list of all files being added or updated from the time that I start the application to the time I press Ctrl-C.

Some applications I've looked into briefly are tripwire, diffmon, systraq, iostatm, fcheck and icheck, but each of these seem to not do exactly what I'm looking for. Tripwire is too much for what I need (with the security, databases, and configuration), diffmon and systraq seem to be more focused on giving a summary of changes after the fact (instead of as the changes happen), and fcheck/icheck shows actual disk useage as it happens but not what files are being touched.

Another description of the application I'm looking for would be that it watches disk activity and prints a timestamp and filename everytime a file is touched on the disk (while not necessarily printing repetitive information). Please post if you know of a tool that can fit this description... or at least comes close.
Think of it as tcpdump for files on a disk.

---

### Post by joshuapurcell on 2006-03-12
Bump.

---

### Post by joshuapurcell on 2006-03-13
Another bump. Any information would be appreciated.

---

### Post by joshuapurcell on 2006-03-22
The best solution I've come up with to this is the following command:```
lsof | cut -c 75-255 | grep '/opt/' | uniq | nl | head -10
```This shows you the first 10 names of unique files that are located in your /opt directory. I would like to get this to automatically refresh on the same lines, but this is where I'm having trouble:```
#!/bin/bash
i=1
while [ $i ]; do
    echo -n -e "\rlsof | cut -c 75-255 | grep '/opt/' | uniq | nl | head -10"
    sleep 1
done
```Instead of the above running the command that is echoed, it's just printing the actual command on the line (instead of the output)... over and over again.

---

### Post by artships on 2006-03-22
I think you need to remove **echo -n -e "\r** and the trailing double-quote.

Have you tried **ls -Fat**?

---

### Post by joshuapurcell on 2006-03-22
[QUOTE=artships]I think you need to remove **echo -n -e "\r** and the trailing double-quote.[/QUOTE]
Removing the **echo** phrase would make it so that the command would be run (displaying output instead of the actual command), but it would not act like the top command does now (which only uses a specific portion of the page to display constantly updated data). The **-e** combined with the **\r** inside the quotes makes it so that the output of the loop constantly overwrites the previous output on the same line. When I get home tonight I'll change it so that it works the way I'm planning, but even then it would not be close to how the top command performs.

I want the data given by the **lsof** command to be filtered very similarly to how I've managed to do with piping it to various commands (but I'll still need to modify this later), then display it in the terminal and constantly refresh the same section of the screen with updated data.

I think I'll start looking into how the top command works and see if I can't use something from there. Another thing is that I've read through the man page of **lsof** and found an option for refreshing the data at specific intervals. One of these routes may help. Thanks for the help.

EDIT:[QUOTE=artships]Have you tried **ls -Fat**?[/QUOTE]Although my current command is only displaying data starting at a single directory, I want to eventually be able to display data for all files on the system. **ls -Fat** only displays the contents of the current directory with an associated timestamp and indicator (for what type of file it is), and doesn't say anything about if the file(s) are actually opened at the time.

---

