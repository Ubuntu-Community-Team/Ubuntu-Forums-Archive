---
title: "I need a shell script for an odd task"
date: 2009-05-12
forum: General Help
---

### Post by kobe81 on 2009-05-12
First off, thanks in advance for your help. I'm trying to find a shell script that copies all files in a given directory to folders of their same names. For example in "directory1" I have file1.txt, file2.txt, file3.txt... I'd like to move file1.txt to a directory named "file1", file2.txt to a directory named "file2" and so on. Do anyone have any ideas?

---

### Post by droazen on 2009-05-12
Here you go...

EDIT: Added support for filenames with spaces in them (which would break the original version)

```

#!/bin/bash
#
# Usage: filestodirs directory_name
#
# Moves all files in the specified directory into
# subdirectories of the same name, minus the file
# extension. Assumes that each file name contains only
# one period :)

if [ $# -ne 1 ]; then
    echo "Usage: ./filestodirs directory_name"
    exit 1
fi

cd $1

IFS=$'\n'

for file in `ls -1`
do
    dirname=`echo "$file" | awk -F . '{ print $1; }'`
    mkdir "$dirname"
    mv "$file" "$dirname"
done

exit 0

```

---

### Post by kobe81 on 2009-05-12
Just wanted to say thank you so much, this was a lifesaver.

---

### Post by mobilediesel on 2009-05-12
> **droazen said:**
> Here you go...

```

#!/bin/bash
#
# Usage: filestodirs directory_name
#
# Moves all files in the specified directory into
# subdirectories of the same name, minus the file
# extension. Assumes that each file name contains only
# one period :)

if [ $# -ne 1 ]; then
    echo "Usage: ./filestodirs directory_name"
    exit 1
fi

cd $1

for file in `ls -1`
do
    dirname=`echo "$file" | [COLOR="Red"]**sed 's/\.[^\.]*$//'**[/COLOR]`
    mkdir "$dirname"
    mv "$file" "$dirname"
done

exit 0

```

Using that SED command instead of AWK takes the extension off regardless of the number of dots in the filename. I can't remember where I found that.

---

### Post by droazen on 2009-05-12
> **kobe81 said:**
> Just wanted to say thank you so much, this was a lifesaver.

No problem :) I've edited the original version to support filenames with spaces, in case you need that feature.

---

### Post by droazen on 2009-05-12
> **mobilediesel said:**
> Using that SED command instead of AWK takes the extension off regardless of the number of dots in the filename. I can't remember where I found that.

Nice one! :guitar:

---

### Post by mobilediesel on 2009-05-12
> **droazen said:**
> Nice one! :guitar:

I did notice, however, that if a file is a .tar.gz that SED statement takes just the .gz

---

### Post by apmcd47 on 2009-05-12
Based on droazen's original code:
[PHP]
#!/bin/bash
#
# Usage: filestodirs directory_name
#
# Moves all files in the specified directory into
# subdirectories of the same name, minus the file
# extension.

