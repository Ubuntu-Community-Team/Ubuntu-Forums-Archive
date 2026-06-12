---
title: "Help with mv bash script"
date: 2008-12-21
forum: General Help
---

### Post by Folditron on 2008-12-21
Skip to next paragraph for the meat of the problem, here's the backstory. We run a samba sever on a desktop in the living room to share media amongst the computers scattered throughout the house. We also run all our bittorrent downloads through the living room server. I have vuze setup to pick up torrents when they are dropped into a folder on the shared drive. As an exercise in beginner script writing and convenience I would like to automate this process.

I would like to write a script to automatically move a file downloaded in firefox. i.e. When I download a file and firefox asks me what to do with it I tell it to open with this script which in turn moves it to the place established in the script.

I can make my way around a terminal ok, but I get pretty lost reading other people's scripts. And I want to learn so pontificate at length and please post links to any good scripting tutorials.

Thanks

---

### Post by pytheas22 on 2008-12-21
If I understand your objective correctly, this would actually be quite simple--just a one-line script.  It would look something like:
```

#!/bin/bash

mv $1 /path/to/torrent/folder
```

'$1' in bash means the first command-line argument ('$2' is the second and so on)--so in your case, that translates to the torrent file that you're downloading through Firefox and opening with the bash script.

The /path/to/torrent/folder is the location where you want the torrent file to be dropped into, obviously.  If it's on a remote machine, you would need to specify the IP address, protocol, etc.  But it sounds like the shared folder is on the local machine so you shouldn't need to worry about this.

Remember to make your script executable using a command like:
```

chmod +x /path/to/script.sh
```

Let me know if you have any questions.  I don't know of any single good site for bash-scripting how-to's, but there's an abundance of stuff out there that you can find through Google.

---

### Post by Folditron on 2008-12-21
Thanks, works like a charm. I've looked at a few tutorials, but this is the best newbie tutorial I've found so far [Link]("http://www.linuxconfig.org/Bash_scripting_Tutorial").

---

### Post by ibuclaw on 2008-12-21
Bash will only get you so far in writing short scripts for small jobs.

I actually find myself writing them in **Perl** nowadays, or **Python** in the very very rare occasion.


One note I'd like to point out is: **Avoid Pipes, if at all necessary**, the chances am that you can achieve the task with just one command.

Take this pipe for example:
```
cat foo | grep 'abc' | tr [:lower:] [:upper:] | head -n 13
```
This is the output from the command **time**:
> 
real    0m0.020s
user    0m0.008s
sys     0m0.012s

Not bad, it took a 200ths of a second to finish... but we can do better...
Here is the exact same code, but written in sed
```
sed -e '/abc/!d' -e 's/\([a-z]\)/\U\1/g' -e '13q' foo
```
and the output from the command **time**:
> 
real    0m0.005s
user    0m0.000s
sys     0m0.004s

FOUR times quicker...

The best places to use pipes, in my opinion, are in loops.
ie: This will print "abc" in the file foo 100 times
```
seq 100 | while read a; do echo "$a: abc" >> foo; done
```
A more indepth explanation:
seq will print out the numbers from 1 to 100. Those numbers get piped to the read command, which assigns them to **a** and echo prints them out.
The resultant print gets appended to the file 'foo'.

To show a better example, here is one I made that parses out a configuration file, and sets the system setting stored in that file accordingly:
```

sed '/^#\|^$/d; s/^\s*\(.*\)\s*=\s*\(.*\s*\)*$/\/sys\/\1\2/' $CONF | \
while read path value
do [ -f $path ] && echo $value > $path || echo "Warning: File $path does not exist"
done

```

Confused?

You will be to start off with... unix shell scripting is one of the most difficult of languages to master, since your only limit are the amount of applications you have... but the amount of applications to choose from is, quite frankly, limitless.

Regards
Iain

---

### Post by dagnabit dang doohickey on 2008-12-21
The following script will look for torrent files in *watchdir* every 30 seconds and, if any are found, move them to *mv2dir*. The script will exit if *browser* is not running.
```

#!/usr/bin/env bash

# torrent-watch.sh
#
# This script will look for torrent files in the _watchdir_ directory
# every 30 seconds and move any that are found to the _mv2dir_
# directory. A log file is saved in the _mv2dir_ directory. If
# _browser_ is set, the script will exit if _browser_ is not running.
#
# The script must be run in a terminal.
# example: xterm -e torrent-watch.sh
#
# Start the script automatically with your browser by adding
# torrent-watch to your browsers launch command.
# example: firefox & xterm -iconic -e torrent-watch.sh

watch -n 30 ' \
	watchdir="${HOME}/Desktop"; \
	mv2dir="${HOME}/torrent_dump"; \
	browser="firefox|opera"; \
	[ -d "$watchdir" -a -d "$mv2dir" ] && \
		ls -1 "$watchdir" | grep ".*\.torrent$" \
			| xargs -r -I '{}' mv -v -t "$mv2dir/" "{}" \
				>> "$watchdir/torrent-watch.log"; \
	[ -f "$watchdir/torrent-watch.log" ] && \
		tail -n 20 "$watchdir/torrent-watch.log"; \
	[ -n "$browser" -a -z "`pgrep -u \"$USER\" \"$browser\"`" ] && \
		kill $PPID \
'

```

---

### Post by Folditron on 2008-12-22
Sorry for getting a bit off topic in the thread, but for me this is totally related. What would anyone recommend as far as books/starting points to gaining a basic understanding of programming? Should I start with perl, C, python? Are O'reilly books worth the fifty bucks each? Ideally I'd like something heavy on theory as languages and fads come and go.
I'm currently on a sort of slacker sabbatical and learning to code sounds like a great project to gainfully occupy my time. 
Thanks again.

---

### Post by dagnabit dang doohickey on 2008-12-22
Bash may be the most immediately useful.

[man bash]("http://linux.die.net/man/1/bash")
[Bash Guide for Beginners]("http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html")
[Advanced Bash-Scripting Guide]("http://tldp.org/LDP/abs/html/index.html")

---

