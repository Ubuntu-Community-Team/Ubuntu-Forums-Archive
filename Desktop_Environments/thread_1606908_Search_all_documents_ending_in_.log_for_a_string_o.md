---
title: "Search all documents ending in .log for a string of text?"
date: 2010-10-27
forum: Desktop Environments
---

### Post by Dáire Fagan on 2010-10-27
I'm trying to search all .log files in ~/.irssi/irclogs/ and it's sub directories for the string 'irssi' and I had though the command I'd used for something similar before was:

```
$HOME -name 'documentname*' -exec grep "string" /dev/null '{}' +
```

Evidently this is not the case as bash outputs:

```
bash: /home/dusf: is a directory
```

How should I edit the command, and is it possible to output every line found containing the string to file?

---

### Post by ad_267 on 2010-10-27
Close, it should be:
```
find ~/.irssi/irclogs -name "*.log" -exec grep -H "irssi" {} \;
```

$HOME just means your home directory, you would usually start a command with the name of an executable to run.

The "-H" means grep will print out the file name if it finds a match. I usually want this option enabled when using grep with find but you might not. You can use the "-i" option for grep if you want the grep to be case insensitive too.

If you want to output the result of a command to a file then just add " > filename.txt" at the end.

---

### Post by Dáire Fagan on 2010-10-28
> **ad_267 said:**
> Close, it should be:
```
find ~/.irssi/irclogs -name "*.log" -exec grep -H "irssi" {} \;
```$HOME just means your home directory, you would usually start a command with the name of an executable to run.

The "-H" means grep will print out the file name if it finds a match. I usually want this option enabled when using grep with find but you might not. You can use the "-i" option for grep if you want the grep to be case insensitive too.

If you want to output the result of a command to a file then just add " > filename.txt" at the end.

Works great, thanks! :) 

Could we an an argument  to search for lines with the string "irssi", but don't include those that also contain the string "quit"?

---

### Post by ad_267 on 2010-10-29
Yeah one way would be to pipe the output of that command into another grep that removes any lines containing quit.

So the full command with the output going to a file would be:

```
find ~/.irssi/irclogs -name "*.log" -exec grep -H "irssi" {} \; | grep -v "quit" > filename.txt
```

The "|" sends the output from the first find command into the second grep and the "-v" option means invert, so it outputs any lines that don't contain quit.

Another way might be to use a regular expression with just the one grep that matched lines containing irssi but not quit.

---

### Post by Dáire Fagan on 2010-11-01
> **ad_267 said:**
> Yeah one way would be to pipe the output of that command into another grep that removes any lines containing quit.

So the full command with the output going to a file would be:

```
find ~/.irssi/irclogs -name "*.log" -exec grep -H "irssi" {} \; | grep -v "quit" > filename.txt
```The "|" sends the output from the first find command into the second grep and the "-v" option means invert, so it outputs any lines that don't contain quit.

Another way might be to use a regular expression with just the one grep that matched lines containing irssi but not quit.

Thanks :) 

Grep seems like a very cool and powerful tool which I look forward to learning to use.

---