myname=${0##*/}   # dirname

if [ -z "${1:+set}" ]   # null string if not set
then
   echo "Not enough arguments"
   echo "Usage: ${myname} directory_name [file extension]"
   exit 1
fi

if [ $# -gt 2 ]
then
   echo "Too many arguments"
   echo "Usage: ${myname} directory_name [file extension]"
   exit 1
fi

ext=${2:-"*"}     # substitute "*" if not set

if [ ! -d "$1" ]
then
   echo "$1 is not a directory"
   echo "Usage: ${myname} directory_name [file extension]"
   exit 1
fi
cd $1

ls -1 | while read fn
do
   dn=${fn%.${ext}}            # remove extension
   if [ "${dn}" != "${fn}" ]   # don't do this if extension was not removed
   then
      mkdir -p "${dn}"
      mv "${fn}" "${dn}"
   fi
done


[/PHP]
This version allows you to choose the extension and makes extensive use of shell variable substitution, especially ${#} and ${%}. The former removes a pattern from the beginning of the variable pattern and the latter from the end. One % or # is "non-greedy", two are greedy, e.g. the ```
myname=${0##*/}
``` removes all characters until the last / from the beginning of $0, ```
dn=${fn%.*}
``` would remove only the last extension.

Note also the "bitch and exit" if the first argument isn't a directory.

Note also the use of mkdir -p - should stop mkdir complaining if you have multiple files with the same name but different extensions, e.g. 
```

me.txt
me.jpg

```

> **mobilediesel said:**
> I did notice, however, that if a file is a .tar.gz that SED statement takes just the .gz

If you want to remove multiple "." extensions from the filename change the dn= line to:
```
dn=${fn%%.${ext}}
```

---

### Post by mobilediesel on 2009-05-12
> **apmcd47 said:**
> If you want to remove multiple "." extensions from the filename change the dn= line to:
```
dn=${fn%%.${ext}}
```

Nice! I'm still getting the hang of regular expressions.

Regular expressions can be amazingly simple and amazingly complex at the same time!

---

### Post by bigboy_pdb on 2009-05-12
> **mobilediesel said:**
> Nice! I'm still getting the hang of regular expressions.

Regular expressions can be amazingly simple and amazingly complex at the same time!

It's not a regular expression. It's bash parameter expansion being used in conjunction with bash pattern matching.

The only reason why I'm mentioning it is so that it will save you some trouble when you search for information in the future.

You can use "man bash" to view the bash manual page. The sections "Parameter Expansion" and "Pattern Matching" explain them.

I'll give some examples that will make it more clear.

```

x='123.abc.def';

# Prints string x with '.def' removed from the end of the string x
# (x is unchanged)
echo "${x%%.def}" # Prints '123.abc'

# Prints string x with all characters up to the . removed from the end of the string
# (x is unchanged)
echo "${x%%.*}" # Prints '123'

shopt extglob # Enables extended pattern matching

x='abc.123.def          #'

# Prints string x with a trailing number sign preceeded by one or more blank characters
# removed from the end of the string
echo "${x%%+([[:blank:]])#}"

```

For '${fn%%.${ext}}', the variable ext is being substituted into the expression. For example, if ext is 'tar.gz' then '${fn%%.${ext}}' is the same as '${fn%%.tar.gz}', which is equivalent to the string fn with '.tar.gz' removed from the end.

---

### Post by mobilediesel on 2009-05-12
> **bigboy_pdb said:**
> It's not a regular expression. It's bash parameter expansion being used in conjunction with bash pattern matching.

The only reason why I'm mentioning it is so that it will save you some trouble when you search for information in the future.

You can use "man bash" to view the bash manual page. The sections "Parameter Expansion" and "Pattern Matching" explain them.

I'll give some examples that will make it more clear.

```

x='123.abc.def';

# Prints string x with '.def' removed from the end of the string x
# (x is unchanged)
echo "${x%%.def}" # Prints '123.abc'

# Prints string x with all characters up to the . removed from the end of the string
# (x is unchanged)
echo "${x%%.*}" # Prints '123'

shopt extglob # Enables extended pattern matching

x='abc.123.def          #'

# Prints string x with a trailing number sign preceeded by one or more blank characters
# removed from the end of the string
echo "${x%%+([[:blank:]])#}"

```

For '${fn%%.${ext}}', the variable ext is being substituted into the expression. For example, if ext is 'tar.gz' then '${fn%%.${ext}}' is the same as '${fn%%.tar.gz}', which is equivalent to the string fn with '.tar.gz' removed from the end.

Ah, ok. You learn something new every day! I've actually looked at man bash a few times. Quite a bit of information there. I just did a ```
man bash > bash.txt
```so I can have that open without having more than one terminal open.

---

### Post by apmcd47 on 2009-05-13
> **mobilediesel said:**
> Ah, ok. You learn something new every day! I've actually looked at man bash a few times. Quite a bit of information there. I just did a ```
man bash > bash.txt
```so I can have that open without having more than one terminal open.

If you don't want to use a terminal but are happy keeping a web browser open, it's amazing how many web sites have the Unix/Linux manual pages in html format. Just type, eg ```
man bash
``` into your favourite search engine and take your pick.

Quite often I'm looking at this forum on a Windows laptop, and when I want to reference a man page to help someone I rely on these web sites.

Andrew

---

### Post by geirha on 2009-05-13
One-liner ... because we can.
```
for file in *; do [ -f "$file" ] || continue; [ -d "${file%.*}" ] || mkdir -v "${file%.*}"; mv -v "$file" "${file%.*}"; done
```

---

### Post by petrus4 on 2009-05-13
> **kobe81 said:**
> First off, thanks in advance for your help. I'm trying to find a shell script that copies all files in a given directory to folders of their same names. For example in "directory1" I have file1.txt, file2.txt, file3.txt... I'd like to move file1.txt to a directory named "file1", file2.txt to a directory named "file2" and so on. Do anyone have any ideas?

My apologies for the late reply; I hope I'm not too late.

I recently wrote a shell script which takes an MD5 file (say, from the directory of the KDE ftp site) and from that generates a flat text database, in the format:-

<MD5SUM>;<DOWNLOAD SITE ADDRESS>;<FULL FILE NAME>;<FILE EXTENSION>;<FILE VERSION>;<FILE NAME WITHOUT VERSION OR EXTENSION>.

So looking at that, once you've downloaded an MD5SUM list, (say from [ftp://ftp.lfs-matrix.net/pub/lfs/lfs-packages/6.4/MD5SUMS](ftp://ftp.lfs-matrix.net/pub/lfs/lfs-packages/6.4/MD5SUMS), which is what I wrote this for initially) once you've run the script, if hypothetically you wanted to create directories from the names of those packages, all you'd then need to write is:-

```
filelist=`cat MD5SUMS`

for i in $filelist
do
dirname=`echo $i | cut -d';' -f6`
mkdir -p $dirname
unset $dirname
done
```

If you are downloading a group of files for which no such remote MD5SUMS file exists, once you have downloaded all of the files, put the downloaded files in their own directory, and you can create one like so:-

```
filelist=`ls *`
for i in $filelist
do md5sum $i >> MD5SUMS
done

sed s'@  @;@'g MD5SUMS > MD5SUMS.bak
mv MD5SUMS.bak MD5SUMS
```

I've uploaded the script as a file attachment.  I apologise for uploading a tarball as I realise that may cause security concerns, but the script is six files long, (although only short files) and I am only allowed to attach five.

In what may be a futile gesture of good faith to demonstrate the absence of malware in the tarball, however, I am including the md5sum of the tarball itself, which you will be able to verify from your end.

90add2c48ed2cb9e055c99bc1ab46cfc mkpkgdata.tar.bz2

I hope this is of some use.  My file naming convention may appear rather cryptic, however if you edit the end of the spine file, you will notice that it calls the other files, with arguments for the input file, which you can change from MD5SUMS to whatever you need.  The spine file should then be executed in order to run the script, and it will call the other files.

I also recommend using the command:-

```
./mkpkgdata+0-of-5+spine.sh 2>&1 | tee mkpkgdata+0-of-5+spine.log
```

This will create a log file of the spine script's activities, and the called scripts.  It is possible to see where the log of each called script begins when viewing the main log, by doing a keyword search for addurl, addversion, and so on; the keywords of each script's name.  This will allow for extremely precise debugging of the script if you run into problems.

I also of course offer this to anyone else who may be able to use it.  It uses the BSD license.

---

