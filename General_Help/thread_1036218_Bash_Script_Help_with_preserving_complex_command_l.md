---
title: "Bash Script: Help with preserving complex command line aruments"
date: 2009-01-10
forum: General Help
---

### Post by starfry on 2009-01-10
Hi,
I'm pulling my hair out on this one... I have a script and it needs to be able to execute itself passing in the command line arguments it was invoked with, plus a few others. 

Some arguments are of the form --parameter="complex value".

My problem is that the quotes around "complex value" get stripped when the script invokes itself, resulting in the parameters being parsed incorrectly.

I've written a test script to demonstrate the problem:

```

#!/bin/bash
echo "---------------------------start of script"
echo "Received argument list:$@"

for i in "$@"
do 
    echo "Parameter found:$i"
    case $i in
        --param=*)
            PARAM=`echo $i | sed 's/[-a-zA-Z0-9]*=//'`
            ;;
        --recalled)
            RECALLED=TRUE
            ;;
    esac
done

if [ -n "$PARAM" ]
then
    echo "Parameter is >$PARAM<"
fi

if [ $RECALLED ]
then
    echo "Recalled"
else
    echo "Not Recalled, calling $0 again"
    command="$@"
    echo "Sending argument list:$command"
    /bin/bash -c "$0 --recalled $command"
fi
echo "-----------------------------end of script"

```

Executing this script gives this output:

```

$ /tmp/test --p1 --param="complex string"
---------------------------start of script
Received argument list:--p1 --param=complex string
Parameter found:--p1
Parameter found:--param=complex string
Parameter is >complex string<
Not Recalled, calling /tmp/test again
Sending argument list:--p1 --param=complex string
---------------------------start of script
Received argument list:--recalled --p1 --param=complex string
Parameter found:--recalled
Parameter found:--p1
Parameter found:--param=complex
Parameter found:string
Parameter is >complex<
Recalled
-----------------------------end of script
-----------------------------end of script

```

As you can see, on the first invocation the --param="complex string" is successfully parsed on the first call but is seen as separate arguments on the second call.

I've tried so many ways to do this now, I hope I am missing something obvious. Any solution to this would be greatly appreciated if there's anyone that knows how to solve this...

---

### Post by sdennie on 2009-01-10
Have you tried passing "complex value" as 'complex value'?  The single quotes should never be seen by the shell.

---

### Post by starfry on 2009-01-10
Yes, same result:

```

/tmp/test --p1 --param='complex string'
---------------------------start of script
Received argument list:--p1 --param=complex string
Parameter found:--p1
Parameter found:--param=complex string
Parameter is >complex string<
Not Recalled, calling /tmp/test again
Sending argument list:--p1 --param=complex string
---------------------------start of script
Received argument list:--recalled --p1 --param=complex string
Parameter found:--recalled
Parameter found:--p1
Parameter found:--param=complex
Parameter found:string
Parameter is >complex<
Recalled
-----------------------------end of script
-----------------------------end of script

```

---

### Post by schilcha on 2009-01-10
What seems to work is
```


[... quite some code above ...]

if [ $RECALLED ]
then
    echo "Recalled"
else
    echo "Not Recalled, calling $0 again"
    $0 --recalled "$@"
fi

[... some lines to follow ...]

```

This is a little simpler than your code (no explicit shell invocation, no separate assembly of the command). However, it seemed that the use of too many double quotes destroyed the inteded quoting-structure. 

The above code behaves pretty much as expected (see bash-man-page):
> "$@" is equivalent to "$1" "$2" ...

Best,
   schilcha

---

