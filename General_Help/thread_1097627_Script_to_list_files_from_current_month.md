---
title: "Script to list files from current month"
date: 2009-03-16
forum: General Help
---

### Post by Throwie on 2009-03-16
Hi guys I'm sort of new to linux and I'm wondering how I would create an executable (using vim) to create a listing which displays only files created in the current month and year in the current directory or perhaps even other directories?

---

### Post by unutbu on 2009-03-16
To list all the files in the current directory which have been modified in the last 30 days, you could run this command:
```
find . -type f -mtime -30
```
Change 30 to 365 to find files changed in the last 365 days.

I'm not sure this matters to you, but to be precise, the original creation date of a file is not information that is saved by ext3 filesystem. (ext3 is the default filesystem type used by Ubuntu). Only the last times when the file has been modified, accessed or changed is saved.

---

### Post by heindsight on 2009-03-16
Well, first of all, it's not really possible to find files based on the time they were created. Your filesystem stores three timestamps for each file:
[LIST]
[*]The time the file was last **accessed** (ie. when the contents were last read)
[*]The time the file was last **modified** (ie. the last time the contents changed)
[*]The time the file status was last **changed** (ie. the last time file permissions or ownership or something like that changed)
[/LIST]

You can use the find command to find files based on any of those timestamps. The find command's time options are rather tricky to use though since it only allows you to search based on how many days (or minutes) ago the file was accessed, modified or changed rather than letting you specify a specific time to compare to.

With that in mind, here's a little shell script that will find files in a specified set of directories that were last accessed/modified/changed in the past n months or years.

```

#!/bin/sh

N=0
PERIOD="m"
TYPE="m"
NOW=$(date +%s)
SCRIPTNAME=${0##*/}
USAGE="Usage: $SCRIPTNAME [-n N] [-p y|m] [-t a|c|m] DIRS
    find files in a specified set of directories that were last
    accessed/modified/changed in the past N months or years.

OPTIONS:
    -h          Show this help and exit.
    -n N        Find files with timestamps more recent than the
                start of the Nth month or year before the current
                date. The default, 0 means since start of current
                month/year.
    -p [y|m]    The unit for N, either months or years (default: m).
    -t [a|c|m]  Which timestamp to use: atime, ctime or mtime. (default: m)"


# Compute the number of days since the start of the Nth
# month or year before now.
getdays() { # $1: N, $2 : month or year
    local THEN DELTA TMPD MNTH
    case "$2" in
        "month") MNTH="%m";;
        "year") MNTH="01";;
    esac
    TMPD=$(date -d "$1 $2 ago" "+%Y-$MNTH-01")
    THEN=$(date -d "$TMPD" +%s)
    DELTA=$((NOW - THEN))
    echo $((DELTA/86400))
}

# Parse Command line options
while getopts "n:p:t:h" O; do
    case "$O" in
        n) N=$OPTARG;;
        p) PERIOD=$OPTARG;;
        t) TYPE=$OPTARG;;
        h) echo "$USAGE"; exit 0;;
        \?) echo "$USAGE" >&2; exit 1;;
    esac
done

shift $(expr $OPTIND - 1)

case "$PERIOD" in
    "m") PERIOD="month";;
    "y") PERIOD="year";;
    *)  echo "Unrecognised argument to -p: $PERIOD" >&2
        echo "$USAGE" >&2
        exit 1;;
esac

if [ $N -lt 0 ]; then
    echo "Invalid argument to -n: $N" >&2
    echo "$USAGE" >&2
    exit 1
fi

NDAYS=$(getdays $N $PERIOD)

case "$TYPE" in
    "a") find "$@" -daystart -atime -$NDAYS;;
    "c") find "$@" -daystart -ctime -$NDAYS;;
    "m") find "$@" -daystart -mtime -$NDAYS;;
    *) echo "Unrecognised argument to -t: $TYPE" >&2
       echo "$USAGE" >&2
       exit 1;;
esac

```
EDIT {
Save it as (for example) ~/find_date.sh, give it execute permission and then run it as:
```
~/find_date.sh /etc
```
to find all files under /etc that have been modified since the beginning of this month.
OR
```
~/find_date.sh -n 1 -p y -t c /etc /usr
```
To find all files under /etc or /usr that have been changed since the beginning of last year.
}

