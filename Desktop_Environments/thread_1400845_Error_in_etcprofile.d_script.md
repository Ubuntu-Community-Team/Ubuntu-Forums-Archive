---
title: "Error in /etc/profile.d script"
date: 2010-02-07
forum: Desktop Environments
---

### Post by ajcoon on 2010-02-07
Hi all,

I have a custom script in /etc/profile.d that is causing Gnome login to fail.  It only works when I login using failsafe.

Here is the output from `~/.xsession-errors`:

    ```
/etc/gdm/Xsession: Beginning session setup...
    /etc/profile.d/p4c.sh: 8: Syntax error: "(" unexpected
```


`p4c.sh` is a script that I copied from my previous Ubuntu system - where it worked fine.  Here are the contents of p4c.sh:

    ```
#!/bin/bash
    
    # p4c() function setup params
    p4_HOST=`hostname | awk -F . '{print $1}'`
    
    # function for setting the P4CLIENT variable based on the first non-option
    # argument provided
    function p4client() {
        HELP_MODE=''
        VERBOSE_MODE=''
        DESC_MODE=''
        SHORT_MODE=''
        while getopts ":hdsv" option
        do
            case $option in
                h) echo "p4c provides information about perforce clients."
                   echo "Recognized arguments:"
                   echo "    -h     help (this message)"
                   echo "    -d     descriptions (prints client descriptions - useful, but slightly slower)"
                   echo "    -v     verbose (print unreasonable amounts of debugging info"
                   echo
                   # About to exit - reset OPTIND or we'll be in trouble later.
                   OPTIND=1
                   # Abort
                   return
                   ;;
                v) VERBOSE_MODE='verbose';;
                d) DESC_MODE='descriptions';;
                s) SHORT_MODE='short';;
                *) echo "Unknown option '$OPTARG'!  Specify -h for help..."
                   # About to exit - reset OPTIND or we'll be in trouble later.
                   OPTIND=1
                   # Abort
                   return
                   ;;
            esac
        done
    
        # Set argument pointer to first non-option argument
        shift $(($OPTIND - 1))
    
        # Done with OPTIND - better reset it before something bad happens...
        OPTIND=1
    
        PROJECT=$1;
        if [ $VERBOSE_MODE ]
        then
            echo "PROJECT: $PROJECT"
        fi
    
        # Need to check/set p4_USER every time to allow changes between invocations
        if [ -z "$p4c_USER" ]
        then
            p4_USER=`echo $P4USER`
            if [ -z "$p4_USER" ]
            then
                p4_USER=`id -nu`
            fi
        else
            p4_USER=$p4c_USER
        fi
        if [ $VERBOSE_MODE ]
        then
            echo "p4_USER: $p4_USER"
        fi
    
    
        if [ -n "$PROJECT" ]
        then
            # provided a non empty string project name
            p4_CLIENT=$p4_HOST-$p4_USER-$PROJECT
            if [ $VERBOSE_MODE ]
            then
                echo "p4_CLIENT: $p4_CLIENT"
            fi
    
            # check client to see if it exists
            p4_GREP_RESULT=`p4 clients | grep "$p4_CLIENT"`
            if [ -z "$p4_GREP_RESULT" ]
            then
                echo "NOTE: P4 client \"$p4_CLIENT\" does not exist on server."
                echo "Setting P4CLIENT anyway so that client \"$p4_CLIENT\" can be created."
                echo
            fi
    
            export P4CLIENT=$p4_CLIENT;
        else
            # check for client matches
            p4_GREP_RESULT=`p4 clients | egrep "($p4_HOST-$p4_USER-|$p4_USER-$p4_HOST-)" | awk '{print $2;}'`
            echo "Known workspaces for user $p4_USER, host $p4_HOST:"
            if [ -z "$p4_GREP_RESULT" ]
            then
                echo "None found."
            else
    #            echo "$p4_GREP_RESULT"
                for result in `echo $p4_GREP_RESULT`
                do
                    if [ $DESC_MODE ]
                    then
                        comment=`p4 clients | grep "\<$result\>" | awk -F "'" '{print $2;}' | sed 's/[  ]*$//'`
                        echo "$result ($comment)"
                    else
                        echo "$result"
                    fi
                done
            fi
            echo
        fi
        if [ $DESC_MODE ]
        then
            comment=`p4 clients | grep "\<$P4CLIENT\>" | awk -F "'" '{print $2;}' | sed 's/[    ]*$//'`
            echo "Current P4CLIENT=$P4CLIENT ($comment)";
        else
            echo "Current P4CLIENT=$P4CLIENT";
        fi
    }
    
    export p4c

```


Could anyone please tell me what I need to change in this script to make it compatible?  It worked fine on my previous Ubuntu system.


Thanks in advance,

-aj

---

### Post by warp99 on 2010-02-07
In line 8 remove the term "function". So from this:

```
 function p4client() {
```

to this:

```
 p4client() {
```

I'm not a script expert, but I don't believe you need to use the term since the interpreter already knows this. This is most likely why you're getting the "(" error.

---

### Post by falconindy on 2010-02-07
> **warp99 said:**
> In line 8 remove the term "function". So from this:

```
 function p4client() {
```

to this:

```
 p4client() {
```

I'm not a script expert, but I don't believe you need to use the term since the interpreter already knows this. This is most likely why you're getting the "(" error.
This is valid actually. Older syntax says to use the 'function' keyword. Now you can just use () after the name to denote a function. Using both is fine, but you should pick one or the other.

What I notice is this:
```
p4_HOST=`hostname | awk -F . '{print $1}'`
p4client() { ... }
export p4c
```
Bit of a disconnect here... You're exporting nothing.

---

