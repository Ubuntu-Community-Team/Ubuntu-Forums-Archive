---
title: "bash scripting help"
date: 2009-03-12
forum: General Help
---

### Post by brainsick on 2009-03-12
I've been banging my head on this for hours now.  I've tried all sorts of variations on quoting this, but nothing has worked.  If I have a script that calls a second script that accepts parameters, how do I build a variable that I can pass to the second script and still have the parameters expanded correctly?

```
todd@carbon:~$ cat test.sh
#!/bin/bash

if [ $# -gt 0 ]; then
    echo \$#: $#
    for param in "$@"; do
        echo $param
    done
    exit 0
fi

# straight-up; how I want this to work
$0 --this=that --some='thing else' --wcard='*'

# double-quoted variable
PARAMS="--this=that --some='thing else' --wcard='*'"
$0 $PARAMS
```

This seems like the logical first choice.  The single quotes are inside double quotes, so they should be left alone and passed as they are, right?

```
todd@carbon:~$ bash -x ./test.sh
+ '[' 0 -gt 0 ']'
+ ./test.sh --this=that '--some=thing else' '--wcard=*'
$#: 3
--this=that
--some=thing else
--wcard=*
+ PARAMS='--this=that --some='\''thing else'\'' --wcard='\''*'\'''
+ ./test.sh --this=that '--some='\''thing' 'else'\''' '--wcard='\''*'\'''
$#: 4
--this=that
--some='thing
else'
--wcard='*'
```

As you can see, they aren't treated the same.

---

