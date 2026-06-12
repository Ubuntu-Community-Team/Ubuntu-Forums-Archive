---
title: "&quot;grep -q ...&quot; unexpectedly returns 0 in scripts run from Caja in Mate desktop"
date: 2019-02-13
forum: Desktop Environments
---

### Post by stevew-purdue on 2019-02-13
Hi,

I've run into an interesting problem with Caja that crops up from time to time on different workstations in our group. Users began complaining that when they double-click on a LibreOffice document nothing happens. If the user logs out and then logs in again, the problem disappears. But it will then reappear after some time (it can be days before it reappears, though). I found that the script /usr/lib/libreoffice/program/soffice was always evaluating the following condition as true and exiting regardless of the value of the $checks variable:
```

    if echo "$checks" | grep -q "cc" ; then
        echo "Error: The debug options --record, --backtrace, --strace, and --valgrind cannot be used together."
        echo "       Please, use them one by one."
        exit 1;
    fi

```

Using a small test script, I was able to see that "grep -q ..." would always return 0 (zero) when run from Caja regardless of whether grep located an occurence of the specified string or not. If, though, I run the test script from Caja using the "Run in Terminal" option then the script works as expected.

Environment:
    
[LIST]
[*]Ubuntu 18.04
[*]MATE
[*]Caja 1.20.2 (and perhaps other versions)
[/LIST]

I hope I've adequately explained this rather strange scenario. If not, please feel free to ask for clarifying information.

Thanks for any ideas of what may be causing this and/or how to prevent it from happening!

Steve

---

### Post by The Cog on 2019-02-13
I would probably add lines to clear and then output debug info to a file in /tmp, e.g.
```
echo checks="$checks" > /tmp/checksfound
echo GDBTRACECHECK="$GDBTRACECHECK" >> /tmp/checksfound
echo STRACECHECK="$STRACECHECK" >> /tmp/checksfound
echo VALGRINDCHECK="$VALGRINDCHECK" >> /tmp/checksfound
echo RRCHECK="$RRCHECK" >> /tmp/checksfound
```
Then you can look and see which checks were positive (I guess some are)

---

### Post by stevew-purdue on 2019-02-14
Thanks for the suggestion but, yes, I already did that.  The value of the $checks variable was empty (tested by echoing to a file in /tmp).  I then created a simple test script like the following:
```
#!/bin/sh

checks=
echo "$checks" | grep -q "cc"
echo "[$checks]: $?" >> /tmp/test.debug

checks=cc
echo "$checks" | grep -q "cc"
echo "[$checks]: $?" >> /tmp/test.debug

```

The results when run from the command line are as expected:[INDENT][]: 1[/INDENT]
[INDENT][cc]: 0[/INDENT]

But when run from Caja, the results are:[INDENT][]: 0[/INDENT]
[INDENT][cc]: 0[/INDENT]

Having the user logout and login again corrects the problem but only for a while since the problem will usually reappear at some point in the future.

Steve

---

### Post by The Cog on 2019-02-14
I don't understand that. I thought for a minute that the exit value from echo was being carried through the pipeline, but I can't find a setting that might do that. I found this page: [https://vaneyckt.io/posts/safer_bash_scripts_with_set_euxo_pipefail/](https://vaneyckt.io/posts/safer_bash_scripts_with_set_euxo_pipefail/) but I don't see anything there that would do it.
Try printing the exit value of **echo "" | grep -q "cc"** or try **set -x** at the top of your test script to see the args. 

I'm baffled too.

---

### Post by stevew-purdue on 2019-02-15
So I changed my test script a little so that the pipe is removed and grep is searching a file instead:
```
#!/bin/sh

checks=
#echo "$checks" | grep -q "cc"
echo "$checks" > /tmp/checks.debug
grep -q "cc" /tmp/checks.debug
echo "[$checks]: $?" >> /tmp/test.debug


checks=cc
#echo "$checks" | grep -q "cc"
echo "$checks" > /tmp/checks.debug
grep -q "cc" /tmp/checks.debug
echo "[$checks]: $?" >> /tmp/test.debug
```

The results remain the same.  The exit code from both grep commands is zero:
```
[]: 0
[cc]: 0
```

---

### Post by The Cog on 2019-02-15
Something must be changing. Something we haven't thought of, obviously. Try saving the output of **env** in both cases and looking to see what's different there.

---

### Post by stevew-purdue on 2019-02-15
I grabbed the output of env while 1) running directly from Caja and 2) running from Caja using the "run in terminal" mode.  Here are the only differences (these are IN the environment when run in terminal mode but not int the environenment when run directly from Caja):
> COLORTERM=truecolor
> WINDOWID=70374258
> TERM=xterm
> VTE_VERSION=5202

I also found that that Nemo demonstrates the same problem as Caja.

---

