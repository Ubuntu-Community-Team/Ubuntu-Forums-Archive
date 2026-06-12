---
title: "Bash script: File as argument"
date: 2009-02-24
forum: General Help
---

### Post by goldfish2 on 2009-02-24
I'm writting a bash script and am struggling to parse all the various ways someone could write a file in like:

```
$script ../input.txt
$script ~/input.txt
$script $HOME/test/input.txt
$script /home/goldfish/input.txt
$script input.txt
```

I need to set one variable, dir to the directory, and file to the name of the file.

The ALMOST code I have so far is:
```
dir=$PWD/`dirname $1`
if [ -d $dir ]
then
  dir=$PWD/`dirname $1`
else
  dir=`dirname $1`
fi
file=`basename $1`
```

but this will do funny things like make the directory name:
/home/goldfish/./

Any ideas? I was surpised I didn't see anyone else asking this question... maybe its something obvious.

Thanks,
~GoldFish

---

### Post by soxs on 2009-02-24
because of that behavior: ```
$dirname ./
.

```Edit: Fiddeling with strings and stuff is very nasty with shell. I'd suggest you go for pythion in some time.

EDIT:
This may solve it:
[http://www.unix.com/shell-programming-scripting/36200-getting-full-path-relative-path.html](http://www.unix.com/shell-programming-scripting/36200-getting-full-path-relative-path.html)

---

### Post by goldfish2 on 2009-02-24
Isn't there a much better way to do all of this though?  I could add a couple more if statements to account for various situations... but I'm guessing there is some way to do this in less than 3 lines, isn't this something that is commonly needed?

~GoldFish

---

### Post by heindsight on 2009-02-24
The easiest is:
```

file=${1##*/}
dir=${1%$file}
[ -z "$dir" ] && dir=.
dir=$(readlink -e "$dir")

```

Note though, that ```
readlink -e dir
``` will recursively dereference any symbolic links in dir. So if dir is /foo and /foo is a symbolic link to /bar/baz/ then after readlink, dir will be /bar/baz.

If you want to avoid this, you can use something like:
```

#!/bin/sh

# Convert single argument into an absolute path without 
# any /./ or /../ or sequences of /'s
abspath() {
    local p tmp tmp1 tmp2;

    if [ "${1#/}" != "$1" ]; then
        tmp=$1/
    else
        tmp=$PWD/$1/
    fi

    while [ "$tmp" != "/" ]; do
        tmp1=${tmp#/*/}
        tmp2=${tmp%$tmp1}
        if [ "$tmp2" = "/../" ]; then
            p=${p:+${p%/*/}/}
        elif [ "$tmp2" != "//" -a "$tmp2" != "/./" ]; then
            p=${p%/}$tmp2
        fi
        tmp=/$tmp1
    done
    if [ "${1%/}" = "$1" ]; then
        p=${p%/}
    fi
    echo ${p:-/}
}

file=${1##*/}
dir=${1%$file}
[ -z "$dir" ] && dir=.
dir=$(abspath "$dir")

```

EDIT:
I just discovered a bug causing abspath /foo/.. to give an empty string instead of /
I fixed this by replacing ```
echo $p
``` with ```
echo ${p:-/}
```

---

### Post by goldfish2 on 2009-02-24
Thanks for the link. Guess it looks like there is no magic solution.  Always thought cp/rm/ls handled file inputs so well, but those aren't written in bash of course, which goes along with your suggestion to choose another language.

I'll just add some more conditional statments, thanks.

~GoldFish

---

### Post by goldfish2 on 2009-02-24
Whoa... that is some awesome code.  It works great!

I'm trying to understand it though... what do the % and : symbols do? Like in this statement:
```
p=${p:+${p%/*/}/}
```

Thanks,
~GoldFish

---

### Post by heindsight on 2009-02-24
> **goldfish2 said:**
> Whoa... that is some awesome code.  It works great!

I'm trying to understand it though... what do the % and : symbols do? Like in this statement:
```
p=${p:+${p%/*/}/}
```

Thanks,
~GoldFish

the short answer is RTFM ;)
```
man sh
```

the longer answer is:
```

bar=${p%foo} # bar becomes $p with shortest suffix matching foo stripped off
bar=${p%%foo} # Same as above but strips longest suffix
bar=${p#foo} # strip shortest prefix matching foo from $p
bar=${p##foo} # strip longest matching prefix
bar=${p:+foo} # if $p is empty string or unset: bar is empty string, otherwise bar=foo

```

---

### Post by goldfish2 on 2009-02-24
Thank you for all your help!

Thanks,
~GoldFish

P.S. The man page for sh on my HP-UX box is only 2 pages... and symbols are hard to google, even when spelled out, so thanks for the long version... though I did find a much larger version of the sh man page online which has more in depth information, which you are correct, could have been found if I had been more persistant.

Glad I asked though, because 
```
size=${2:-10}
```
actually comes in rather handy later in my same script to set the default value of size to 10 if the 2nd variable isn't specified.

Thanks Again!

---

### Post by Slim Odds on 2009-02-24
> **goldfish2 said:**
> Whoa... that is some awesome code.  It works great!

I'm trying to understand it though... what do the % and : symbols do? Like in this statement:
```
p=${p:+${p%/*/}/}
```Thanks,
~GoldFish

I always recommend the Advanced Bash Scripting Guide: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

or at least "man bash"    :p

---

### Post by Wayne_V on 2009-02-24
Simplest way I can think of resolving to absolute names is:

```
#!/bin/bash

if [ "x$1" == "x" ]
then
    echo "usage: $0 <filename>"
else
    T=`dirname "$1"`
    F=`basename "$1"`
    D=`cd "$T" && pwd`
    echo $1 is $F in $D
fi
```

---

### Post by heindsight on 2009-02-25
> **Wayne_V said:**
> Simplest way I can think of resolving to absolute names is:

```
#!/bin/bash

if [ "x$1" == "x" ]
then
    echo "usage: $0 <filename>"
else
    T=`dirname "$1"`
    F=`basename "$1"`
    D=`cd "$T" && pwd`
    echo $1 is $F in $D
fi
```

Yes that works, but only if the directory already exists. I originally wrote that abspath function to deal with situations where the directory doesn't necessarily exist.
Of course in such a situation one could just use 
```
mkdir -p "$T"
D=`cd "$T" && pwd`
```
but you don't necessarily always want to create the directory if it doesn't exist. For example, I initially wrote that abspath function for use in constructing a path to use as the target of a symlink and since it is allowed to create a symlink if the target doesn't exist, I didn't want to create the directory just to construct the path.
Of course I could have used ```
readlink -m
```but as I mentioned earlier in this thread, that recursively dereferences any symlinks in the path and that's not always desired.

By the way, just a quick hint. Unless you really need bash specific features it's usually more efficient to use sh rather than bash to execute a script (at least on systems like ubuntu where sh is not symlinked to bash). Also, although it may be a bit more difficult to understand at a glance, using something like:
```
F=${1##*/}
D=${1%$F}
[ -z $D ] && D=.
```
is more efficient than doing:
```
D=`dirname "$1"`
F=`basename "$1"`
```
since the former only uses the shell's built in parameter expansion and the shells builtin [ command, while the latter requires subshells and external commands.

---

