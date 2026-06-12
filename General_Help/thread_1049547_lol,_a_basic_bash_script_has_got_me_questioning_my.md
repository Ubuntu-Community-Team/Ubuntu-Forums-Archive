---
title: "lol, a basic bash script has got me questioning my sanity."
date: 2009-01-24
forum: General Help
---

### Post by Orange Luna on 2009-01-24
hello all.  I got a basic, or maybe not so basic question, about a bash script.  It seems really very basic, but I can't figure out why its not working, so I'm referring it to experts.

I'd like a bash script that can toggle apache on and off again.  Seems like it be real basic but it just doesn't work.  Here's the script:

```
#!/bin/bash
# apachtoggle

if ps -A | grep "apache" > /dev/null; then
    /etc/init.d/apache stop; else
    /etc/init.d/apache start
fi
```

The script will stop apache if it's running but if it is not it will tell me that apache is already stopped.  If I run "ps -A | grep "apache"" while apache is stopped it does return nothing.  Any idea why the script won't start apache?

---

### Post by Gen2ly on 2009-01-24
sometimes a quirk in bash will do this, try loggin in and out again.

---

### Post by gmjs on 2009-01-24
Hi OrangeLuna,

I'm not very good with bash scripts (they're on my 'to learn' list!) but I don't follow the redirection to **/dev/null** at all.

Also, the apache daemon is called **httpd** by default and not 'apache'.

The following code will print "start" if **httpd** is not running and "stop" if it is.

```
#!/bin/bash

test=$(ps -A | grep httpd);

if [ -z "$test" ]; then
  echo 'start'; else
  echo 'stop';
fi
```

Hope this helps,

Graham

---

### Post by kerry_s on 2009-01-24
```
#!/bin/sh
# apache-toggle

if pidof apache | grep [0-9] > /dev/null; then 
    exec /etc/init.d/apache stop
 else
    exec /etc/init.d/apache start
fi
```

the first line might be even easier:
```
if `pidof apache` > /dev/null; then
```

---

### Post by dcstar on 2009-01-24
> **Orange Luna said:**
> hello all.  I got a basic, or maybe not so basic question, about a bash script.  It seems really very basic, but I can't figure out why its not working, so I'm referring it to experts.

I'd like a bash script that can toggle apache on and off again.
.......

```
man start-stop-daemon
```

All system processes already have scripts in /etc/init.d that do these things.

---

### Post by Orange Luna on 2009-01-25
Thanks guys, I got it... down!

@ Dirk

yeah that did it, pretty weird.

@ gmjs

FYI, or maybe not ;)

/dev/null is defined as literally nothing.  When asking if something is greater than /dev/null you ask if the command produces a positive output, i.e. that is... anything.

@ kerry, your bash script is alot better, good thinking.

---

### Post by sdennie on 2009-01-25
You can also use pgrep instead of pidof:

```

if pgrep httpd > /dev/null; then

```

pgrep is like grep but for running processes.

---

### Post by skoorbevad on 2009-01-26
Sometimes your grep command will show up in the process list, also, thus returning a positive result when you didn't mean for it to.  Try:

```

ps -A | grep apache | grep -v grep

```

...to weed out any trailing grep processes which may produce an erroneous result.  The output to /dev/null is also not helping, you might which to add in the "-q" option to grep to basically make it return nothing to STDOUT or STDERR (useful when the exit status of grep is all you're after).

To confuse things more, sometimes bash may not find the original apache process, but will then find the final grep process, producing a false positive.  In this case, you can use the "pipefail" option to bash to return the exit status of the left-most command in a pipe string which failed:

```

(set -o pipefail; ps -A | grep -i apache | grep -vq grep)

```

Hope this helps!

Edit:  'pidof' and 'pgrep' work fine also, as other posters have suggested, and probably won't require any tomfoolery UNLESS the process returns multiple PIDs and you were only looking for one.  It's also not a common utility outside of Linux-based unix derivatives, so consider that also.

---

### Post by Orange Luna on 2009-01-28
good debugging skoorbevad, thanks, i took notes :)

---

