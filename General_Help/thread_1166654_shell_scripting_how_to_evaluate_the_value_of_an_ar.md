---
title: "shell scripting: how to evaluate the value of an argument with an 'if' statement"
date: 2009-05-22
forum: General Help
---

### Post by motoperpetuo on 2009-05-22
i'm trying to add a "help" option to a script i'm writing. basically, if the user types

```

./script --help

```

he should get a few lines of text explaining how to use the script.

here's one of the many variations i've tried, to no avail:
```

#!/bin/bash
if "$1"="--help"
then
	echo "Help text here."
fi

```

i know the if statement i've got there probably looks ludicrous to someone who knows what he's doing, but apparently i just don't know the syntax for "if the first argument is --help" in bash shell scripting.

very humbling indeed.

---

### Post by lykwydchykyn on 2009-05-22
I can't fault anyone for bungling BASH syntax; it's not exactly what you'd call intuitive.

I rarely write a script without a copy of the BASH beginner's guide open; google it up and give it a look.

You're missing two things:
 - Square brackets around the test condition
 - Using the equality operator (==) not the assignment operator (=)

So your code should look like this:
```

if [ "$1" == "--help" ]
then
    echo "Help text"
fi

```

Now, the only problem with that is if there are no arguments to the script, you'll get an error.  So you might want to test to see if there are arguments first, and only then check what they are.

Frankly, I'd have to believe there are more practical and robust ways of handling command line switches like this, seeing as they are such a common convention.  I don't know off-hand how this is typically handled, though.

---

### Post by lensman3 on 2009-05-22
Go look at the scripts in

/etc/init.d and /etc/rc.d and /etc/sysconfig/network-scripts

One of those will give you the hint.

Also do a "grep bash /usr/bin/*"  (remove the quotes).

The grep will find all the bash scripts in /usr/bin.  Scripts can also be found in /bin, /usr/sbin, and /sbin.

---

### Post by kpkeerthi on 2009-05-22
= is a valid relational operator for strings. The following code will also work.

```

if [ "$1" [COLOR="Red"]=[/COLOR] "--help" ]
then
    echo "Help text"
fi

```

---

### Post by KyleBrandt on 2009-05-22
I wouldn't process command options like that.  Here is an example of a standard way of doing this:

```
# Parse options
while [ $# -gt 0 ]; do
        case $1 in
                -t)     
                        shift
                        tapedev=$1
                        ;;
                -b)
                        shift
                        backupdir="$1"
                        ;;
                -r)
                        shift
                        restoredir="$1"
                        ;;
                -l)
                        shift
                        log="$1"
                        ;;
                -m)     
                        shift
                        rmode="$1"
                        ;;
                *)
                        echo "!!! ERROR: Unrecognized or trailing option: $1"
                        print_usage
                        exit 1
        esac
        shift
done
```

In this case, print_usage is a function that prints help information.  * is the last resort if nothing else matches, so if they type anything it will print that.  You could also add a case like ```
--help)
```

---

### Post by sedawk on 2009-05-22
For parsing and handling the typical command line options you
can use bash's built-in command getopts.
Or you can check gnu's getopt which for example allows long
options like "--help".
This can simplify command line parsing a lot (e.g. to correctly
handle option with and without parameter and in short and
long format like -v=--verbose or -o filename = --output=filename)

---

### Post by motoperpetuo on 2009-05-23
thanks very much to lykwydchykyn and kpkeerthi, both of your syntax suggestions worked. thanks also to the others who posted. i'm still at beginner level with scripting, but i think all of your suggestions will be helpful as i try to learn more.

---

### Post by motoperpetuo on 2009-05-23
btw, is there still a way to officially thank people who make helpful posts? what about some way for me to mark this thread as "solved"? it's been a while since i've been on the ubuntu forums, and it seems like there have been some significant changes.

---

