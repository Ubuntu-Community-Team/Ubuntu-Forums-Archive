---
title: "Bash shell Problem with let command in Ubuntu 10.04"
date: 2011-04-22
forum: Desktop Environments
---

### Post by webusr1 on 2011-04-22
Can anyone help with getting the all Bash shell commands in Ubuntu 10.04 working. I'm taking a Linux OS class and now as I try to work on shell scripting I've discovered that the Bash shell in Ubuntu 10.04 doesn't recognize many commands. For example, the simple let command doesn't work, here's my terminal output and file contents.

file: testscr
etcmon@etcmon-laptop:~$ cat testscr 
let x=100
echo $x


etcmon@etcmon-laptop:~$ sh testscr 
testscr: 1: let: not found

Any HELP would .be greatly appreciated.

Thanks

---

### Post by holiday on 2011-04-22
> **webusr1 said:**
> Can anyone help with getting the all Bash shell commands in Ubuntu 10.04 working. I'm taking a Linux OS class and now as I try to work on shell scripting I've discovered that the Bash shell in Ubuntu 10.04 doesn't recognize many commands. For example, the simple let command doesn't work, here's my terminal output and file contents.

file: testscr
etcmon@etcmon-laptop:~$ cat testscr 
let x=100
echo $x


etcmon@etcmon-laptop:~$ sh testscr 
testscr: 1: let: not found

Any HELP would .be greatly appreciated.

Thanks

In Ubuntu, the /bin/sh link points to dash. So you will have to specify bash in your script. 

#!/bin/bash
let x=100
echo $x

Make the file executable and run it.

$ chmod +x testscr
$ ./testscr

or 

$ bash testscr

---

### Post by shashanksingh on 2011-04-22
use "bash" instead of "sh"

It'll work

---

### Post by sisco311 on 2011-04-22
EDIT: I'm too slow. holiday and shashanksingh beat me to it. :)

In Ubuntu, the default system shell, /bin/sh, is [dash]("http://en.wikipedia.org/wiki/Debian_Almquist_shell"). See: [uwiki] DashAsBinSh[/uwiki]

let is a bash builtin command, so if you want to run your script in bash, run:
```
bash script
```

Or make your script executable and use a [shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)"):
```

sisco@acme:~$ chmod +x script
sisco@acme:~$ cat script
#!/bin/bash

let x=100
echo $x

sisco@acme:~$ ./script

```

---

### Post by shashanksingh on 2011-04-23
> **sisco311 said:**
> EDIT: I'm too slow. holiday and shashanksingh beat me to it. :)

In Ubuntu, the default system shell, /bin/sh, is [dash]("http://en.wikipedia.org/wiki/Debian_Almquist_shell"). See: [uwiki] DashAsBinSh[/uwiki]

let is a bash builtin command, so if you want to run your script in bash, run:
```
bash script
```

Or make your script executable and use a [shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)"):
```

sisco@acme:~$ chmod +x script
sisco@acme:~$ cat script
#!/bin/bash

let x=100
echo $x

sisco@acme:~$ ./script

```

I have a doubt.
When I checked my /etc/passwd
bash was the default shell for both root as well as for myself

but when I executed the above script, it still runs on dash???

---

### Post by webusr1 on 2011-04-23
Thanks guys! Adding shebang to line one and making testscr file executable solved my problems. Moving ahead learning Linux on Ubuntu 10.04!!! 

Here's my terminal output:

etcmon@etcmon-laptop:~$ chmod 755 testscr 
etcmon@etcmon-laptop:~$ ls -l testscr 
-rwxr-xr-x 1 etcmon etcmon 19 2011-04-22 12:26 testscr
etcmon@etcmon-laptop:~$ head testscr 
#!/bin/bash
let x=100
echo $x
 
etcmon@etcmon-laptop:~$ ./testscr 
100

---

### Post by rafia2k on 2012-06-21
> **holiday said:**
> In Ubuntu, the /bin/sh link points to dash. So you will have to specify bash in your script. 

#!/bin/bash
let x=100
echo $x

Make the file executable and run it.

$ chmod +x testscr
$ ./testscr

or 

$ bash testscr

It is working thanks

---