A large part of this is just dealing with command line arguments etc.
The important parts are:
```

NOW=$(date +%s)

getdays() { # $1: N, $2 : month or year
    local THEN DELTA TMPD MNTH
    case "$2" in
        "month") MNTH="%m";;
        "year") MNTH="01";;
    esac
    TMPD=$(date -d "$1 $2 ago" "+%Y-$MNTH-01")
    THEN=$(date -d "$TMPD" +%s)
    DELTA=$((NOW - THEN))
    echo $((DELTA/86400))
}
```
Which first gets the date of the first day of the Nth month/year before now. Then converts that date to seconds since 1 January 1970, and stores the number of seconds in the variable THEN. It gets the difference in seconds between THEN and NOW (the current time in seconds since 1 Jan 1970) and converts that to a number of days (there are 86400 seconds in a day).
```
NDAYS=$(getdays $N $PERIOD
```
Puts the result of the above in the variable NDAYS

The next important parts are:
```
find "$@" -daystart -atime -$NDAYS
```
```
find "$@" -daystart -ctime -$NDAYS
```
```
find "$@" -daystart -mtime -$NDAYS
```
which tell find to search for files last accessed/changed/modified less than NDAYS days ago (where the number of days ago is measured from the start of today, rather than from the current time).

Have a look at the manuals for the find and date commands as well as the shell manual for more detail:
```
man find
```
```
man date
```
```
man sh
```

---

### Post by Throwie on 2009-03-16
Thanks for the help guys.

So I will be listing the files last modified in the current month from the current directory

Can this be done with a variation of ls and then trimming some stuff? or do I have to use find

I'd rather not have it list hidden files so the screen is flooded

---

### Post by unutbu on 2009-03-17
I believe there is no way to do this with ls alone.

If you'd like to get an ls-style listing of the files, you could do something like this:

```
find /path/to/dir/ -maxdepth 0 -name ".*" -prune -o -mtime -30  -exec ls -l {} \;

```
This will list all files in the top level of /path/to/dir/ which has been modified in the past 30 days and which is not a hidden file.

If you'd like to list all files -- even in subdirectories -- then use```


find /path/to/dir/ -name ".*" -prune -o -mtime -30  -exec ls -l {} \;
```

Note: for some reason, for the above commands to work, it appears to be necessary that you specify a path to the directory in some way other than through use of '.' to indicate the current directory. Also, you must include the trailing slash (/) at the end of the directory path.

---

### Post by Throwie on 2009-03-17
Okay, thanks.

So if type that into vim I could use the program from the directory its placed in just by typing ./script (assuming i name it script) and it will list all files in that directory that have been modified in the last 30 days?

---

### Post by heindsight on 2009-03-17
> **unutbu said:**
> 
Note: for some reason, for the above commands to work, it appears to be necessary that you specify a path to the directory in some way other than through use of '.' to indicate the current directory. Also, you must include the trailing slash (/) at the end of the directory path.

I believe part of the problem may be that you used **-maxdepth 0** which means that  find doesn't descend into any of the directories specified on the command line - it only applies the tests to command line arguments.

Also your use of **-prune** is preventing find from descending into the directory ".", even when maxdepth is increased to 1. That prevents it from working when . is specified as command line argument.

I didn't try the second command you gave but the first seemed to mostly work well enough when I changed the maxdepth to 1, added a -d option to ls and switched from -exec .... **;** to -exec ... **+** (gives nicer output).

Anyway this is another way of doing it:
```
#!/bin/sh
find "$@" -maxdepth 1 -daystart \( -not -name ".*" -mtime -30 \) -exec ls -ltd \{\} +
```

(save it in a file, give it execute permission and then run it, specifying the directories you want to search as command line arguments)

---

### Post by kevdog on 2009-03-17
Could you use $pwd instead of . to represent the current working directory?

---

### Post by unutbu on 2009-03-17
Thank you for the explanation and improvements, heindsight!

---

