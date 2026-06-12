---
title: "Extracting hundreds of files to seperate dirs"
date: 2005-06-27
forum: Desktop Environments
---

### Post by WAM on 2005-06-27
I have about 600 seperate .zip or .rar files I need to extract to seperate directores. For the curious, they're manga chapters (legal of course). So, for example, I need to extract manga_ch001.zip to a dir named manga_chap001. It would be great if I could do this in a batch too (like selecting all, right click > extract to,,,)

If anyone knew how I could do this I would be fantastically appreciative.

---

### Post by WAM on 2005-06-27
...and Google-fu reveals a solution, courtesy of Dawid Michalczyk.

[http://comp.eonworks.com/index.html](http://comp.eonworks.com/index.html)

The script is unpack2dir, located at [http://comp.eonworks.com/scripts/unpack2dir](http://comp.eonworks.com/scripts/unpack2dir)

Basically, do as follows:

```
sudo gedit /bin/unpack2dir
```
Then copy the following into the file.
```

#! /bin/bash
# #############################################################################

       NAME_="unpack2dir"
    PURPOSE_="unpack zip, tar, tgz, tar.gz, tar.bz2, tar.z to a dir of the same name as archive prefix"
   SYNOPSIS_="$NAME_ [-vhlr] <file> [file...]"
   REQUIRES_="standard GNU commands"
    VERSION_="1.1"
       DATE_="1999-09-20; last update: 2005-03-01"
     AUTHOR_="Dawid Michalczyk <dm@eonworks.com>"
        URL_="www.comp.eonworks.com"
   CATEGORY_="compress"
   PLATFORM_="Linux"
      SHELL_="bash"
 DISTRIBUTE_="yes"

# #############################################################################
# This program is distributed under the terms of the GNU General Public License

usage () {

echo >&2 "$NAME_ $VERSION_ - $PURPOSE_
Usage: $SYNOPSIS_
Requires: $REQUIRES_
Options:
     -r, remove the compressed file after extraction
     -v, verbose
     -h, usage and options (help)
     -l, see this script"
    exit 1
}

# args check
[ $# -eq 0 ] && { echo >&2 missing argument, type $NAME_ -h for help; exit 1; }

# var init
rmf=
verbose=

# option and argument handling
while getopts vhlr options; do

    case $options in
        r) rmf=on ;;
        v) verbose=on ;;
        h) usage ;;
        l) more $0; exit 1 ;;
       \?) echo invalid argument, type $NAME_ -h for help; exit 1 ;;
    esac

done
shift $(( $OPTIND - 1 ))

mkdirf() {

    # usage: fnc <file_prefix> <file>

    [ -d $1 ] && { echo "${NAME_}: skipping ${2} - dir ${1} already exist" ; continue; }
    mkdir $1
#    [[ $verbose ]] && echo "${NAME_}: unpacking "$2
}

file_getDirname() {

    local _dir="${1%${1##*/}}"
    [ "${_dir:=./}" != "/" ] && _dir="${_dir%?}"
    echo "$_dir"

}

file_getBasename() {

    local _name="${1##*/}"
    echo "${_name%$2}"

}

clean() {

    # usage <exit_status> <dir_to_rm>

    [[ $1 != 0 ]] && rmdir $2 # remove empty dir if unpacking went wrong
    [[ $1 == 0 && $verbose ]] && echo "${NAME_}: unpacking " ${dir}/${a}
    [[ $rmf ]] && rm -f -- $a

}

start_dir=$(pwd)

for a in "$@"; do

    cd $start_dir        
    fname=$(file_getBasename $a)
    dir=$(file_getDirname $a)
    cd $dir
    a=$fname

    case $a in


        # zip
        *.[zZ][iI][pP])
            mkdirf ${a/.[zZ][iI][pP]/} $a
            unzip -qq $a -d ${a/.[zZ][iI][pP]/}
            clean $? ${a/.[zZ][iI][pP]/}
            ;;

        # tar
        *.[tT][aA][rR])
            mkdirf ${a/.[tT][aA][rR]/} $a
            tar -xf $a ${a/.[tT][aA][rR]/}/
            clean $? ${a/.[tT][aA][rR]/}
            ;;

        # tgz
        *.[tT][gG][zZ])
            mkdirf ${a/.[tT][gG][zZ]/} $a
            tar -xzf $a ${a/.[tT][gG][zZ]/}
            clean $? ${a/.[tT][gG][zZ]/}
            ;;

        # tar.gz 
        *.[tT][aA][rR].[gG][zZ])
            mkdirf ${a/.[tT][aA][rR].[gG][zZ]/} $a
            tar -xzf $a ${a/.[tT][aA][rR].[gG][zZ]/}/
            clean $? ${a/.[tT][aA][rR].[gG][zZ]/}
            ;;

        # tar.bz2
        *.[tT][aA][rR].[bB][zZ]2)
            mkdirf ${a/.[tT][aA][rR].[bB][zZ]2/} $a
            tar -xjf $a ${a/.[tT][aA][rR].[bB][zZ]2/}/
            clean $? ${a/.[tT][aA][rR].[bB][zZ]2/}
            ;;

        # tar.z
        *.[tT][aA][rR].[zZ])
            mkdirf ${a/.[tT][aA][rR].[zZ]/} $a
            tar -xZf $a ${a/.[tT][aA][rR].[zZ]/}/
            clean $? ${a/.[tT][aA][rR].[zZ]/}
            ;;


        *) echo "${NAME_}: $a not a compressed file or lacks proper suffix" ;;

    esac

done

```
```
sudo chmod +x /bin/unpack2dir
```
Then type unpack2dir <files> in a terminal to extract them to directories named after the zip file. You can also do something like:
```
unpack2dir *.zip
```

Once again, all credit goes to Mr. Dawid Michalczyk. Must have saved me hours.

---

### Post by keyshawn on 2005-06-27
wow !!!!!!!!

Thank you for finding this.....I've been looking for something like this for a while...
It will definitely come in handy ! :)

regards,
keyshawn

---

