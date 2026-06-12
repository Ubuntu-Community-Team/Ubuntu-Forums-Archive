---
title: "Organizing fonts"
date: 2009-04-04
forum: General Help
---

### Post by jonathonblake on 2009-04-04
All:

I've decided to organize my fonts into several directories.

My current thinking is to create one directory for each font extension, and then 37 subdirectories within them.   Each subdirectory is a different letter of the alphabet or number. (The 37 is for font file names that don't begin with a..z or 0..9. )
Before moving the fonts, I run a script that deletes white space, and a second script that converts file names to lower case. 

Questions:

Are there are any font extensions that need to be in the same directory?

Are there any reasons to not create these directories and subdirectories within /usr/share/fonts/  ?

jonathon

---

### Post by jonathonblake on 2009-04-25
Here are the scripts I used

To remove white space: 
This is the "remove_white_spaces.sh" script called by one of the scripts below:
```

for f in *; do mv "$f" `echo $f | tr ' ' '_'`; done

```

To convert to minuscles:
This is the "convert_to_lower_case.sh" script called by one of the scripts below:
```

#!/bin/sh
#
# To make this Bourne shell script operative apply once:
#  chmod 700 namedown
#  rehash

# Alter the general path for BSD vs. Sys V compatibility
#
if [ -d /usr/ucb ] ; then
  PATH=/usr/ucb:$PATH ; export PATH
fi

case $# in

  0)
    echo
    echo "====================================================="
    echo "namedown, Convert file names to lower case and ; to ."
    echo "By Hannu Hirvonen and Timo Salmi Sun 18-Mar-2001"
    echo "http://www.uwasa.fi/~ts/ and http://www.uwasa.fi/~hh/"
    echo "====================================================="
    echo
    echo "Usage: namedown [FILENAME(S)]"
    echo
    echo "Converts file names only.  Directory names are not affected"
    echo
    ;;

  *)
    for oldname in $*
    do
      newfile=`basename ${oldname} | tr '[A-Z;]' '[a-z.]'`
      dirname=`dirname ${oldname}`
      newname="${dirname}/${newfile}"
      oldname="${dirname}/`basename ${oldname}`"
#Don't convert a file into itself
      if [ "${newname}" = "${oldname}" ]; then
        echo > /dev/null
#Don't convert directory names
      elif [ -d "${oldname}" ]; then
        echo > /dev/null
#Don't convert if the file does not exist
      elif [ ! -f "${oldname}" ]; then
        echo > /dev/null
#Don't overwrite existing files
      elif [ -f "${newname}" ]; then
        echo "${oldname} not converted, file ${newname} already exists" 2>&1
#Don't move to subdirectories if they happen to exist
      elif [ -d "${newname}" ]; then
        echo "${oldname} not converted, directory ${newname} already exists" 2>&1
#Do it
      else
        mv "${oldname}" "${newname:-${oldname}}"
        echo "File ${oldname} converted to file ${newname:-${oldname}}"
      fi
   done
    ;;
esac

```

To create the extension named directories:
```


# Make the directory for the file name extensions.
# Then make the alphabetical directories within those directories

sudo mkdir asf
sudo mkdir auf
sudo mkdir atm
sudo mkdir bdf
sudo mkdir bez
sudo mkdir bfn
sudo mkdir bmf
sudo mkdir chd
sudo mkdir chm
sudo mkdir dfont
sudo mkdir drs
sudo mkdir fdb
sudo mkdir ff
sudo mkdir ffil
sudo mkdir fi
sudo mkdir fif
sudo mkdir fli
sudo mkdir fnt
sudo mkdir fon
sudo mkdir frs 
sudo mkdir glf 
sudo mkdir glf 
sudo mkdir hpc 
sudo mkdir hpi 
sudo mkdir lxo 
sudo mkdir mmm 
sudo mkdir mrf 
sudo mkdir mtf 
sudo mkdir mxf 
sudo mkdir ofm 
sudo mkdir otf 
sudo mkdir pcf 
sudo mkdir pfb 
sudo mkdir pfm 
sudo mkdir pft 
sudo mkdir psf 
sudo mkdir scr 
sudo mkdir scr 
sudo mkdir sfd 
sudo mkdir sfi 
sudo mkdir sfl 
sudo mkdir snf 
sudo mkdir snf 
sudo mkdir spd 
sudo mkdir spd 
sudo mkdir t2 
sudo mkdir ttc
sudo mkdir xft 
sudo mkdir all
sudo mkdir asf
sudo mkdir auf
sudo mkdir atm
sudo mkdir bdf
sudo mkdir bez
sudo mkdir bfn
sudo mkdir bmf
sudo mkdir chd
sudo mkdir chm
sudo mkdir dfont
sudo mkdir drs
sudo mkdir fdb
sudo mkdir ff
sudo mkdir ffil
sudo mkdir fi
sudo mkdir fif
sudo mkdir fli
sudo mkdir fnt
sudo mkdir fon
sudo mkdir frs 
sudo mkdir glf 
sudo mkdir glf 
sudo mkdir hpc 
sudo mkdir hpi 
sudo mkdir lxo 
sudo mkdir mmm 
sudo mkdir mrf 
sudo mkdir mtf 
sudo mkdir mxf 
sudo mkdir ofm 
sudo mkdir otf 
sudo mkdir pcf 
sudo mkdir pfb 
sudo mkdir pfm 
sudo mkdir pft 
sudo mkdir psf 
sudo mkdir scr 
sudo mkdir scr 
sudo mkdir sfd 
sudo mkdir sfi 
sudo mkdir sfl 
sudo mkdir snf 
sudo mkdir snf 
sudo mkdir spd 
sudo mkdir spd 
sudo mkdir t2 
sudo mkdir ttc
sudo mkdir xft 


cd  all
sudo sh make_directory.sh
cd ..

cd  asf
sudo sh make_directory.sh
cd ..

cd  auf
sudo sh make_directory.sh
cd ..

cd  atm
sudo sh make_directory.sh
cd ..

cd  bdf
sudo sh make_directory.sh
cd ..

cd  bez
sudo sh make_directory.sh
cd ..

cd  bfn
sudo sh make_directory.sh
cd ..

cd  bmf
sudo sh make_directory.sh
cd ..

cd  chd
sudo sh make_directory.sh
cd ..

cd  chm
sudo sh make_directory.sh
cd ..

cd  dfont
sudo sh make_directory.sh
cd ..

cd  drs
sudo sh make_directory.sh
cd ..

cd  fdb
sudo sh make_directory.sh
cd ..

cd  ff
sudo sh make_directory.sh
cd ..

cd  ffil
sudo sh make_directory.sh
cd ..

cd  fi
sudo sh make_directory.sh
cd ..

cd  fif
sudo sh make_directory.sh
cd ..

cd  fli
sudo sh make_directory.sh
cd ..

cd  fnt
sudo sh make_directory.sh
cd ..

cd  fon
sudo sh make_directory.sh
cd ..

cd  frs 
sudo sh make_directory.sh
cd ..

cd  glf 
sudo sh make_directory.sh
cd ..

cd  glf 
sudo sh make_directory.sh
cd ..

cd  hpc 
sudo sh make_directory.sh
cd ..

cd  hpi 
sudo sh make_directory.sh
cd ..

cd  lxo 
sudo sh make_directory.sh
cd ..

cd  mmm 
sudo sh make_directory.sh
cd ..

cd  mrf 
sudo sh make_directory.sh
cd ..

cd  mtf 
sudo sh make_directory.sh
cd ..

cd  mxf 
sudo sh make_directory.sh
cd ..

cd  ofm 
sudo sh make_directory.sh
cd ..

cd  otf 
sudo sh make_directory.sh
cd ..

cd  pcf 
sudo sh make_directory.sh
cd ..

cd  pfb 
sudo sh make_directory.sh
cd ..

cd  pfm 
sudo sh make_directory.sh
cd ..

cd  pft 
sudo sh make_directory.sh
cd ..

cd  psf 
sudo sh make_directory.sh
cd ..

cd  scr 
sudo sh make_directory.sh
cd ..

cd  scr 
sudo sh make_directory.sh
cd ..

cd  sfd 
sudo sh make_directory.sh
cd ..

cd  sfi 
sudo sh make_directory.sh
cd ..

cd  sfl 
sudo sh make_directory.sh
cd ..

cd  snf 
sudo sh make_directory.sh
cd ..

cd  snf 
sudo sh make_directory.sh
cd ..

cd  spd 
sudo sh make_directory.sh
cd ..

cd  spd 
sudo sh make_directory.sh
cd ..

cd  t2 
sudo sh make_directory.sh
cd ..

cd  ttc
sudo sh make_directory.sh
cd ..

cd  xft 
sudo sh make_directory.sh
cd ..

```

The "make_directory.sh" script used above is:
```


sudo mkdir  a/
sudo mkdir  b/
sudo mkdir  c/
sudo mkdir  d/
sudo mkdir  e/
sudo mkdir  f/
sudo mkdir  g/
sudo mkdir  h/
sudo mkdir  i/
sudo mkdir  j/
sudo mkdir  k/
sudo mkdir  l/
sudo mkdir  m/
sudo mkdir  n/
sudo mkdir  o/
sudo mkdir  p/
sudo mkdir  q/
sudo mkdir  r/
sudo mkdir  s/
sudo mkdir  t/
sudo mkdir  u/
sudo mkdir  v/
sudo mkdir  w/
sudo mkdir  x/
sudo mkdir  y/
sudo mkdir  z/
sudo mkdir  0/
sudo mkdir  1/
sudo mkdir  2/
sudo mkdir  3/
sudo mkdir  4/
sudo mkdir  5/
sudo mkdir  6/
sudo mkdir  7/
sudo mkdir  8/
sudo mkdir  9/
sudo mkdir other/

```

To move the fonts:
```

# this script copies fonts from one location into /usr/share/fonts.

# A message of 
# cannot stat <file_name> :No such file or directory
# simply means that there are no files with the specified criteria to be copied.
# Some font types are extremely rare.
# Filenames beginning with glyphs other than letters and numbers are unusual;

cd /usr/share/fonts/temp
sh remove_white_spaces.sh
sh convert_to_lower_case.sh

echo ABF
cp   /home/temp_user/Theme/fonts/_*.abf   /usr/share/fonts/abf/other/
cp   /home/temp_user/Theme/fonts/a*.abf   /usr/share/fonts/abf/a/
cp   /home/temp_user/Theme/fonts/b*.abf   /usr/share/fonts/abf/b/
cp   /home/temp_user/Theme/fonts/c*.abf   /usr/share/fonts/abf/c/
cp   /home/temp_user/Theme/fonts/d*.abf   /usr/share/fonts/abf/d/
cp   /home/temp_user/Theme/fonts/e*.abf   /usr/share/fonts/abf/e/
cp   /home/temp_user/Theme/fonts/f*.abf   /usr/share/fonts/abf/f/
cp   /home/temp_user/Theme/fonts/g*.abf   /usr/share/fonts/abf/g/
cp   /home/temp_user/Theme/fonts/h*.abf   /usr/share/fonts/abf/h/
cp   /home/temp_user/Theme/fonts/i*.abf   /usr/share/fonts/abf/i/
cp   /home/temp_user/Theme/fonts/j*.abf   /usr/share/fonts/abf/j/
cp   /home/temp_user/Theme/fonts/k*.abf   /usr/share/fonts/abf/k/
cp   /home/temp_user/Theme/fonts/l*.abf   /usr/share/fonts/abf/l/
cp   /home/temp_user/Theme/fonts/m*.abf   /usr/share/fonts/abf/m/
cp   /home/temp_user/Theme/fonts/n*.abf   /usr/share/fonts/abf/n/
cp   /home/temp_user/Theme/fonts/o*.abf   /usr/share/fonts/abf/o/
cp   /home/temp_user/Theme/fonts/p*.abf   /usr/share/fonts/abf/p/
cp   /home/temp_user/Theme/fonts/q*.abf   /usr/share/fonts/abf/q/
cp   /home/temp_user/Theme/fonts/r*.abf   /usr/share/fonts/abf/r/
cp   /home/temp_user/Theme/fonts/s*.abf   /usr/share/fonts/abf/s/
cp   /home/temp_user/Theme/fonts/t*.abf   /usr/share/fonts/abf/t/
cp   /home/temp_user/Theme/fonts/u*.abf   /usr/share/fonts/abf/u/
cp   /home/temp_user/Theme/fonts/v*.abf   /usr/share/fonts/abf/v/
cp   /home/temp_user/Theme/fonts/w*.abf   /usr/share/fonts/abf/w/
cp   /home/temp_user/Theme/fonts/x*.abf   /usr/share/fonts/abf/x/
cp   /home/temp_user/Theme/fonts/y*.abf   /usr/share/fonts/abf/y/
cp   /home/temp_user/Theme/fonts/z*.abf   /usr/share/fonts/abf/z/
cp   /home/temp_user/Theme/fonts/0*.abf   /usr/share/fonts/abf/0/
cp   /home/temp_user/Theme/fonts/1*.abf   /usr/share/fonts/abf/1/
cp   /home/temp_user/Theme/fonts/2*.abf   /usr/share/fonts/abf/2/
cp   /home/temp_user/Theme/fonts/3*.abf   /usr/share/fonts/abf/3/
cp   /home/temp_user/Theme/fonts/4*.abf   /usr/share/fonts/abf/4/
cp   /home/temp_user/Theme/fonts/5*.abf   /usr/share/fonts/abf/5/
cp   /home/temp_user/Theme/fonts/6*.abf   /usr/share/fonts/abf/6/
cp   /home/temp_user/Theme/fonts/7*.abf   /usr/share/fonts/abf/7/
cp   /home/temp_user/Theme/fonts/8*.abf   /usr/share/fonts/abf/8/
cp   /home/temp_user/Theme/fonts/9*.abf   /usr/share/fonts/abf/9/
cp   /home/temp_user/Theme/fonts/[*.abf   /usr/share/fonts/abf/other/

echo ALL
cp   /home/temp_user/Theme/fonts/_*.all   /usr/share/fonts/all/other/
cp   /home/temp_user/Theme/fonts/a*.all   /usr/share/fonts/all/a/
cp   /home/temp_user/Theme/fonts/b*.all   /usr/share/fonts/all/b/
cp   /home/temp_user/Theme/fonts/c*.all   /usr/share/fonts/all/c/
cp   /home/temp_user/Theme/fonts/d*.all   /usr/share/fonts/all/d/
cp   /home/temp_user/Theme/fonts/e*.all   /usr/share/fonts/all/e/
cp   /home/temp_user/Theme/fonts/f*.all   /usr/share/fonts/all/f/
cp   /home/temp_user/Theme/fonts/g*.all   /usr/share/fonts/all/g/
cp   /home/temp_user/Theme/fonts/h*.all   /usr/share/fonts/all/h/
cp   /home/temp_user/Theme/fonts/i*.all   /usr/share/fonts/all/i/
cp   /home/temp_user/Theme/fonts/j*.all   /usr/share/fonts/all/j/
cp   /home/temp_user/Theme/fonts/k*.all   /usr/share/fonts/all/k/
cp   /home/temp_user/Theme/fonts/l*.all   /usr/share/fonts/all/l/
cp   /home/temp_user/Theme/fonts/m*.all   /usr/share/fonts/all/m/
cp   /home/temp_user/Theme/fonts/n*.all   /usr/share/fonts/all/n/
cp   /home/temp_user/Theme/fonts/o*.all   /usr/share/fonts/all/o/
cp   /home/temp_user/Theme/fonts/p*.all   /usr/share/fonts/all/p/
cp   /home/temp_user/Theme/fonts/q*.all   /usr/share/fonts/all/q/
cp   /home/temp_user/Theme/fonts/r*.all   /usr/share/fonts/all/r/
cp   /home/temp_user/Theme/fonts/s*.all   /usr/share/fonts/all/s/
cp   /home/temp_user/Theme/fonts/t*.all   /usr/share/fonts/all/t/
cp   /home/temp_user/Theme/fonts/u*.all   /usr/share/fonts/all/u/
cp   /home/temp_user/Theme/fonts/v*.all   /usr/share/fonts/all/v/
cp   /home/temp_user/Theme/fonts/w*.all   /usr/share/fonts/all/w/
cp   /home/temp_user/Theme/fonts/x*.all   /usr/share/fonts/all/x/
cp   /home/temp_user/Theme/fonts/y*.all   /usr/share/fonts/all/y/
cp   /home/temp_user/Theme/fonts/z*.all   /usr/share/fonts/all/z/
cp   /home/temp_user/Theme/fonts/0*.all   /usr/share/fonts/all/0/
cp   /home/temp_user/Theme/fonts/1*.all   /usr/share/fonts/all/1/
cp   /home/temp_user/Theme/fonts/2*.all   /usr/share/fonts/all/2/
cp   /home/temp_user/Theme/fonts/3*.all   /usr/share/fonts/all/3/
cp   /home/temp_user/Theme/fonts/4*.all   /usr/share/fonts/all/4/
cp   /home/temp_user/Theme/fonts/5*.all   /usr/share/fonts/all/5/
cp   /home/temp_user/Theme/fonts/6*.all   /usr/share/fonts/all/6/
cp   /home/temp_user/Theme/fonts/7*.all   /usr/share/fonts/all/7/
cp   /home/temp_user/Theme/fonts/8*.all   /usr/share/fonts/all/8/
cp   /home/temp_user/Theme/fonts/9*.all   /usr/share/fonts/all/9/
cp   /home/temp_user/Theme/fonts/[*.all   /usr/share/fonts/all/other/

echo ASF
cp   /home/temp_user/Theme/fonts/_*.asf   /usr/share/fonts/asf/other/
cp   /home/temp_user/Theme/fonts/a*.asf   /usr/share/fonts/asf/a/
cp   /home/temp_user/Theme/fonts/b*.asf   /usr/share/fonts/asf/b/
cp   /home/temp_user/Theme/fonts/c*.asf   /usr/share/fonts/asf/c/
cp   /home/temp_user/Theme/fonts/d*.asf   /usr/share/fonts/asf/d/
cp   /home/temp_user/Theme/fonts/e*.asf   /usr/share/fonts/asf/e/
cp   /home/temp_user/Theme/fonts/f*.asf   /usr/share/fonts/asf/f/
cp   /home/temp_user/Theme/fonts/g*.asf   /usr/share/fonts/asf/g/
cp   /home/temp_user/Theme/fonts/h*.asf   /usr/share/fonts/asf/h/
cp   /home/temp_user/Theme/fonts/i*.asf   /usr/share/fonts/asf/i/
cp   /home/temp_user/Theme/fonts/j*.asf   /usr/share/fonts/asf/j/
cp   /home/temp_user/Theme/fonts/k*.asf   /usr/share/fonts/asf/k/
cp   /home/temp_user/Theme/fonts/l*.asf   /usr/share/fonts/asf/l/
cp   /home/temp_user/Theme/fonts/m*.asf   /usr/share/fonts/asf/m/
cp   /home/temp_user/Theme/fonts/n*.asf   /usr/share/fonts/asf/n/
cp   /home/temp_user/Theme/fonts/o*.asf   /usr/share/fonts/asf/o/
cp   /home/temp_user/Theme/fonts/p*.asf   /usr/share/fonts/asf/p/
cp   /home/temp_user/Theme/fonts/q*.asf   /usr/share/fonts/asf/q/
cp   /home/temp_user/Theme/fonts/r*.asf   /usr/share/fonts/asf/r/
cp   /home/temp_user/Theme/fonts/s*.asf   /usr/share/fonts/asf/s/
cp   /home/temp_user/Theme/fonts/t*.asf   /usr/share/fonts/asf/t/
cp   /home/temp_user/Theme/fonts/u*.asf   /usr/share/fonts/asf/u/
cp   /home/temp_user/Theme/fonts/v*.asf   /usr/share/fonts/asf/v/
cp   /home/temp_user/Theme/fonts/w*.asf   /usr/share/fonts/asf/w/
cp   /home/temp_user/Theme/fonts/x*.asf   /usr/share/fonts/asf/x/
cp   /home/temp_user/Theme/fonts/y*.asf   /usr/share/fonts/asf/y/
cp   /home/temp_user/Theme/fonts/z*.asf   /usr/share/fonts/asf/z/
cp   /home/temp_user/Theme/fonts/0*.asf   /usr/share/fonts/asf/0/
cp   /home/temp_user/Theme/fonts/1*.asf   /usr/share/fonts/asf/1/
cp   /home/temp_user/Theme/fonts/2*.asf   /usr/share/fonts/asf/2/
cp   /home/temp_user/Theme/fonts/3*.asf   /usr/share/fonts/asf/3/
cp   /home/temp_user/Theme/fonts/4*.asf   /usr/share/fonts/asf/4/
cp   /home/temp_user/Theme/fonts/5*.asf   /usr/share/fonts/asf/5/
cp   /home/temp_user/Theme/fonts/6*.asf   /usr/share/fonts/asf/6/
cp   /home/temp_user/Theme/fonts/7*.asf   /usr/share/fonts/asf/7/
cp   /home/temp_user/Theme/fonts/8*.asf   /usr/share/fonts/asf/8/
cp   /home/temp_user/Theme/fonts/9*.asf   /usr/share/fonts/asf/9/
cp   /home/temp_user/Theme/fonts/[*.asf   /usr/share/fonts/asf/other/

echo ATM
cp   /home/temp_user/Theme/fonts/_*.atm   /usr/share/fonts/atm/other/
cp   /home/temp_user/Theme/fonts/a*.atm   /usr/share/fonts/atm/a/
cp   /home/temp_user/Theme/fonts/b*.atm   /usr/share/fonts/atm/b/
cp   /home/temp_user/Theme/fonts/c*.atm   /usr/share/fonts/atm/c/
cp   /home/temp_user/Theme/fonts/d*.atm   /usr/share/fonts/atm/d/
cp   /home/temp_user/Theme/fonts/e*.atm   /usr/share/fonts/atm/e/
cp   /home/temp_user/Theme/fonts/f*.atm   /usr/share/fonts/atm/f/
cp   /home/temp_user/Theme/fonts/g*.atm   /usr/share/fonts/atm/g/
cp   /home/temp_user/Theme/fonts/h*.atm   /usr/share/fonts/atm/h/
cp   /home/temp_user/Theme/fonts/i*.atm   /usr/share/fonts/atm/i/
cp   /home/temp_user/Theme/fonts/j*.atm   /usr/share/fonts/atm/j/
cp   /home/temp_user/Theme/fonts/k*.atm   /usr/share/fonts/atm/k/
cp   /home/temp_user/Theme/fonts/l*.atm   /usr/share/fonts/atm/l/
cp   /home/temp_user/Theme/fonts/m*.atm   /usr/share/fonts/atm/m/
cp   /home/temp_user/Theme/fonts/n*.atm   /usr/share/fonts/atm/n/
cp   /home/temp_user/Theme/fonts/o*.atm   /usr/share/fonts/atm/o/
cp   /home/temp_user/Theme/fonts/p*.atm   /usr/share/fonts/atm/p/
cp   /home/temp_user/Theme/fonts/q*.atm   /usr/share/fonts/atm/q/
cp   /home/temp_user/Theme/fonts/r*.atm   /usr/share/fonts/atm/r/
cp   /home/temp_user/Theme/fonts/s*.atm   /usr/share/fonts/atm/s/
cp   /home/temp_user/Theme/fonts/t*.atm   /usr/share/fonts/atm/t/
cp   /home/temp_user/Theme/fonts/u*.atm   /usr/share/fonts/atm/u/
cp   /home/temp_user/Theme/fonts/v*.atm   /usr/share/fonts/atm/v/
cp   /home/temp_user/Theme/fonts/w*.atm   /usr/share/fonts/atm/w/
cp   /home/temp_user/Theme/fonts/x*.atm   /usr/share/fonts/atm/x/
cp   /home/temp_user/Theme/fonts/y*.atm   /usr/share/fonts/atm/y/
cp   /home/temp_user/Theme/fonts/z*.atm   /usr/share/fonts/atm/z/
cp   /home/temp_user/Theme/fonts/0*.atm   /usr/share/fonts/atm/0/
cp   /home/temp_user/Theme/fonts/1*.atm   /usr/share/fonts/atm/1/
cp   /home/temp_user/Theme/fonts/2*.atm   /usr/share/fonts/atm/2/
cp   /home/temp_user/Theme/fonts/3*.atm   /usr/share/fonts/atm/3/
cp   /home/temp_user/Theme/fonts/4*.atm   /usr/share/fonts/atm/4/
cp   /home/temp_user/Theme/fonts/5*.atm   /usr/share/fonts/atm/5/
cp   /home/temp_user/Theme/fonts/6*.atm   /usr/share/fonts/atm/6/
cp   /home/temp_user/Theme/fonts/7*.atm   /usr/share/fonts/atm/7/
cp   /home/temp_user/Theme/fonts/8*.atm   /usr/share/fonts/atm/8/
cp   /home/temp_user/Theme/fonts/9*.atm   /usr/share/fonts/atm/9/
cp   /home/temp_user/Theme/fonts/[*.atm   /usr/share/fonts/atm/other/

echo AUF
cp   /home/temp_user/Theme/fonts/_*.auf   /usr/share/fonts/auf/other/
cp   /home/temp_user/Theme/fonts/a*.auf   /usr/share/fonts/auf/a/
cp   /home/temp_user/Theme/fonts/b*.auf   /usr/share/fonts/auf/b/
cp   /home/temp_user/Theme/fonts/c*.auf   /usr/share/fonts/auf/c/
cp   /home/temp_user/Theme/fonts/d*.auf   /usr/share/fonts/auf/d/
cp   /home/temp_user/Theme/fonts/e*.auf   /usr/share/fonts/auf/e/
cp   /home/temp_user/Theme/fonts/f*.auf   /usr/share/fonts/auf/f/
cp   /home/temp_user/Theme/fonts/g*.auf   /usr/share/fonts/auf/g/
cp   /home/temp_user/Theme/fonts/h*.auf   /usr/share/fonts/auf/h/
cp   /home/temp_user/Theme/fonts/i*.auf   /usr/share/fonts/auf/i/
cp   /home/temp_user/Theme/fonts/j*.auf   /usr/share/fonts/auf/j/
cp   /home/temp_user/Theme/fonts/k*.auf   /usr/share/fonts/auf/k/
cp   /home/temp_user/Theme/fonts/l*.auf   /usr/share/fonts/auf/l/
cp   /home/temp_user/Theme/fonts/m*.auf   /usr/share/fonts/auf/m/
cp   /home/temp_user/Theme/fonts/n*.auf   /usr/share/fonts/auf/n/
cp   /home/temp_user/Theme/fonts/o*.auf   /usr/share/fonts/auf/o/
cp   /home/temp_user/Theme/fonts/p*.auf   /usr/share/fonts/auf/p/
cp   /home/temp_user/Theme/fonts/q*.auf   /usr/share/fonts/auf/q/
cp   /home/temp_user/Theme/fonts/r*.auf   /usr/share/fonts/auf/r/
cp   /home/temp_user/Theme/fonts/s*.auf   /usr/share/fonts/auf/s/
cp   /home/temp_user/Theme/fonts/t*.auf   /usr/share/fonts/auf/t/
cp   /home/temp_user/Theme/fonts/u*.auf   /usr/share/fonts/auf/u/
cp   /home/temp_user/Theme/fonts/v*.auf   /usr/share/fonts/auf/v/
cp   /home/temp_user/Theme/fonts/w*.auf   /usr/share/fonts/auf/w/
cp   /home/temp_user/Theme/fonts/x*.auf   /usr/share/fonts/auf/x/
cp   /home/temp_user/Theme/fonts/y*.auf   /usr/share/fonts/auf/y/
cp   /home/temp_user/Theme/fonts/z*.auf   /usr/share/fonts/auf/z/
cp   /home/temp_user/Theme/fonts/0*.auf   /usr/share/fonts/auf/0/
cp   /home/temp_user/Theme/fonts/1*.auf   /usr/share/fonts/auf/1/
cp   /home/temp_user/Theme/fonts/2*.auf   /usr/share/fonts/auf/2/
cp   /home/temp_user/Theme/fonts/3*.auf   /usr/share/fonts/auf/3/
cp   /home/temp_user/Theme/fonts/4*.auf   /usr/share/fonts/auf/4/
cp   /home/temp_user/Theme/fonts/5*.auf   /usr/share/fonts/auf/5/
cp   /home/temp_user/Theme/fonts/6*.auf   /usr/share/fonts/auf/6/
cp   /home/temp_user/Theme/fonts/7*.auf   /usr/share/fonts/auf/7/
cp   /home/temp_user/Theme/fonts/8*.auf   /usr/share/fonts/auf/8/
cp   /home/temp_user/Theme/fonts/9*.auf   /usr/share/fonts/auf/9/
cp   /home/temp_user/Theme/fonts/[*.auf   /usr/share/fonts/auf/other/

echo BDF
cp   /home/temp_user/Theme/fonts/_*.bdf   /usr/share/fonts/bdf/other/
cp   /home/temp_user/Theme/fonts/a*.bdf   /usr/share/fonts/bdf/a/
cp   /home/temp_user/Theme/fonts/b*.bdf   /usr/share/fonts/bdf/b/
cp   /home/temp_user/Theme/fonts/c*.bdf   /usr/share/fonts/bdf/c/
cp   /home/temp_user/Theme/fonts/d*.bdf   /usr/share/fonts/bdf/d/
cp   /home/temp_user/Theme/fonts/e*.bdf   /usr/share/fonts/bdf/e/
cp   /home/temp_user/Theme/fonts/f*.bdf   /usr/share/fonts/bdf/f/
cp   /home/temp_user/Theme/fonts/g*.bdf   /usr/share/fonts/bdf/g/
cp   /home/temp_user/Theme/fonts/h*.bdf   /usr/share/fonts/bdf/h/
cp   /home/temp_user/Theme/fonts/i*.bdf   /usr/share/fonts/bdf/i/
cp   /home/temp_user/Theme/fonts/j*.bdf   /usr/share/fonts/bdf/j/
cp   /home/temp_user/Theme/fonts/k*.bdf   /usr/share/fonts/bdf/k/
cp   /home/temp_user/Theme/fonts/l*.bdf   /usr/share/fonts/bdf/l/
cp   /home/temp_user/Theme/fonts/m*.bdf   /usr/share/fonts/bdf/m/
cp   /home/temp_user/Theme/fonts/n*.bdf   /usr/share/fonts/bdf/n/
cp   /home/temp_user/Theme/fonts/o*.bdf   /usr/share/fonts/bdf/o/
cp   /home/temp_user/Theme/fonts/p*.bdf   /usr/share/fonts/bdf/p/
cp   /home/temp_user/Theme/fonts/q*.bdf   /usr/share/fonts/bdf/q/
cp   /home/temp_user/Theme/fonts/r*.bdf   /usr/share/fonts/bdf/r/
cp   /home/temp_user/Theme/fonts/s*.bdf   /usr/share/fonts/bdf/s/
cp   /home/temp_user/Theme/fonts/t*.bdf   /usr/share/fonts/bdf/t/
cp   /home/temp_user/Theme/fonts/u*.bdf   /usr/share/fonts/bdf/u/
cp   /home/temp_user/Theme/fonts/v*.bdf   /usr/share/fonts/bdf/v/
cp   /home/temp_user/Theme/fonts/w*.bdf   /usr/share/fonts/bdf/w/
cp   /home/temp_user/Theme/fonts/x*.bdf   /usr/share/fonts/bdf/x/
cp   /home/temp_user/Theme/fonts/y*.bdf   /usr/share/fonts/bdf/y/
cp   /home/temp_user/Theme/fonts/z*.bdf   /usr/share/fonts/bdf/z/
cp   /home/temp_user/Theme/fonts/0*.bdf   /usr/share/fonts/bdf/0/
cp   /home/temp_user/Theme/fonts/1*.bdf   /usr/share/fonts/bdf/1/
cp   /home/temp_user/Theme/fonts/2*.bdf   /usr/share/fonts/bdf/2/
cp   /home/temp_user/Theme/fonts/3*.bdf   /usr/share/fonts/bdf/3/
cp   /home/temp_user/Theme/fonts/4*.bdf   /usr/share/fonts/bdf/4/
cp   /home/temp_user/Theme/fonts/5*.bdf   /usr/share/fonts/bdf/5/
cp   /home/temp_user/Theme/fonts/6*.bdf   /usr/share/fonts/bdf/6/
cp   /home/temp_user/Theme/fonts/7*.bdf   /usr/share/fonts/bdf/7/
cp   /home/temp_user/Theme/fonts/8*.bdf   /usr/share/fonts/bdf/8/
cp   /home/temp_user/Theme/fonts/9*.bdf   /usr/share/fonts/bdf/9/
cp   /home/temp_user/Theme/fonts/[*.bdf   /usr/share/fonts/bdf/other/

echo BEZ
cp   /home/temp_user/Theme/fonts/_*.bez   /usr/share/fonts/bez/other/
cp   /home/temp_user/Theme/fonts/a*.bez   /usr/share/fonts/bez/a/
cp   /home/temp_user/Theme/fonts/b*.bez   /usr/share/fonts/bez/b/
cp   /home/temp_user/Theme/fonts/c*.bez   /usr/share/fonts/bez/c/
cp   /home/temp_user/Theme/fonts/d*.bez   /usr/share/fonts/bez/d/
cp   /home/temp_user/Theme/fonts/e*.bez   /usr/share/fonts/bez/e/
cp   /home/temp_user/Theme/fonts/f*.bez   /usr/share/fonts/bez/f/
cp   /home/temp_user/Theme/fonts/g*.bez   /usr/share/fonts/bez/g/
cp   /home/temp_user/Theme/fonts/h*.bez   /usr/share/fonts/bez/h/
cp   /home/temp_user/Theme/fonts/i*.bez   /usr/share/fonts/bez/i/
cp   /home/temp_user/Theme/fonts/j*.bez   /usr/share/fonts/bez/j/
cp   /home/temp_user/Theme/fonts/k*.bez   /usr/share/fonts/bez/k/
cp   /home/temp_user/Theme/fonts/l*.bez   /usr/share/fonts/bez/l/
cp   /home/temp_user/Theme/fonts/m*.bez   /usr/share/fonts/bez/m/
cp   /home/temp_user/Theme/fonts/n*.bez   /usr/share/fonts/bez/n/
cp   /home/temp_user/Theme/fonts/o*.bez   /usr/share/fonts/bez/o/
cp   /home/temp_user/Theme/fonts/p*.bez   /usr/share/fonts/bez/p/
cp   /home/temp_user/Theme/fonts/q*.bez   /usr/share/fonts/bez/q/
cp   /home/temp_user/Theme/fonts/r*.bez   /usr/share/fonts/bez/r/
cp   /home/temp_user/Theme/fonts/s*.bez   /usr/share/fonts/bez/s/
cp   /home/temp_user/Theme/fonts/t*.bez   /usr/share/fonts/bez/t/
cp   /home/temp_user/Theme/fonts/u*.bez   /usr/share/fonts/bez/u/
cp   /home/temp_user/Theme/fonts/v*.bez   /usr/share/fonts/bez/v/
cp   /home/temp_user/Theme/fonts/w*.bez   /usr/share/fonts/bez/w/
cp   /home/temp_user/Theme/fonts/x*.bez   /usr/share/fonts/bez/x/
cp   /home/temp_user/Theme/fonts/y*.bez   /usr/share/fonts/bez/y/
cp   /home/temp_user/Theme/fonts/z*.bez   /usr/share/fonts/bez/z/
cp   /home/temp_user/Theme/fonts/0*.bez   /usr/share/fonts/bez/0/
cp   /home/temp_user/Theme/fonts/1*.bez   /usr/share/fonts/bez/1/
cp   /home/temp_user/Theme/fonts/2*.bez   /usr/share/fonts/bez/2/
cp   /home/temp_user/Theme/fonts/3*.bez   /usr/share/fonts/bez/3/
cp   /home/temp_user/Theme/fonts/4*.bez   /usr/share/fonts/bez/4/
cp   /home/temp_user/Theme/fonts/5*.bez   /usr/share/fonts/bez/5/
cp   /home/temp_user/Theme/fonts/6*.bez   /usr/share/fonts/bez/6/
cp   /home/temp_user/Theme/fonts/7*.bez   /usr/share/fonts/bez/7/
cp   /home/temp_user/Theme/fonts/8*.bez   /usr/share/fonts/bez/8/
cp   /home/temp_user/Theme/fonts/9*.bez   /usr/share/fonts/bez/9/
cp   /home/temp_user/Theme/fonts/[*.bez   /usr/share/fonts/bez/other/

echo BMF
cp   /home/temp_user/Theme/fonts/_*.bmf   /usr/share/fonts/bmf/other/
cp   /home/temp_user/Theme/fonts/a*.bmf   /usr/share/fonts/bmf/a/
cp   /home/temp_user/Theme/fonts/b*.bmf   /usr/share/fonts/bmf/b/
cp   /home/temp_user/Theme/fonts/c*.bmf   /usr/share/fonts/bmf/c/
cp   /home/temp_user/Theme/fonts/d*.bmf   /usr/share/fonts/bmf/d/
cp   /home/temp_user/Theme/fonts/e*.bmf   /usr/share/fonts/bmf/e/
cp   /home/temp_user/Theme/fonts/f*.bmf   /usr/share/fonts/bmf/f/
cp   /home/temp_user/Theme/fonts/g*.bmf   /usr/share/fonts/bmf/g/
cp   /home/temp_user/Theme/fonts/h*.bmf   /usr/share/fonts/bmf/h/
cp   /home/temp_user/Theme/fonts/i*.bmf   /usr/share/fonts/bmf/i/
cp   /home/temp_user/Theme/fonts/j*.bmf   /usr/share/fonts/bmf/j/
cp   /home/temp_user/Theme/fonts/k*.bmf   /usr/share/fonts/bmf/k/
cp   /home/temp_user/Theme/fonts/l*.bmf   /usr/share/fonts/bmf/l/
cp   /home/temp_user/Theme/fonts/m*.bmf   /usr/share/fonts/bmf/m/
cp   /home/temp_user/Theme/fonts/n*.bmf   /usr/share/fonts/bmf/n/
cp   /home/temp_user/Theme/fonts/o*.bmf   /usr/share/fonts/bmf/o/
cp   /home/temp_user/Theme/fonts/p*.bmf   /usr/share/fonts/bmf/p/
cp   /home/temp_user/Theme/fonts/q*.bmf   /usr/share/fonts/bmf/q/
cp   /home/temp_user/Theme/fonts/r*.bmf   /usr/share/fonts/bmf/r/
cp   /home/temp_user/Theme/fonts/s*.bmf   /usr/share/fonts/bmf/s/
cp   /home/temp_user/Theme/fonts/t*.bmf   /usr/share/fonts/bmf/t/
cp   /home/temp_user/Theme/fonts/u*.bmf   /usr/share/fonts/bmf/u/
cp   /home/temp_user/Theme/fonts/v*.bmf   /usr/share/fonts/bmf/v/
cp   /home/temp_user/Theme/fonts/w*.bmf   /usr/share/fonts/bmf/w/
cp   /home/temp_user/Theme/fonts/x*.bmf   /usr/share/fonts/bmf/x/
cp   /home/temp_user/Theme/fonts/y*.bmf   /usr/share/fonts/bmf/y/
cp   /home/temp_user/Theme/fonts/z*.bmf   /usr/share/fonts/bmf/z/
cp   /home/temp_user/Theme/fonts/0*.bmf   /usr/share/fonts/bmf/0/
cp   /home/temp_user/Theme/fonts/1*.bmf   /usr/share/fonts/bmf/1/
cp   /home/temp_user/Theme/fonts/2*.bmf   /usr/share/fonts/bmf/2/
cp   /home/temp_user/Theme/fonts/3*.bmf   /usr/share/fonts/bmf/3/
cp   /home/temp_user/Theme/fonts/4*.bmf   /usr/share/fonts/bmf/4/
cp   /home/temp_user/Theme/fonts/5*.bmf   /usr/share/fonts/bmf/5/
cp   /home/temp_user/Theme/fonts/6*.bmf   /usr/share/fonts/bmf/6/
cp   /home/temp_user/Theme/fonts/7*.bmf   /usr/share/fonts/bmf/7/
cp   /home/temp_user/Theme/fonts/8*.bmf   /usr/share/fonts/bmf/8/
cp   /home/temp_user/Theme/fonts/9*.bmf   /usr/share/fonts/bmf/9/
cp   /home/temp_user/Theme/fonts/[*.bmf   /usr/share/fonts/bmf/other/

echo CHD
cp   /home/temp_user/Theme/fonts/_*.chd   /usr/share/fonts/chd/other/
cp   /home/temp_user/Theme/fonts/a*.chd   /usr/share/fonts/chd/a/
cp   /home/temp_user/Theme/fonts/b*.chd   /usr/share/fonts/chd/b/
cp   /home/temp_user/Theme/fonts/c*.chd   /usr/share/fonts/chd/c/
cp   /home/temp_user/Theme/fonts/d*.chd   /usr/share/fonts/chd/d/
cp   /home/temp_user/Theme/fonts/e*.chd   /usr/share/fonts/chd/e/
cp   /home/temp_user/Theme/fonts/f*.chd   /usr/share/fonts/chd/f/
cp   /home/temp_user/Theme/fonts/g*.chd   /usr/share/fonts/chd/g/
cp   /home/temp_user/Theme/fonts/h*.chd   /usr/share/fonts/chd/h/
cp   /home/temp_user/Theme/fonts/i*.chd   /usr/share/fonts/chd/i/
cp   /home/temp_user/Theme/fonts/j*.chd   /usr/share/fonts/chd/j/
cp   /home/temp_user/Theme/fonts/k*.chd   /usr/share/fonts/chd/k/
cp   /home/temp_user/Theme/fonts/l*.chd   /usr/share/fonts/chd/l/
cp   /home/temp_user/Theme/fonts/m*.chd   /usr/share/fonts/chd/m/
cp   /home/temp_user/Theme/fonts/n*.chd   /usr/share/fonts/chd/n/
cp   /home/temp_user/Theme/fonts/o*.chd   /usr/share/fonts/chd/o/
cp   /home/temp_user/Theme/fonts/p*.chd   /usr/share/fonts/chd/p/
cp   /home/temp_user/Theme/fonts/q*.chd   /usr/share/fonts/chd/q/
cp   /home/temp_user/Theme/fonts/r*.chd   /usr/share/fonts/chd/r/
cp   /home/temp_user/Theme/fonts/s*.chd   /usr/share/fonts/chd/s/
cp   /home/temp_user/Theme/fonts/t*.chd   /usr/share/fonts/chd/t/
cp   /home/temp_user/Theme/fonts/u*.chd   /usr/share/fonts/chd/u/
cp   /home/temp_user/Theme/fonts/v*.chd   /usr/share/fonts/chd/v/
cp   /home/temp_user/Theme/fonts/w*.chd   /usr/share/fonts/chd/w/
cp   /home/temp_user/Theme/fonts/x*.chd   /usr/share/fonts/chd/x/
cp   /home/temp_user/Theme/fonts/y*.chd   /usr/share/fonts/chd/y/
cp   /home/temp_user/Theme/fonts/z*.chd   /usr/share/fonts/chd/z/
cp   /home/temp_user/Theme/fonts/0*.chd   /usr/share/fonts/chd/0/
cp   /home/temp_user/Theme/fonts/1*.chd   /usr/share/fonts/chd/1/
cp   /home/temp_user/Theme/fonts/2*.chd   /usr/share/fonts/chd/2/
cp   /home/temp_user/Theme/fonts/3*.chd   /usr/share/fonts/chd/3/
cp   /home/temp_user/Theme/fonts/4*.chd   /usr/share/fonts/chd/4/
cp   /home/temp_user/Theme/fonts/5*.chd   /usr/share/fonts/chd/5/
cp   /home/temp_user/Theme/fonts/6*.chd   /usr/share/fonts/chd/6/
cp   /home/temp_user/Theme/fonts/7*.chd   /usr/share/fonts/chd/7/
cp   /home/temp_user/Theme/fonts/8*.chd   /usr/share/fonts/chd/8/
cp   /home/temp_user/Theme/fonts/9*.chd   /usr/share/fonts/chd/9/
cp   /home/temp_user/Theme/fonts/[*.chd   /usr/share/fonts/chd/other/

echo FIF
cp   /home/temp_user/Theme/fonts/_*.fif   /usr/share/fonts/fif/other/
cp   /home/temp_user/Theme/fonts/a*.fif   /usr/share/fonts/fif/a/
cp   /home/temp_user/Theme/fonts/b*.fif   /usr/share/fonts/fif/b/
cp   /home/temp_user/Theme/fonts/c*.fif   /usr/share/fonts/fif/c/
cp   /home/temp_user/Theme/fonts/d*.fif   /usr/share/fonts/fif/d/
cp   /home/temp_user/Theme/fonts/e*.fif   /usr/share/fonts/fif/e/
cp   /home/temp_user/Theme/fonts/f*.fif   /usr/share/fonts/fif/f/
cp   /home/temp_user/Theme/fonts/g*.fif   /usr/share/fonts/fif/g/
cp   /home/temp_user/Theme/fonts/h*.fif   /usr/share/fonts/fif/h/
cp   /home/temp_user/Theme/fonts/i*.fif   /usr/share/fonts/fif/i/
cp   /home/temp_user/Theme/fonts/j*.fif   /usr/share/fonts/fif/j/
cp   /home/temp_user/Theme/fonts/k*.fif   /usr/share/fonts/fif/k/
cp   /home/temp_user/Theme/fonts/l*.fif   /usr/share/fonts/fif/l/
cp   /home/temp_user/Theme/fonts/m*.fif   /usr/share/fonts/fif/m/
cp   /home/temp_user/Theme/fonts/n*.fif   /usr/share/fonts/fif/n/
cp   /home/temp_user/Theme/fonts/o*.fif   /usr/share/fonts/fif/o/
cp   /home/temp_user/Theme/fonts/p*.fif   /usr/share/fonts/fif/p/
cp   /home/temp_user/Theme/fonts/q*.fif   /usr/share/fonts/fif/q/
cp   /home/temp_user/Theme/fonts/r*.fif   /usr/share/fonts/fif/r/
cp   /home/temp_user/Theme/fonts/s*.fif   /usr/share/fonts/fif/s/
cp   /home/temp_user/Theme/fonts/t*.fif   /usr/share/fonts/fif/t/
cp   /home/temp_user/Theme/fonts/u*.fif   /usr/share/fonts/fif/u/
cp   /home/temp_user/Theme/fonts/v*.fif   /usr/share/fonts/fif/v/
cp   /home/temp_user/Theme/fonts/w*.fif   /usr/share/fonts/fif/w/
cp   /home/temp_user/Theme/fonts/x*.fif   /usr/share/fonts/fif/x/
cp   /home/temp_user/Theme/fonts/y*.fif   /usr/share/fonts/fif/y/
cp   /home/temp_user/Theme/fonts/z*.fif   /usr/share/fonts/fif/z/
cp   /home/temp_user/Theme/fonts/0*.fif   /usr/share/fonts/fif/0/
cp   /home/temp_user/Theme/fonts/1*.fif   /usr/share/fonts/fif/1/
cp   /home/temp_user/Theme/fonts/2*.fif   /usr/share/fonts/fif/2/
cp   /home/temp_user/Theme/fonts/3*.fif   /usr/share/fonts/fif/3/
cp   /home/temp_user/Theme/fonts/4*.fif   /usr/share/fonts/fif/4/
cp   /home/temp_user/Theme/fonts/5*.fif   /usr/share/fonts/fif/5/
cp   /home/temp_user/Theme/fonts/6*.fif   /usr/share/fonts/fif/6/
cp   /home/temp_user/Theme/fonts/7*.fif   /usr/share/fonts/fif/7/
cp   /home/temp_user/Theme/fonts/8*.fif   /usr/share/fonts/fif/8/
cp   /home/temp_user/Theme/fonts/9*.fif   /usr/share/fonts/fif/9/
cp   /home/temp_user/Theme/fonts/[*.fif   /usr/share/fonts/fif/other/

echo FLI
cp   /home/temp_user/Theme/fonts/_*.fli   /usr/share/fonts/fli/other/
cp   /home/temp_user/Theme/fonts/a*.fli   /usr/share/fonts/fli/a/
cp   /home/temp_user/Theme/fonts/b*.fli   /usr/share/fonts/fli/b/
cp   /home/temp_user/Theme/fonts/c*.fli   /usr/share/fonts/fli/c/
cp   /home/temp_user/Theme/fonts/d*.fli   /usr/share/fonts/fli/d/
cp   /home/temp_user/Theme/fonts/e*.fli   /usr/share/fonts/fli/e/
cp   /home/temp_user/Theme/fonts/f*.fli   /usr/share/fonts/fli/f/
cp   /home/temp_user/Theme/fonts/g*.fli   /usr/share/fonts/fli/g/
cp   /home/temp_user/Theme/fonts/h*.fli   /usr/share/fonts/fli/h/
cp   /home/temp_user/Theme/fonts/i*.fli   /usr/share/fonts/fli/i/
cp   /home/temp_user/Theme/fonts/j*.fli   /usr/share/fonts/fli/j/
cp   /home/temp_user/Theme/fonts/k*.fli   /usr/share/fonts/fli/k/
cp   /home/temp_user/Theme/fonts/l*.fli   /usr/share/fonts/fli/l/
cp   /home/temp_user/Theme/fonts/m*.fli   /usr/share/fonts/fli/m/
cp   /home/temp_user/Theme/fonts/n*.fli   /usr/share/fonts/fli/n/
cp   /home/temp_user/Theme/fonts/o*.fli   /usr/share/fonts/fli/o/
cp   /home/temp_user/Theme/fonts/p*.fli   /usr/share/fonts/fli/p/
cp   /home/temp_user/Theme/fonts/q*.fli   /usr/share/fonts/fli/q/
cp   /home/temp_user/Theme/fonts/r*.fli   /usr/share/fonts/fli/r/
cp   /home/temp_user/Theme/fonts/s*.fli   /usr/share/fonts/fli/s/
cp   /home/temp_user/Theme/fonts/t*.fli   /usr/share/fonts/fli/t/
cp   /home/temp_user/Theme/fonts/u*.fli   /usr/share/fonts/fli/u/
cp   /home/temp_user/Theme/fonts/v*.fli   /usr/share/fonts/fli/v/
cp   /home/temp_user/Theme/fonts/w*.fli   /usr/share/fonts/fli/w/
cp   /home/temp_user/Theme/fonts/x*.fli   /usr/share/fonts/fli/x/
cp   /home/temp_user/Theme/fonts/y*.fli   /usr/share/fonts/fli/y/
cp   /home/temp_user/Theme/fonts/z*.fli   /usr/share/fonts/fli/z/
cp   /home/temp_user/Theme/fonts/0*.fli   /usr/share/fonts/fli/0/
cp   /home/temp_user/Theme/fonts/1*.fli   /usr/share/fonts/fli/1/
cp   /home/temp_user/Theme/fonts/2*.fli   /usr/share/fonts/fli/2/
cp   /home/temp_user/Theme/fonts/3*.fli   /usr/share/fonts/fli/3/
cp   /home/temp_user/Theme/fonts/4*.fli   /usr/share/fonts/fli/4/
cp   /home/temp_user/Theme/fonts/5*.fli   /usr/share/fonts/fli/5/
cp   /home/temp_user/Theme/fonts/6*.fli   /usr/share/fonts/fli/6/
cp   /home/temp_user/Theme/fonts/7*.fli   /usr/share/fonts/fli/7/
cp   /home/temp_user/Theme/fonts/8*.fli   /usr/share/fonts/fli/8/
cp   /home/temp_user/Theme/fonts/9*.fli   /usr/share/fonts/fli/9/
cp   /home/temp_user/Theme/fonts/[*.fli   /usr/share/fonts/fli/other/

echo FNT 
cp   /home/temp_user/Theme/fonts/_*.fnt   /usr/share/fonts/fnt/other/
cp   /home/temp_user/Theme/fonts/a*.fnt   /usr/share/fonts/fnt/a/
cp   /home/temp_user/Theme/fonts/b*.fnt   /usr/share/fonts/fnt/b/
cp   /home/temp_user/Theme/fonts/c*.fnt   /usr/share/fonts/fnt/c/
cp   /home/temp_user/Theme/fonts/d*.fnt   /usr/share/fonts/fnt/d/
cp   /home/temp_user/Theme/fonts/e*.fnt   /usr/share/fonts/fnt/e/
cp   /home/temp_user/Theme/fonts/f*.fnt   /usr/share/fonts/fnt/f/
cp   /home/temp_user/Theme/fonts/g*.fnt   /usr/share/fonts/fnt/g/
cp   /home/temp_user/Theme/fonts/h*.fnt   /usr/share/fonts/fnt/h/
cp   /home/temp_user/Theme/fonts/i*.fnt   /usr/share/fonts/fnt/i/
cp   /home/temp_user/Theme/fonts/j*.fnt   /usr/share/fonts/fnt/j/
cp   /home/temp_user/Theme/fonts/k*.fnt   /usr/share/fonts/fnt/k/
cp   /home/temp_user/Theme/fonts/l*.fnt   /usr/share/fonts/fnt/l/
cp   /home/temp_user/Theme/fonts/m*.fnt   /usr/share/fonts/fnt/m/
cp   /home/temp_user/Theme/fonts/n*.fnt   /usr/share/fonts/fnt/n/
cp   /home/temp_user/Theme/fonts/o*.fnt   /usr/share/fonts/fnt/o/
cp   /home/temp_user/Theme/fonts/p*.fnt   /usr/share/fonts/fnt/p/
cp   /home/temp_user/Theme/fonts/q*.fnt   /usr/share/fonts/fnt/q/
cp   /home/temp_user/Theme/fonts/r*.fnt   /usr/share/fonts/fnt/r/
cp   /home/temp_user/Theme/fonts/s*.fnt   /usr/share/fonts/fnt/s/
cp   /home/temp_user/Theme/fonts/t*.fnt   /usr/share/fonts/fnt/t/
cp   /home/temp_user/Theme/fonts/u*.fnt   /usr/share/fonts/fnt/u/
cp   /home/temp_user/Theme/fonts/v*.fnt   /usr/share/fonts/fnt/v/
cp   /home/temp_user/Theme/fonts/w*.fnt   /usr/share/fonts/fnt/w/
cp   /home/temp_user/Theme/fonts/x*.fnt   /usr/share/fonts/fnt/x/
cp   /home/temp_user/Theme/fonts/y*.fnt   /usr/share/fonts/fnt/y/
cp   /home/temp_user/Theme/fonts/z*.fnt   /usr/share/fonts/fnt/z/
cp   /home/temp_user/Theme/fonts/0*.fnt   /usr/share/fonts/fnt/0/
cp   /home/temp_user/Theme/fonts/1*.fnt   /usr/share/fonts/fnt/1/
cp   /home/temp_user/Theme/fonts/2*.fnt   /usr/share/fonts/fnt/2/
cp   /home/temp_user/Theme/fonts/3*.fnt   /usr/share/fonts/fnt/3/
cp   /home/temp_user/Theme/fonts/4*.fnt   /usr/share/fonts/fnt/4/
cp   /home/temp_user/Theme/fonts/5*.fnt   /usr/share/fonts/fnt/5/
cp   /home/temp_user/Theme/fonts/6*.fnt   /usr/share/fonts/fnt/6/
cp   /home/temp_user/Theme/fonts/7*.fnt   /usr/share/fonts/fnt/7/
cp   /home/temp_user/Theme/fonts/8*.fnt   /usr/share/fonts/fnt/8/
cp   /home/temp_user/Theme/fonts/9*.fnt   /usr/share/fonts/fnt/9/
cp   /home/temp_user/Theme/fonts/[*.fnt   /usr/share/fonts/fnt/other/

FON 
cp   /home/temp_user/Theme/fonts/_*.fon   /usr/share/fonts/font/other/
cp   /home/temp_user/Theme/fonts/a*.fon   /usr/share/fonts/fon/a/
cp   /home/temp_user/Theme/fonts/b*.fon   /usr/share/fonts/fon/b/
cp   /home/temp_user/Theme/fonts/c*.fon   /usr/share/fonts/fon/c/
cp   /home/temp_user/Theme/fonts/d*.fon   /usr/share/fonts/fon/d/
cp   /home/temp_user/Theme/fonts/e*.fon   /usr/share/fonts/fon/e/
cp   /home/temp_user/Theme/fonts/f*.fon   /usr/share/fonts/fon/f/
cp   /home/temp_user/Theme/fonts/g*.fon   /usr/share/fonts/fon/g/
cp   /home/temp_user/Theme/fonts/h*.fon   /usr/share/fonts/fon/h/
cp   /home/temp_user/Theme/fonts/i*.fon   /usr/share/fonts/fon/i/
cp   /home/temp_user/Theme/fonts/j*.fon   /usr/share/fonts/fon/j/
cp   /home/temp_user/Theme/fonts/k*.fon   /usr/share/fonts/fon/k/
cp   /home/temp_user/Theme/fonts/l*.fon   /usr/share/fonts/fon/l/
cp   /home/temp_user/Theme/fonts/m*.fon   /usr/share/fonts/fon/m/
cp   /home/temp_user/Theme/fonts/n*.fon   /usr/share/fonts/fon/n/
cp   /home/temp_user/Theme/fonts/o*.fon   /usr/share/fonts/fon/o/
cp   /home/temp_user/Theme/fonts/p*.fon   /usr/share/fonts/fon/p/
cp   /home/temp_user/Theme/fonts/q*.fon   /usr/share/fonts/fon/q/
cp   /home/temp_user/Theme/fonts/r*.fon   /usr/share/fonts/fon/r/
cp   /home/temp_user/Theme/fonts/s*.fon   /usr/share/fonts/fon/s/
cp   /home/temp_user/Theme/fonts/t*.fon   /usr/share/fonts/fon/t/
cp   /home/temp_user/Theme/fonts/u*.fon   /usr/share/fonts/fon/u/
cp   /home/temp_user/Theme/fonts/v*.fon   /usr/share/fonts/fon/v/
cp   /home/temp_user/Theme/fonts/w*.fon   /usr/share/fonts/fon/w/
cp   /home/temp_user/Theme/fonts/x*.fon   /usr/share/fonts/fon/x/
cp   /home/temp_user/Theme/fonts/y*.fon   /usr/share/fonts/fon/y/
cp   /home/temp_user/Theme/fonts/z*.fon   /usr/share/fonts/fon/z/
cp   /home/temp_user/Theme/fonts/0*.fon   /usr/share/fonts/fon/0/
cp   /home/temp_user/Theme/fonts/1*.fon   /usr/share/fonts/fon/1/
cp   /home/temp_user/Theme/fonts/2*.fon   /usr/share/fonts/fon/2/
cp   /home/temp_user/Theme/fonts/3*.fon   /usr/share/fonts/fon/3/
cp   /home/temp_user/Theme/fonts/4*.fon   /usr/share/fonts/fon/4/
cp   /home/temp_user/Theme/fonts/5*.fon   /usr/share/fonts/fon/5/
cp   /home/temp_user/Theme/fonts/6*.fon   /usr/share/fonts/fon/6/
cp   /home/temp_user/Theme/fonts/7*.fon   /usr/share/fonts/fon/7/
cp   /home/temp_user/Theme/fonts/8*.fon   /usr/share/fonts/fon/8/
cp   /home/temp_user/Theme/fonts/9*.fon   /usr/share/fonts/fon/9/
cp   /home/temp_user/Theme/fonts/[*.fon   /usr/share/fonts/fon/other/

echo FRS
cp   /home/temp_user/Theme/fonts/_*.frs   /usr/share/fonts/frs/other/
cp   /home/temp_user/Theme/fonts/a*.frs   /usr/share/fonts/frs/a/
cp   /home/temp_user/Theme/fonts/b*.frs   /usr/share/fonts/frs/b/
cp   /home/temp_user/Theme/fonts/c*.frs   /usr/share/fonts/frs/c/
cp   /home/temp_user/Theme/fonts/d*.frs   /usr/share/fonts/frs/d/
cp   /home/temp_user/Theme/fonts/e*.frs   /usr/share/fonts/frs/e/
cp   /home/temp_user/Theme/fonts/f*.frs   /usr/share/fonts/frs/f/
cp   /home/temp_user/Theme/fonts/g*.frs   /usr/share/fonts/frs/g/
cp   /home/temp_user/Theme/fonts/h*.frs   /usr/share/fonts/frs/h/
cp   /home/temp_user/Theme/fonts/i*.frs   /usr/share/fonts/frs/i/
cp   /home/temp_user/Theme/fonts/j*.frs   /usr/share/fonts/frs/j/
cp   /home/temp_user/Theme/fonts/k*.frs   /usr/share/fonts/frs/k/
cp   /home/temp_user/Theme/fonts/l*.frs   /usr/share/fonts/frs/l/
cp   /home/temp_user/Theme/fonts/m*.frs   /usr/share/fonts/frs/m/
cp   /home/temp_user/Theme/fonts/n*.frs   /usr/share/fonts/frs/n/
cp   /home/temp_user/Theme/fonts/o*.frs   /usr/share/fonts/frs/o/
cp   /home/temp_user/Theme/fonts/p*.frs   /usr/share/fonts/frs/p/
cp   /home/temp_user/Theme/fonts/q*.frs   /usr/share/fonts/frs/q/
cp   /home/temp_user/Theme/fonts/r*.frs   /usr/share/fonts/frs/r/
cp   /home/temp_user/Theme/fonts/s*.frs   /usr/share/fonts/frs/s/
cp   /home/temp_user/Theme/fonts/t*.frs   /usr/share/fonts/frs/t/
cp   /home/temp_user/Theme/fonts/u*.frs   /usr/share/fonts/frs/u/
cp   /home/temp_user/Theme/fonts/v*.frs   /usr/share/fonts/frs/v/
cp   /home/temp_user/Theme/fonts/w*.frs   /usr/share/fonts/frs/w/
cp   /home/temp_user/Theme/fonts/x*.frs   /usr/share/fonts/frs/x/
cp   /home/temp_user/Theme/fonts/y*.frs   /usr/share/fonts/frs/y/
cp   /home/temp_user/Theme/fonts/z*.frs   /usr/share/fonts/frs/z/
cp   /home/temp_user/Theme/fonts/0*.frs   /usr/share/fonts/frs/0/
cp   /home/temp_user/Theme/fonts/1*.frs   /usr/share/fonts/frs/1/
cp   /home/temp_user/Theme/fonts/2*.frs   /usr/share/fonts/frs/2/
cp   /home/temp_user/Theme/fonts/3*.frs   /usr/share/fonts/frs/3/
cp   /home/temp_user/Theme/fonts/4*.frs   /usr/share/fonts/frs/4/
cp   /home/temp_user/Theme/fonts/5*.frs   /usr/share/fonts/frs/5/
cp   /home/temp_user/Theme/fonts/6*.frs   /usr/share/fonts/frs/6/
cp   /home/temp_user/Theme/fonts/7*.frs   /usr/share/fonts/frs/7/
cp   /home/temp_user/Theme/fonts/8*.frs   /usr/share/fonts/frs/8/
cp   /home/temp_user/Theme/fonts/9*.frs   /usr/share/fonts/frs/9/
cp   /home/temp_user/Theme/fonts/[*.frs   /usr/share/fonts/frs/other/

echo GLF
cp   /home/temp_user/Theme/fonts/_*.glf   /usr/share/fonts/glf/other/
cp   /home/temp_user/Theme/fonts/a*.glf   /usr/share/fonts/glf/a/
cp   /home/temp_user/Theme/fonts/b*.glf   /usr/share/fonts/glf/b/
cp   /home/temp_user/Theme/fonts/c*.glf   /usr/share/fonts/glf/c/
cp   /home/temp_user/Theme/fonts/d*.glf   /usr/share/fonts/glf/d/
cp   /home/temp_user/Theme/fonts/e*.glf   /usr/share/fonts/glf/e/
cp   /home/temp_user/Theme/fonts/f*.glf   /usr/share/fonts/glf/f/
cp   /home/temp_user/Theme/fonts/g*.glf   /usr/share/fonts/glf/g/
cp   /home/temp_user/Theme/fonts/h*.glf   /usr/share/fonts/glf/h/
cp   /home/temp_user/Theme/fonts/i*.glf   /usr/share/fonts/glf/i/
cp   /home/temp_user/Theme/fonts/j*.glf   /usr/share/fonts/glf/j/
cp   /home/temp_user/Theme/fonts/k*.glf   /usr/share/fonts/glf/k/
cp   /home/temp_user/Theme/fonts/l*.glf   /usr/share/fonts/glf/l/
cp   /home/temp_user/Theme/fonts/m*.glf   /usr/share/fonts/glf/m/
cp   /home/temp_user/Theme/fonts/n*.glf   /usr/share/fonts/glf/n/
cp   /home/temp_user/Theme/fonts/o*.glf   /usr/share/fonts/glf/o/
cp   /home/temp_user/Theme/fonts/p*.glf   /usr/share/fonts/glf/p/
cp   /home/temp_user/Theme/fonts/q*.glf   /usr/share/fonts/glf/q/
cp   /home/temp_user/Theme/fonts/r*.glf   /usr/share/fonts/glf/r/
cp   /home/temp_user/Theme/fonts/s*.glf   /usr/share/fonts/glf/s/
cp   /home/temp_user/Theme/fonts/t*.glf   /usr/share/fonts/glf/t/
cp   /home/temp_user/Theme/fonts/u*.glf   /usr/share/fonts/glf/u/
cp   /home/temp_user/Theme/fonts/v*.glf   /usr/share/fonts/glf/v/
cp   /home/temp_user/Theme/fonts/w*.glf   /usr/share/fonts/glf/w/
cp   /home/temp_user/Theme/fonts/x*.glf   /usr/share/fonts/glf/x/
cp   /home/temp_user/Theme/fonts/y*.glf   /usr/share/fonts/glf/y/
cp   /home/temp_user/Theme/fonts/z*.glf   /usr/share/fonts/glf/z/
cp   /home/temp_user/Theme/fonts/0*.glf   /usr/share/fonts/glf/0/
cp   /home/temp_user/Theme/fonts/1*.glf   /usr/share/fonts/glf/1/
cp   /home/temp_user/Theme/fonts/2*.glf   /usr/share/fonts/glf/2/
cp   /home/temp_user/Theme/fonts/3*.glf   /usr/share/fonts/glf/3/
cp   /home/temp_user/Theme/fonts/4*.glf   /usr/share/fonts/glf/4/
cp   /home/temp_user/Theme/fonts/5*.glf   /usr/share/fonts/glf/5/
cp   /home/temp_user/Theme/fonts/6*.glf   /usr/share/fonts/glf/6/
cp   /home/temp_user/Theme/fonts/7*.glf   /usr/share/fonts/glf/7/
cp   /home/temp_user/Theme/fonts/8*.glf   /usr/share/fonts/glf/8/
cp   /home/temp_user/Theme/fonts/9*.glf   /usr/share/fonts/glf/9/
cp   /home/temp_user/Theme/fonts/[*.glf   /usr/share/fonts/glf/other/

echo HPC
cp   /home/temp_user/Theme/fonts/_*.hpc   /usr/share/fonts/hpc/other/
cp   /home/temp_user/Theme/fonts/a*.hpc   /usr/share/fonts/hpc/a/
cp   /home/temp_user/Theme/fonts/b*.hpc   /usr/share/fonts/hpc/b/
cp   /home/temp_user/Theme/fonts/c*.hpc   /usr/share/fonts/hpc/c/
cp   /home/temp_user/Theme/fonts/d*.hpc   /usr/share/fonts/hpc/d/
cp   /home/temp_user/Theme/fonts/e*.hpc   /usr/share/fonts/hpc/e/
cp   /home/temp_user/Theme/fonts/f*.hpc   /usr/share/fonts/hpc/f/
cp   /home/temp_user/Theme/fonts/g*.hpc   /usr/share/fonts/hpc/g/
cp   /home/temp_user/Theme/fonts/h*.hpc   /usr/share/fonts/hpc/h/
cp   /home/temp_user/Theme/fonts/i*.hpc   /usr/share/fonts/hpc/i/
cp   /home/temp_user/Theme/fonts/j*.hpc   /usr/share/fonts/hpc/j/
cp   /home/temp_user/Theme/fonts/k*.hpc   /usr/share/fonts/hpc/k/
cp   /home/temp_user/Theme/fonts/l*.hpc   /usr/share/fonts/hpc/l/
cp   /home/temp_user/Theme/fonts/m*.hpc   /usr/share/fonts/hpc/m/
cp   /home/temp_user/Theme/fonts/n*.hpc   /usr/share/fonts/hpc/n/
cp   /home/temp_user/Theme/fonts/o*.hpc   /usr/share/fonts/hpc/o/
cp   /home/temp_user/Theme/fonts/p*.hpc   /usr/share/fonts/hpc/p/
cp   /home/temp_user/Theme/fonts/q*.hpc   /usr/share/fonts/hpc/q/
cp   /home/temp_user/Theme/fonts/r*.hpc   /usr/share/fonts/hpc/r/
cp   /home/temp_user/Theme/fonts/s*.hpc   /usr/share/fonts/hpc/s/
cp   /home/temp_user/Theme/fonts/t*.hpc   /usr/share/fonts/hpc/t/
cp   /home/temp_user/Theme/fonts/u*.hpc   /usr/share/fonts/hpc/u/
cp   /home/temp_user/Theme/fonts/v*.hpc   /usr/share/fonts/hpc/v/
cp   /home/temp_user/Theme/fonts/w*.hpc   /usr/share/fonts/hpc/w/
cp   /home/temp_user/Theme/fonts/x*.hpc   /usr/share/fonts/hpc/x/
cp   /home/temp_user/Theme/fonts/y*.hpc   /usr/share/fonts/hpc/y/
cp   /home/temp_user/Theme/fonts/z*.hpc   /usr/share/fonts/hpc/z/
cp   /home/temp_user/Theme/fonts/0*.hpc   /usr/share/fonts/hpc/0/
cp   /home/temp_user/Theme/fonts/1*.hpc   /usr/share/fonts/hpc/1/
cp   /home/temp_user/Theme/fonts/2*.hpc   /usr/share/fonts/hpc/2/
cp   /home/temp_user/Theme/fonts/3*.hpc   /usr/share/fonts/hpc/3/
cp   /home/temp_user/Theme/fonts/4*.hpc   /usr/share/fonts/hpc/4/
cp   /home/temp_user/Theme/fonts/5*.hpc   /usr/share/fonts/hpc/5/
cp   /home/temp_user/Theme/fonts/6*.hpc   /usr/share/fonts/hpc/6/
cp   /home/temp_user/Theme/fonts/7*.hpc   /usr/share/fonts/hpc/7/
cp   /home/temp_user/Theme/fonts/8*.hpc   /usr/share/fonts/hpc/8/
cp   /home/temp_user/Theme/fonts/9*.hpc   /usr/share/fonts/hpc/9/
cp   /home/temp_user/Theme/fonts/[*.hpc   /usr/share/fonts/hpc/other/

echo HPI
cp   /home/temp_user/Theme/fonts/_*.hpi   /usr/share/fonts/hpi/other/
cp   /home/temp_user/Theme/fonts/a*.hpi   /usr/share/fonts/hpi/a/
cp   /home/temp_user/Theme/fonts/b*.hpi   /usr/share/fonts/hpi/b/
cp   /home/temp_user/Theme/fonts/c*.hpi   /usr/share/fonts/hpi/c/
cp   /home/temp_user/Theme/fonts/d*.hpi   /usr/share/fonts/hpi/d/
cp   /home/temp_user/Theme/fonts/e*.hpi   /usr/share/fonts/hpi/e/
cp   /home/temp_user/Theme/fonts/f*.hpi   /usr/share/fonts/hpi/f/
cp   /home/temp_user/Theme/fonts/g*.hpi   /usr/share/fonts/hpi/g/
cp   /home/temp_user/Theme/fonts/h*.hpi   /usr/share/fonts/hpi/h/
cp   /home/temp_user/Theme/fonts/i*.hpi   /usr/share/fonts/hpi/i/
cp   /home/temp_user/Theme/fonts/j*.hpi   /usr/share/fonts/hpi/j/
cp   /home/temp_user/Theme/fonts/k*.hpi   /usr/share/fonts/hpi/k/
cp   /home/temp_user/Theme/fonts/l*.hpi   /usr/share/fonts/hpi/l/
cp   /home/temp_user/Theme/fonts/m*.hpi   /usr/share/fonts/hpi/m/
cp   /home/temp_user/Theme/fonts/n*.hpi   /usr/share/fonts/hpi/n/
cp   /home/temp_user/Theme/fonts/o*.hpi   /usr/share/fonts/hpi/o/
cp   /home/temp_user/Theme/fonts/p*.hpi   /usr/share/fonts/hpi/p/
cp   /home/temp_user/Theme/fonts/q*.hpi   /usr/share/fonts/hpi/q/
cp   /home/temp_user/Theme/fonts/r*.hpi   /usr/share/fonts/hpi/r/
cp   /home/temp_user/Theme/fonts/s*.hpi   /usr/share/fonts/hpi/s/
cp   /home/temp_user/Theme/fonts/t*.hpi   /usr/share/fonts/hpi/t/
cp   /home/temp_user/Theme/fonts/u*.hpi   /usr/share/fonts/hpi/u/
cp   /home/temp_user/Theme/fonts/v*.hpi   /usr/share/fonts/hpi/v/
cp   /home/temp_user/Theme/fonts/w*.hpi   /usr/share/fonts/hpi/w/
cp   /home/temp_user/Theme/fonts/x*.hpi   /usr/share/fonts/hpi/x/
cp   /home/temp_user/Theme/fonts/y*.hpi   /usr/share/fonts/hpi/y/
cp   /home/temp_user/Theme/fonts/z*.hpi   /usr/share/fonts/hpi/z/
cp   /home/temp_user/Theme/fonts/0*.hpi   /usr/share/fonts/hpi/0/
cp   /home/temp_user/Theme/fonts/1*.hpi   /usr/share/fonts/hpi/1/
cp   /home/temp_user/Theme/fonts/2*.hpi   /usr/share/fonts/hpi/2/
cp   /home/temp_user/Theme/fonts/3*.hpi   /usr/share/fonts/hpi/3/
cp   /home/temp_user/Theme/fonts/4*.hpi   /usr/share/fonts/hpi/4/
cp   /home/temp_user/Theme/fonts/5*.hpi   /usr/share/fonts/hpi/5/
cp   /home/temp_user/Theme/fonts/6*.hpi   /usr/share/fonts/hpi/6/
cp   /home/temp_user/Theme/fonts/7*.hpi   /usr/share/fonts/hpi/7/
cp   /home/temp_user/Theme/fonts/8*.hpi   /usr/share/fonts/hpi/8/
cp   /home/temp_user/Theme/fonts/9*.hpi   /usr/share/fonts/hpi/9/
cp   /home/temp_user/Theme/fonts/[*.hpi   /usr/share/fonts/hpi/other/

echo LXO
cp   /home/temp_user/Theme/fonts/_*.lxo   /usr/share/fonts/lxo/other/
cp   /home/temp_user/Theme/fonts/a*.lxo   /usr/share/fonts/lxo/a/
cp   /home/temp_user/Theme/fonts/b*.lxo   /usr/share/fonts/lxo/b/
cp   /home/temp_user/Theme/fonts/c*.lxo   /usr/share/fonts/lxo/c/
cp   /home/temp_user/Theme/fonts/d*.lxo   /usr/share/fonts/lxo/d/
cp   /home/temp_user/Theme/fonts/e*.lxo   /usr/share/fonts/lxo/e/
cp   /home/temp_user/Theme/fonts/f*.lxo   /usr/share/fonts/lxo/f/
cp   /home/temp_user/Theme/fonts/g*.lxo   /usr/share/fonts/lxo/g/
cp   /home/temp_user/Theme/fonts/h*.lxo   /usr/share/fonts/lxo/h/
cp   /home/temp_user/Theme/fonts/i*.lxo   /usr/share/fonts/lxo/i/
cp   /home/temp_user/Theme/fonts/j*.lxo   /usr/share/fonts/lxo/j/
cp   /home/temp_user/Theme/fonts/k*.lxo   /usr/share/fonts/lxo/k/
cp   /home/temp_user/Theme/fonts/l*.lxo   /usr/share/fonts/lxo/l/
cp   /home/temp_user/Theme/fonts/m*.lxo   /usr/share/fonts/lxo/m/
cp   /home/temp_user/Theme/fonts/n*.lxo   /usr/share/fonts/lxo/n/
cp   /home/temp_user/Theme/fonts/o*.lxo   /usr/share/fonts/lxo/o/
cp   /home/temp_user/Theme/fonts/p*.lxo   /usr/share/fonts/lxo/p/
cp   /home/temp_user/Theme/fonts/q*.lxo   /usr/share/fonts/lxo/q/
cp   /home/temp_user/Theme/fonts/r*.lxo   /usr/share/fonts/lxo/r/
cp   /home/temp_user/Theme/fonts/s*.lxo   /usr/share/fonts/lxo/s/
cp   /home/temp_user/Theme/fonts/t*.lxo   /usr/share/fonts/lxo/t/
cp   /home/temp_user/Theme/fonts/u*.lxo   /usr/share/fonts/lxo/u/
cp   /home/temp_user/Theme/fonts/v*.lxo   /usr/share/fonts/lxo/v/
cp   /home/temp_user/Theme/fonts/w*.lxo   /usr/share/fonts/lxo/w/
cp   /home/temp_user/Theme/fonts/x*.lxo   /usr/share/fonts/lxo/x/
cp   /home/temp_user/Theme/fonts/y*.lxo   /usr/share/fonts/lxo/y/
cp   /home/temp_user/Theme/fonts/z*.lxo   /usr/share/fonts/lxo/z/
cp   /home/temp_user/Theme/fonts/0*.lxo   /usr/share/fonts/lxo/0/
cp   /home/temp_user/Theme/fonts/1*.lxo   /usr/share/fonts/lxo/1/
cp   /home/temp_user/Theme/fonts/2*.lxo   /usr/share/fonts/lxo/2/
cp   /home/temp_user/Theme/fonts/3*.lxo   /usr/share/fonts/lxo/3/
cp   /home/temp_user/Theme/fonts/4*.lxo   /usr/share/fonts/lxo/4/
cp   /home/temp_user/Theme/fonts/5*.lxo   /usr/share/fonts/lxo/5/
cp   /home/temp_user/Theme/fonts/6*.lxo   /usr/share/fonts/lxo/6/
cp   /home/temp_user/Theme/fonts/7*.lxo   /usr/share/fonts/lxo/7/
cp   /home/temp_user/Theme/fonts/8*.lxo   /usr/share/fonts/lxo/8/
cp   /home/temp_user/Theme/fonts/9*.lxo   /usr/share/fonts/lxo/9/
cp   /home/temp_user/Theme/fonts/[*.lxo   /usr/share/fonts/lxo/other/

echo MMM
cp   /home/temp_user/Theme/fonts/_*.mmm   /usr/share/fonts/mmm/other/
cp   /home/temp_user/Theme/fonts/a*.mmm   /usr/share/fonts/mmm/a/
cp   /home/temp_user/Theme/fonts/b*.mmm   /usr/share/fonts/mmm/b/
cp   /home/temp_user/Theme/fonts/c*.mmm   /usr/share/fonts/mmm/c/
cp   /home/temp_user/Theme/fonts/d*.mmm   /usr/share/fonts/mmm/d/
cp   /home/temp_user/Theme/fonts/e*.mmm   /usr/share/fonts/mmm/e/
cp   /home/temp_user/Theme/fonts/f*.mmm   /usr/share/fonts/mmm/f/
cp   /home/temp_user/Theme/fonts/g*.mmm   /usr/share/fonts/mmm/g/
cp   /home/temp_user/Theme/fonts/h*.mmm   /usr/share/fonts/mmm/h/
cp   /home/temp_user/Theme/fonts/i*.mmm   /usr/share/fonts/mmm/i/
cp   /home/temp_user/Theme/fonts/j*.mmm   /usr/share/fonts/mmm/j/
cp   /home/temp_user/Theme/fonts/k*.mmm   /usr/share/fonts/mmm/k/
cp   /home/temp_user/Theme/fonts/l*.mmm   /usr/share/fonts/mmm/l/
cp   /home/temp_user/Theme/fonts/m*.mmm   /usr/share/fonts/mmm/m/
cp   /home/temp_user/Theme/fonts/n*.mmm   /usr/share/fonts/mmm/n/
cp   /home/temp_user/Theme/fonts/o*.mmm   /usr/share/fonts/mmm/o/
cp   /home/temp_user/Theme/fonts/p*.mmm   /usr/share/fonts/mmm/p/
cp   /home/temp_user/Theme/fonts/q*.mmm   /usr/share/fonts/mmm/q/
cp   /home/temp_user/Theme/fonts/r*.mmm   /usr/share/fonts/mmm/r/
cp   /home/temp_user/Theme/fonts/s*.mmm   /usr/share/fonts/mmm/s/
cp   /home/temp_user/Theme/fonts/t*.mmm   /usr/share/fonts/mmm/t/
cp   /home/temp_user/Theme/fonts/u*.mmm   /usr/share/fonts/mmm/u/
cp   /home/temp_user/Theme/fonts/v*.mmm   /usr/share/fonts/mmm/v/
cp   /home/temp_user/Theme/fonts/w*.mmm   /usr/share/fonts/mmm/w/
cp   /home/temp_user/Theme/fonts/x*.mmm   /usr/share/fonts/mmm/x/
cp   /home/temp_user/Theme/fonts/y*.mmm   /usr/share/fonts/mmm/y/
cp   /home/temp_user/Theme/fonts/z*.mmm   /usr/share/fonts/mmm/z/
cp   /home/temp_user/Theme/fonts/0*.mmm   /usr/share/fonts/mmm/0/
cp   /home/temp_user/Theme/fonts/1*.mmm   /usr/share/fonts/mmm/1/
cp   /home/temp_user/Theme/fonts/2*.mmm   /usr/share/fonts/mmm/2/
cp   /home/temp_user/Theme/fonts/3*.mmm   /usr/share/fonts/mmm/3/
cp   /home/temp_user/Theme/fonts/4*.mmm   /usr/share/fonts/mmm/4/
cp   /home/temp_user/Theme/fonts/5*.mmm   /usr/share/fonts/mmm/5/
cp   /home/temp_user/Theme/fonts/6*.mmm   /usr/share/fonts/mmm/6/
cp   /home/temp_user/Theme/fonts/7*.mmm   /usr/share/fonts/mmm/7/
cp   /home/temp_user/Theme/fonts/8*.mmm   /usr/share/fonts/mmm/8/
cp   /home/temp_user/Theme/fonts/9*.mmm   /usr/share/fonts/mmm/9/
cp   /home/temp_user/Theme/fonts/[*.mmm   /usr/share/fonts/mmm/other/

echo MRF
cp   /home/temp_user/Theme/fonts/_*.mrf   /usr/share/fonts/mrf/other/
cp   /home/temp_user/Theme/fonts/a*.mrf   /usr/share/fonts/mrf/a/
cp   /home/temp_user/Theme/fonts/b*.mrf   /usr/share/fonts/mrf/b/
cp   /home/temp_user/Theme/fonts/c*.mrf   /usr/share/fonts/mrf/c/
cp   /home/temp_user/Theme/fonts/d*.mrf   /usr/share/fonts/mrf/d/
cp   /home/temp_user/Theme/fonts/e*.mrf   /usr/share/fonts/mrf/e/
cp   /home/temp_user/Theme/fonts/f*.mrf   /usr/share/fonts/mrf/f/
cp   /home/temp_user/Theme/fonts/g*.mrf   /usr/share/fonts/mrf/g/
cp   /home/temp_user/Theme/fonts/h*.mrf   /usr/share/fonts/mrf/h/
cp   /home/temp_user/Theme/fonts/i*.mrf   /usr/share/fonts/mrf/i/
cp   /home/temp_user/Theme/fonts/j*.mrf   /usr/share/fonts/mrf/j/
cp   /home/temp_user/Theme/fonts/k*.mrf   /usr/share/fonts/mrf/k/
cp   /home/temp_user/Theme/fonts/l*.mrf   /usr/share/fonts/mrf/l/
cp   /home/temp_user/Theme/fonts/m*.mrf   /usr/share/fonts/mrf/m/
cp   /home/temp_user/Theme/fonts/n*.mrf   /usr/share/fonts/mrf/n/
cp   /home/temp_user/Theme/fonts/o*.mrf   /usr/share/fonts/mrf/o/
cp   /home/temp_user/Theme/fonts/p*.mrf   /usr/share/fonts/mrf/p/
cp   /home/temp_user/Theme/fonts/q*.mrf   /usr/share/fonts/mrf/q/
cp   /home/temp_user/Theme/fonts/r*.mrf   /usr/share/fonts/mrf/r/
cp   /home/temp_user/Theme/fonts/s*.mrf   /usr/share/fonts/mrf/s/
cp   /home/temp_user/Theme/fonts/t*.mrf   /usr/share/fonts/mrf/t/
cp   /home/temp_user/Theme/fonts/u*.mrf   /usr/share/fonts/mrf/u/
cp   /home/temp_user/Theme/fonts/v*.mrf   /usr/share/fonts/mrf/v/
cp   /home/temp_user/Theme/fonts/w*.mrf   /usr/share/fonts/mrf/w/
cp   /home/temp_user/Theme/fonts/x*.mrf   /usr/share/fonts/mrf/x/
cp   /home/temp_user/Theme/fonts/y*.mrf   /usr/share/fonts/mrf/y/
cp   /home/temp_user/Theme/fonts/z*.mrf   /usr/share/fonts/mrf/z/
cp   /home/temp_user/Theme/fonts/0*.mrf   /usr/share/fonts/mrf/0/
cp   /home/temp_user/Theme/fonts/1*.mrf   /usr/share/fonts/mrf/1/
cp   /home/temp_user/Theme/fonts/2*.mrf   /usr/share/fonts/mrf/2/
cp   /home/temp_user/Theme/fonts/3*.mrf   /usr/share/fonts/mrf/3/
cp   /home/temp_user/Theme/fonts/4*.mrf   /usr/share/fonts/mrf/4/
cp   /home/temp_user/Theme/fonts/5*.mrf   /usr/share/fonts/mrf/5/
cp   /home/temp_user/Theme/fonts/6*.mrf   /usr/share/fonts/mrf/6/
cp   /home/temp_user/Theme/fonts/7*.mrf   /usr/share/fonts/mrf/7/
cp   /home/temp_user/Theme/fonts/8*.mrf   /usr/share/fonts/mrf/8/
cp   /home/temp_user/Theme/fonts/9*.mrf   /usr/share/fonts/mrf/9/
cp   /home/temp_user/Theme/fonts/[*.mrf   /usr/share/fonts/mrf/other/

echo MTF
cp   /home/temp_user/Theme/fonts/_*.mtf   /usr/share/fonts/mtf/other/
cp   /home/temp_user/Theme/fonts/a*.mtf   /usr/share/fonts/mtf/a/
cp   /home/temp_user/Theme/fonts/b*.mtf   /usr/share/fonts/mtf/b/
cp   /home/temp_user/Theme/fonts/c*.mtf   /usr/share/fonts/mtf/c/
cp   /home/temp_user/Theme/fonts/d*.mtf   /usr/share/fonts/mtf/d/
cp   /home/temp_user/Theme/fonts/e*.mtf   /usr/share/fonts/mtf/e/
cp   /home/temp_user/Theme/fonts/f*.mtf   /usr/share/fonts/mtf/f/
cp   /home/temp_user/Theme/fonts/g*.mtf   /usr/share/fonts/mtf/g/
cp   /home/temp_user/Theme/fonts/h*.mtf   /usr/share/fonts/mtf/h/
cp   /home/temp_user/Theme/fonts/i*.mtf   /usr/share/fonts/mtf/i/
cp   /home/temp_user/Theme/fonts/j*.mtf   /usr/share/fonts/mtf/j/
cp   /home/temp_user/Theme/fonts/k*.mtf   /usr/share/fonts/mtf/k/
cp   /home/temp_user/Theme/fonts/l*.mtf   /usr/share/fonts/mtf/l/
cp   /home/temp_user/Theme/fonts/m*.mtf   /usr/share/fonts/mtf/m/
cp   /home/temp_user/Theme/fonts/n*.mtf   /usr/share/fonts/mtf/n/
cp   /home/temp_user/Theme/fonts/o*.mtf   /usr/share/fonts/mtf/o/
cp   /home/temp_user/Theme/fonts/p*.mtf   /usr/share/fonts/mtf/p/
cp   /home/temp_user/Theme/fonts/q*.mtf   /usr/share/fonts/mtf/q/
cp   /home/temp_user/Theme/fonts/r*.mtf   /usr/share/fonts/mtf/r/
cp   /home/temp_user/Theme/fonts/s*.mtf   /usr/share/fonts/mtf/s/
cp   /home/temp_user/Theme/fonts/t*.mtf   /usr/share/fonts/mtf/t/
cp   /home/temp_user/Theme/fonts/u*.mtf   /usr/share/fonts/mtf/u/
cp   /home/temp_user/Theme/fonts/v*.mtf   /usr/share/fonts/mtf/v/
cp   /home/temp_user/Theme/fonts/w*.mtf   /usr/share/fonts/mtf/w/
cp   /home/temp_user/Theme/fonts/x*.mtf   /usr/share/fonts/mtf/x/
cp   /home/temp_user/Theme/fonts/y*.mtf   /usr/share/fonts/mtf/y/
cp   /home/temp_user/Theme/fonts/z*.mtf   /usr/share/fonts/mtf/z/
cp   /home/temp_user/Theme/fonts/0*.mtf   /usr/share/fonts/mtf/0/
cp   /home/temp_user/Theme/fonts/1*.mtf   /usr/share/fonts/mtf/1/
cp   /home/temp_user/Theme/fonts/2*.mtf   /usr/share/fonts/mtf/2/
cp   /home/temp_user/Theme/fonts/3*.mtf   /usr/share/fonts/mtf/3/
cp   /home/temp_user/Theme/fonts/4*.mtf   /usr/share/fonts/mtf/4/
cp   /home/temp_user/Theme/fonts/5*.mtf   /usr/share/fonts/mtf/5/
cp   /home/temp_user/Theme/fonts/6*.mtf   /usr/share/fonts/mtf/6/
cp   /home/temp_user/Theme/fonts/7*.mtf   /usr/share/fonts/mtf/7/
cp   /home/temp_user/Theme/fonts/8*.mtf   /usr/share/fonts/mtf/8/
cp   /home/temp_user/Theme/fonts/9*.mtf   /usr/share/fonts/mtf/9/
cp   /home/temp_user/Theme/fonts/[*.mtf   /usr/share/fonts/mtf/other/

echo MXF
cp   /home/temp_user/Theme/fonts/_*.mxf   /usr/share/fonts/mxf/other/
cp   /home/temp_user/Theme/fonts/a*.mxf   /usr/share/fonts/mxf/a/
cp   /home/temp_user/Theme/fonts/b*.mxf   /usr/share/fonts/mxf/b/
cp   /home/temp_user/Theme/fonts/c*.mxf   /usr/share/fonts/mxf/c/
cp   /home/temp_user/Theme/fonts/d*.mxf   /usr/share/fonts/mxf/d/
cp   /home/temp_user/Theme/fonts/e*.mxf   /usr/share/fonts/mxf/e/
cp   /home/temp_user/Theme/fonts/f*.mxf   /usr/share/fonts/mxf/f/
cp   /home/temp_user/Theme/fonts/g*.mxf   /usr/share/fonts/mxf/g/
cp   /home/temp_user/Theme/fonts/h*.mxf   /usr/share/fonts/mxf/h/
cp   /home/temp_user/Theme/fonts/i*.mxf   /usr/share/fonts/mxf/i/
cp   /home/temp_user/Theme/fonts/j*.mxf   /usr/share/fonts/mxf/j/
cp   /home/temp_user/Theme/fonts/k*.mxf   /usr/share/fonts/mxf/k/
cp   /home/temp_user/Theme/fonts/l*.mxf   /usr/share/fonts/mxf/l/
cp   /home/temp_user/Theme/fonts/m*.mxf   /usr/share/fonts/mxf/m/
cp   /home/temp_user/Theme/fonts/n*.mxf   /usr/share/fonts/mxf/n/
cp   /home/temp_user/Theme/fonts/o*.mxf   /usr/share/fonts/mxf/o/
cp   /home/temp_user/Theme/fonts/p*.mxf   /usr/share/fonts/mxf/p/
cp   /home/temp_user/Theme/fonts/q*.mxf   /usr/share/fonts/mxf/q/
cp   /home/temp_user/Theme/fonts/r*.mxf   /usr/share/fonts/mxf/r/
cp   /home/temp_user/Theme/fonts/s*.mxf   /usr/share/fonts/mxf/s/
cp   /home/temp_user/Theme/fonts/t*.mxf   /usr/share/fonts/mxf/t/
cp   /home/temp_user/Theme/fonts/u*.mxf   /usr/share/fonts/mxf/u/
cp   /home/temp_user/Theme/fonts/v*.mxf   /usr/share/fonts/mxf/v/
cp   /home/temp_user/Theme/fonts/w*.mxf   /usr/share/fonts/mxf/w/
cp   /home/temp_user/Theme/fonts/x*.mxf   /usr/share/fonts/mxf/x/
cp   /home/temp_user/Theme/fonts/y*.mxf   /usr/share/fonts/mxf/y/
cp   /home/temp_user/Theme/fonts/z*.mxf   /usr/share/fonts/mxf/z/
cp   /home/temp_user/Theme/fonts/0*.mxf   /usr/share/fonts/mxf/0/
cp   /home/temp_user/Theme/fonts/1*.mxf   /usr/share/fonts/mxf/1/
cp   /home/temp_user/Theme/fonts/2*.mxf   /usr/share/fonts/mxf/2/
cp   /home/temp_user/Theme/fonts/3*.mxf   /usr/share/fonts/mxf/3/
cp   /home/temp_user/Theme/fonts/4*.mxf   /usr/share/fonts/mxf/4/
cp   /home/temp_user/Theme/fonts/5*.mxf   /usr/share/fonts/mxf/5/
cp   /home/temp_user/Theme/fonts/6*.mxf   /usr/share/fonts/mxf/6/
cp   /home/temp_user/Theme/fonts/7*.mxf   /usr/share/fonts/mxf/7/
cp   /home/temp_user/Theme/fonts/8*.mxf   /usr/share/fonts/mxf/8/
cp   /home/temp_user/Theme/fonts/9*.mxf   /usr/share/fonts/mxf/9/
cp   /home/temp_user/Theme/fonts/[*.mxf   /usr/share/fonts/mxf/other/

echo OFM
cp   /home/temp_user/Theme/fonts/_*.ofm   /usr/share/fonts/ofm/other/
cp   /home/temp_user/Theme/fonts/a*.ofm   /usr/share/fonts/ofm/a/
cp   /home/temp_user/Theme/fonts/b*.ofm   /usr/share/fonts/ofm/b/
cp   /home/temp_user/Theme/fonts/c*.ofm   /usr/share/fonts/ofm/c/
cp   /home/temp_user/Theme/fonts/d*.ofm   /usr/share/fonts/ofm/d/
cp   /home/temp_user/Theme/fonts/e*.ofm   /usr/share/fonts/ofm/e/
cp   /home/temp_user/Theme/fonts/f*.ofm   /usr/share/fonts/ofm/f/
cp   /home/temp_user/Theme/fonts/g*.ofm   /usr/share/fonts/ofm/g/
cp   /home/temp_user/Theme/fonts/h*.ofm   /usr/share/fonts/ofm/h/
cp   /home/temp_user/Theme/fonts/i*.ofm   /usr/share/fonts/ofm/i/
cp   /home/temp_user/Theme/fonts/j*.ofm   /usr/share/fonts/ofm/j/
cp   /home/temp_user/Theme/fonts/k*.ofm   /usr/share/fonts/ofm/k/
cp   /home/temp_user/Theme/fonts/l*.ofm   /usr/share/fonts/ofm/l/
cp   /home/temp_user/Theme/fonts/m*.ofm   /usr/share/fonts/ofm/m/
cp   /home/temp_user/Theme/fonts/n*.ofm   /usr/share/fonts/ofm/n/
cp   /home/temp_user/Theme/fonts/o*.ofm   /usr/share/fonts/ofm/o/
cp   /home/temp_user/Theme/fonts/p*.ofm   /usr/share/fonts/ofm/p/
cp   /home/temp_user/Theme/fonts/q*.ofm   /usr/share/fonts/ofm/q/
cp   /home/temp_user/Theme/fonts/r*.ofm   /usr/share/fonts/ofm/r/
cp   /home/temp_user/Theme/fonts/s*.ofm   /usr/share/fonts/ofm/s/
cp   /home/temp_user/Theme/fonts/t*.ofm   /usr/share/fonts/ofm/t/
cp   /home/temp_user/Theme/fonts/u*.ofm   /usr/share/fonts/ofm/u/
cp   /home/temp_user/Theme/fonts/v*.ofm   /usr/share/fonts/ofm/v/
cp   /home/temp_user/Theme/fonts/w*.ofm   /usr/share/fonts/ofm/w/
cp   /home/temp_user/Theme/fonts/x*.ofm   /usr/share/fonts/ofm/x/
cp   /home/temp_user/Theme/fonts/y*.ofm   /usr/share/fonts/ofm/y/
cp   /home/temp_user/Theme/fonts/z*.ofm   /usr/share/fonts/ofm/z/
cp   /home/temp_user/Theme/fonts/0*.ofm   /usr/share/fonts/ofm/0/
cp   /home/temp_user/Theme/fonts/1*.ofm   /usr/share/fonts/ofm/1/
cp   /home/temp_user/Theme/fonts/2*.ofm   /usr/share/fonts/ofm/2/
cp   /home/temp_user/Theme/fonts/3*.ofm   /usr/share/fonts/ofm/3/
cp   /home/temp_user/Theme/fonts/4*.ofm   /usr/share/fonts/ofm/4/
cp   /home/temp_user/Theme/fonts/5*.ofm   /usr/share/fonts/ofm/5/
cp   /home/temp_user/Theme/fonts/6*.ofm   /usr/share/fonts/ofm/6/
cp   /home/temp_user/Theme/fonts/7*.ofm   /usr/share/fonts/ofm/7/
cp   /home/temp_user/Theme/fonts/8*.ofm   /usr/share/fonts/ofm/8/
cp   /home/temp_user/Theme/fonts/9*.ofm   /usr/share/fonts/ofm/9/
cp   /home/temp_user/Theme/fonts/[*.ofm   /usr/share/fonts/ofm/other/

echo OTF
cp   /home/temp_user/Theme/fonts/_*.otf   /usr/share/fonts/otf/other/
cp   /home/temp_user/Theme/fonts/a*.otf   /usr/share/fonts/otf/a/
cp   /home/temp_user/Theme/fonts/b*.otf   /usr/share/fonts/otf/b/
cp   /home/temp_user/Theme/fonts/c*.otf   /usr/share/fonts/otf/c/
cp   /home/temp_user/Theme/fonts/d*.otf   /usr/share/fonts/otf/d/
cp   /home/temp_user/Theme/fonts/e*.otf   /usr/share/fonts/otf/e/
cp   /home/temp_user/Theme/fonts/f*.otf   /usr/share/fonts/otf/f/
cp   /home/temp_user/Theme/fonts/g*.otf   /usr/share/fonts/otf/g/
cp   /home/temp_user/Theme/fonts/h*.otf   /usr/share/fonts/otf/h/
cp   /home/temp_user/Theme/fonts/i*.otf   /usr/share/fonts/otf/i/
cp   /home/temp_user/Theme/fonts/j*.otf   /usr/share/fonts/otf/j/
cp   /home/temp_user/Theme/fonts/k*.otf   /usr/share/fonts/otf/k/
cp   /home/temp_user/Theme/fonts/l*.otf   /usr/share/fonts/otf/l/
cp   /home/temp_user/Theme/fonts/m*.otf   /usr/share/fonts/otf/m/
cp   /home/temp_user/Theme/fonts/n*.otf   /usr/share/fonts/otf/n/
cp   /home/temp_user/Theme/fonts/o*.otf   /usr/share/fonts/otf/o/
cp   /home/temp_user/Theme/fonts/p*.otf   /usr/share/fonts/otf/p/
cp   /home/temp_user/Theme/fonts/q*.otf   /usr/share/fonts/otf/q/
cp   /home/temp_user/Theme/fonts/r*.otf   /usr/share/fonts/otf/r/
cp   /home/temp_user/Theme/fonts/s*.otf   /usr/share/fonts/otf/s/
cp   /home/temp_user/Theme/fonts/t*.otf   /usr/share/fonts/otf/t/
cp   /home/temp_user/Theme/fonts/u*.otf   /usr/share/fonts/otf/u/
cp   /home/temp_user/Theme/fonts/v*.otf   /usr/share/fonts/otf/v/
cp   /home/temp_user/Theme/fonts/w*.otf   /usr/share/fonts/otf/w/
cp   /home/temp_user/Theme/fonts/x*.otf   /usr/share/fonts/otf/x/
cp   /home/temp_user/Theme/fonts/y*.otf   /usr/share/fonts/otf/y/
cp   /home/temp_user/Theme/fonts/z*.otf   /usr/share/fonts/otf/z/
cp   /home/temp_user/Theme/fonts/0*.otf   /usr/share/fonts/otf/0/
cp   /home/temp_user/Theme/fonts/1*.otf   /usr/share/fonts/otf/1/
cp   /home/temp_user/Theme/fonts/2*.otf   /usr/share/fonts/otf/2/
cp   /home/temp_user/Theme/fonts/3*.otf   /usr/share/fonts/otf/3/
cp   /home/temp_user/Theme/fonts/4*.otf   /usr/share/fonts/otf/4/
cp   /home/temp_user/Theme/fonts/5*.otf   /usr/share/fonts/otf/5/
cp   /home/temp_user/Theme/fonts/6*.otf   /usr/share/fonts/otf/6/
cp   /home/temp_user/Theme/fonts/7*.otf   /usr/share/fonts/otf/7/
cp   /home/temp_user/Theme/fonts/8*.otf   /usr/share/fonts/otf/8/
cp   /home/temp_user/Theme/fonts/9*.otf   /usr/share/fonts/otf/9/
cp   /home/temp_user/Theme/fonts/[*.otf   /usr/share/fonts/otf/other/

echo PBM 
cp   /home/temp_user/Theme/fonts/_*.pbm   /usr/share/fonts/pbm/other/
cp   /home/temp_user/Theme/fonts/a*.pbm   /usr/share/fonts/pbm/a/
cp   /home/temp_user/Theme/fonts/b*.pbm   /usr/share/fonts/pbm/b/
cp   /home/temp_user/Theme/fonts/c*.pbm   /usr/share/fonts/pbm/c/
cp   /home/temp_user/Theme/fonts/d*.pbm   /usr/share/fonts/pbm/d/
cp   /home/temp_user/Theme/fonts/e*.pbm   /usr/share/fonts/pbm/e/
cp   /home/temp_user/Theme/fonts/f*.pbm   /usr/share/fonts/pbm/f/
cp   /home/temp_user/Theme/fonts/g*.pbm   /usr/share/fonts/pbm/g/
cp   /home/temp_user/Theme/fonts/h*.pbm   /usr/share/fonts/pbm/h/
cp   /home/temp_user/Theme/fonts/i*.pbm   /usr/share/fonts/pbm/i/
cp   /home/temp_user/Theme/fonts/j*.pbm   /usr/share/fonts/pbm/j/
cp   /home/temp_user/Theme/fonts/k*.pbm   /usr/share/fonts/pbm/k/
cp   /home/temp_user/Theme/fonts/l*.pbm   /usr/share/fonts/pbm/l/
cp   /home/temp_user/Theme/fonts/m*.pbm   /usr/share/fonts/pbm/m/
cp   /home/temp_user/Theme/fonts/n*.pbm   /usr/share/fonts/pbm/n/
cp   /home/temp_user/Theme/fonts/o*.pbm   /usr/share/fonts/pbm/o/
cp   /home/temp_user/Theme/fonts/p*.pbm   /usr/share/fonts/pbm/p/
cp   /home/temp_user/Theme/fonts/q*.pbm   /usr/share/fonts/pbm/q/
cp   /home/temp_user/Theme/fonts/r*.pbm   /usr/share/fonts/pbm/r/
cp   /home/temp_user/Theme/fonts/s*.pbm   /usr/share/fonts/pbm/s/
cp   /home/temp_user/Theme/fonts/t*.pbm   /usr/share/fonts/pbm/t/
cp   /home/temp_user/Theme/fonts/u*.pbm   /usr/share/fonts/pbm/u/
cp   /home/temp_user/Theme/fonts/v*.pbm   /usr/share/fonts/pbm/v/
cp   /home/temp_user/Theme/fonts/w*.pbm   /usr/share/fonts/pbm/w/
cp   /home/temp_user/Theme/fonts/x*.pbm   /usr/share/fonts/pbm/x/
cp   /home/temp_user/Theme/fonts/y*.pbm   /usr/share/fonts/pbm/y/
cp   /home/temp_user/Theme/fonts/z*.pbm   /usr/share/fonts/pbm/z/
cp   /home/temp_user/Theme/fonts/0*.pbm   /usr/share/fonts/pbm/0/
cp   /home/temp_user/Theme/fonts/1*.pbm   /usr/share/fonts/pbm/1/
cp   /home/temp_user/Theme/fonts/2*.pbm   /usr/share/fonts/pbm/2/
cp   /home/temp_user/Theme/fonts/3*.pbm   /usr/share/fonts/pbm/3/
cp   /home/temp_user/Theme/fonts/4*.pbm   /usr/share/fonts/pbm/4/
cp   /home/temp_user/Theme/fonts/5*.pbm   /usr/share/fonts/pbm/5/
cp   /home/temp_user/Theme/fonts/6*.pbm   /usr/share/fonts/pbm/6/
cp   /home/temp_user/Theme/fonts/7*.pbm   /usr/share/fonts/pbm/7/
cp   /home/temp_user/Theme/fonts/8*.pbm   /usr/share/fonts/pbm/8/
cp   /home/temp_user/Theme/fonts/9*.pbm   /usr/share/fonts/pbm/9/
cp   /home/temp_user/Theme/fonts/[*.pbm   /usr/share/fonts/pbm/other/

echo PCF
cp   /home/temp_user/Theme/fonts/_*.pcf   /usr/share/fonts/pcf/other/
cp   /home/temp_user/Theme/fonts/a*.pcf   /usr/share/fonts/pcf/a/
cp   /home/temp_user/Theme/fonts/b*.pcf   /usr/share/fonts/pcf/b/
cp   /home/temp_user/Theme/fonts/c*.pcf   /usr/share/fonts/pcf/c/
cp   /home/temp_user/Theme/fonts/d*.pcf   /usr/share/fonts/pcf/d/
cp   /home/temp_user/Theme/fonts/e*.pcf   /usr/share/fonts/pcf/e/
cp   /home/temp_user/Theme/fonts/f*.pcf   /usr/share/fonts/pcf/f/
cp   /home/temp_user/Theme/fonts/g*.pcf   /usr/share/fonts/pcf/g/
cp   /home/temp_user/Theme/fonts/h*.pcf   /usr/share/fonts/pcf/h/
cp   /home/temp_user/Theme/fonts/i*.pcf   /usr/share/fonts/pcf/i/
cp   /home/temp_user/Theme/fonts/j*.pcf   /usr/share/fonts/pcf/j/
cp   /home/temp_user/Theme/fonts/k*.pcf   /usr/share/fonts/pcf/k/
cp   /home/temp_user/Theme/fonts/l*.pcf   /usr/share/fonts/pcf/l/
cp   /home/temp_user/Theme/fonts/m*.pcf   /usr/share/fonts/pcf/m/
cp   /home/temp_user/Theme/fonts/n*.pcf   /usr/share/fonts/pcf/n/
cp   /home/temp_user/Theme/fonts/o*.pcf   /usr/share/fonts/pcf/o/
cp   /home/temp_user/Theme/fonts/p*.pcf   /usr/share/fonts/pcf/p/
cp   /home/temp_user/Theme/fonts/q*.pcf   /usr/share/fonts/pcf/q/
cp   /home/temp_user/Theme/fonts/r*.pcf   /usr/share/fonts/pcf/r/
cp   /home/temp_user/Theme/fonts/s*.pcf   /usr/share/fonts/pcf/s/
cp   /home/temp_user/Theme/fonts/t*.pcf   /usr/share/fonts/pcf/t/
cp   /home/temp_user/Theme/fonts/u*.pcf   /usr/share/fonts/pcf/u/
cp   /home/temp_user/Theme/fonts/v*.pcf   /usr/share/fonts/pcf/v/
cp   /home/temp_user/Theme/fonts/w*.pcf   /usr/share/fonts/pcf/w/
cp   /home/temp_user/Theme/fonts/x*.pcf   /usr/share/fonts/pcf/x/
cp   /home/temp_user/Theme/fonts/y*.pcf   /usr/share/fonts/pcf/y/
cp   /home/temp_user/Theme/fonts/z*.pcf   /usr/share/fonts/pcf/z/
cp   /home/temp_user/Theme/fonts/0*.pcf   /usr/share/fonts/pcf/0/
cp   /home/temp_user/Theme/fonts/1*.pcf   /usr/share/fonts/pcf/1/
cp   /home/temp_user/Theme/fonts/2*.pcf   /usr/share/fonts/pcf/2/
cp   /home/temp_user/Theme/fonts/3*.pcf   /usr/share/fonts/pcf/3/
cp   /home/temp_user/Theme/fonts/4*.pcf   /usr/share/fonts/pcf/4/
cp   /home/temp_user/Theme/fonts/5*.pcf   /usr/share/fonts/pcf/5/
cp   /home/temp_user/Theme/fonts/6*.pcf   /usr/share/fonts/pcf/6/
cp   /home/temp_user/Theme/fonts/7*.pcf   /usr/share/fonts/pcf/7/
cp   /home/temp_user/Theme/fonts/8*.pcf   /usr/share/fonts/pcf/8/
cp   /home/temp_user/Theme/fonts/9*.pcf   /usr/share/fonts/pcf/9/
cp   /home/temp_user/Theme/fonts/[*.pcf   /usr/share/fonts/pcf/other/

echo PFB
cp   /home/temp_user/Theme/fonts/_*.pfb   /usr/share/fonts/pfb/other/
cp   /home/temp_user/Theme/fonts/a*.pfb   /usr/share/fonts/pfb/a/
cp   /home/temp_user/Theme/fonts/b*.pfb   /usr/share/fonts/pfb/b/
cp   /home/temp_user/Theme/fonts/c*.pfb   /usr/share/fonts/pfb/c/
cp   /home/temp_user/Theme/fonts/d*.pfb   /usr/share/fonts/pfb/d/
cp   /home/temp_user/Theme/fonts/e*.pfb   /usr/share/fonts/pfb/e/
cp   /home/temp_user/Theme/fonts/f*.pfb   /usr/share/fonts/pfb/f/
cp   /home/temp_user/Theme/fonts/g*.pfb   /usr/share/fonts/pfb/g/
cp   /home/temp_user/Theme/fonts/h*.pfb   /usr/share/fonts/pfb/h/
cp   /home/temp_user/Theme/fonts/i*.pfb   /usr/share/fonts/pfb/i/
cp   /home/temp_user/Theme/fonts/j*.pfb   /usr/share/fonts/pfb/j/
cp   /home/temp_user/Theme/fonts/k*.pfb   /usr/share/fonts/pfb/k/
cp   /home/temp_user/Theme/fonts/l*.pfb   /usr/share/fonts/pfb/l/
cp   /home/temp_user/Theme/fonts/m*.pfb   /usr/share/fonts/pfb/m/
cp   /home/temp_user/Theme/fonts/n*.pfb   /usr/share/fonts/pfb/n/
cp   /home/temp_user/Theme/fonts/o*.pfb   /usr/share/fonts/pfb/o/
cp   /home/temp_user/Theme/fonts/p*.pfb   /usr/share/fonts/pfb/p/
cp   /home/temp_user/Theme/fonts/q*.pfb   /usr/share/fonts/pfb/q/
cp   /home/temp_user/Theme/fonts/r*.pfb   /usr/share/fonts/pfb/r/
cp   /home/temp_user/Theme/fonts/s*.pfb   /usr/share/fonts/pfb/s/
cp   /home/temp_user/Theme/fonts/t*.pfb   /usr/share/fonts/pfb/t/
cp   /home/temp_user/Theme/fonts/u*.pfb   /usr/share/fonts/pfb/u/
cp   /home/temp_user/Theme/fonts/v*.pfb   /usr/share/fonts/pfb/v/
cp   /home/temp_user/Theme/fonts/w*.pfb   /usr/share/fonts/pfb/w/
cp   /home/temp_user/Theme/fonts/x*.pfb   /usr/share/fonts/pfb/x/
cp   /home/temp_user/Theme/fonts/y*.pfb   /usr/share/fonts/pfb/y/
cp   /home/temp_user/Theme/fonts/z*.pfb   /usr/share/fonts/pfb/z/
cp   /home/temp_user/Theme/fonts/0*.pfb   /usr/share/fonts/pfb/0/
cp   /home/temp_user/Theme/fonts/1*.pfb   /usr/share/fonts/pfb/1/
cp   /home/temp_user/Theme/fonts/2*.pfb   /usr/share/fonts/pfb/2/
cp   /home/temp_user/Theme/fonts/3*.pfb   /usr/share/fonts/pfb/3/
cp   /home/temp_user/Theme/fonts/4*.pfb   /usr/share/fonts/pfb/4/
cp   /home/temp_user/Theme/fonts/5*.pfb   /usr/share/fonts/pfb/5/
cp   /home/temp_user/Theme/fonts/6*.pfb   /usr/share/fonts/pfb/6/
cp   /home/temp_user/Theme/fonts/7*.pfb   /usr/share/fonts/pfb/7/
cp   /home/temp_user/Theme/fonts/8*.pfb   /usr/share/fonts/pfb/8/
cp   /home/temp_user/Theme/fonts/9*.pfb   /usr/share/fonts/pfb/9/
cp   /home/temp_user/Theme/fonts/[*.pfb   /usr/share/fonts/pfb/other/

echo PFT
cp   /home/temp_user/Theme/fonts/_*.pft   /usr/share/fonts/pft/other/
cp   /home/temp_user/Theme/fonts/a*.pft   /usr/share/fonts/pft/a/
cp   /home/temp_user/Theme/fonts/b*.pft   /usr/share/fonts/pft/b/
cp   /home/temp_user/Theme/fonts/c*.pft   /usr/share/fonts/pft/c/
cp   /home/temp_user/Theme/fonts/d*.pft   /usr/share/fonts/pft/d/
cp   /home/temp_user/Theme/fonts/e*.pft   /usr/share/fonts/pft/e/
cp   /home/temp_user/Theme/fonts/f*.pft   /usr/share/fonts/pft/f/
cp   /home/temp_user/Theme/fonts/g*.pft   /usr/share/fonts/pft/g/
cp   /home/temp_user/Theme/fonts/h*.pft   /usr/share/fonts/pft/h/
cp   /home/temp_user/Theme/fonts/i*.pft   /usr/share/fonts/pft/i/
cp   /home/temp_user/Theme/fonts/j*.pft   /usr/share/fonts/pft/j/
cp   /home/temp_user/Theme/fonts/k*.pft   /usr/share/fonts/pft/k/
cp   /home/temp_user/Theme/fonts/l*.pft   /usr/share/fonts/pft/l/
cp   /home/temp_user/Theme/fonts/m*.pft   /usr/share/fonts/pft/m/
cp   /home/temp_user/Theme/fonts/n*.pft   /usr/share/fonts/pft/n/
cp   /home/temp_user/Theme/fonts/o*.pft   /usr/share/fonts/pft/o/
cp   /home/temp_user/Theme/fonts/p*.pft   /usr/share/fonts/pft/p/
cp   /home/temp_user/Theme/fonts/q*.pft   /usr/share/fonts/pft/q/
cp   /home/temp_user/Theme/fonts/r*.pft   /usr/share/fonts/pft/r/
cp   /home/temp_user/Theme/fonts/s*.pft   /usr/share/fonts/pft/s/
cp   /home/temp_user/Theme/fonts/t*.pft   /usr/share/fonts/pft/t/
cp   /home/temp_user/Theme/fonts/u*.pft   /usr/share/fonts/pft/u/
cp   /home/temp_user/Theme/fonts/v*.pft   /usr/share/fonts/pft/v/
cp   /home/temp_user/Theme/fonts/w*.pft   /usr/share/fonts/pft/w/
cp   /home/temp_user/Theme/fonts/x*.pft   /usr/share/fonts/pft/x/
cp   /home/temp_user/Theme/fonts/y*.pft   /usr/share/fonts/pft/y/
cp   /home/temp_user/Theme/fonts/z*.pft   /usr/share/fonts/pft/z/
cp   /home/temp_user/Theme/fonts/0*.pft   /usr/share/fonts/pft/0/
cp   /home/temp_user/Theme/fonts/1*.pft   /usr/share/fonts/pft/1/
cp   /home/temp_user/Theme/fonts/2*.pft   /usr/share/fonts/pft/2/
cp   /home/temp_user/Theme/fonts/3*.pft   /usr/share/fonts/pft/3/
cp   /home/temp_user/Theme/fonts/4*.pft   /usr/share/fonts/pft/4/
cp   /home/temp_user/Theme/fonts/5*.pft   /usr/share/fonts/pft/5/
cp   /home/temp_user/Theme/fonts/6*.pft   /usr/share/fonts/pft/6/
cp   /home/temp_user/Theme/fonts/7*.pft   /usr/share/fonts/pft/7/
cp   /home/temp_user/Theme/fonts/8*.pft   /usr/share/fonts/pft/8/
cp   /home/temp_user/Theme/fonts/9*.pft   /usr/share/fonts/pft/9/
cp   /home/temp_user/Theme/fonts/[*.pft   /usr/share/fonts/pft/other/

echo PSF
cp   /home/temp_user/Theme/fonts/_*.psf   /usr/share/fonts/psf/other/
cp   /home/temp_user/Theme/fonts/a*.psf   /usr/share/fonts/psf/a/
cp   /home/temp_user/Theme/fonts/b*.psf   /usr/share/fonts/psf/b/
cp   /home/temp_user/Theme/fonts/c*.psf   /usr/share/fonts/psf/c/
cp   /home/temp_user/Theme/fonts/d*.psf   /usr/share/fonts/psf/d/
cp   /home/temp_user/Theme/fonts/e*.psf   /usr/share/fonts/psf/e/
cp   /home/temp_user/Theme/fonts/f*.psf   /usr/share/fonts/psf/f/
cp   /home/temp_user/Theme/fonts/g*.psf   /usr/share/fonts/psf/g/
cp   /home/temp_user/Theme/fonts/h*.psf   /usr/share/fonts/psf/h/
cp   /home/temp_user/Theme/fonts/i*.psf   /usr/share/fonts/psf/i/
cp   /home/temp_user/Theme/fonts/j*.psf   /usr/share/fonts/psf/j/
cp   /home/temp_user/Theme/fonts/k*.psf   /usr/share/fonts/psf/k/
cp   /home/temp_user/Theme/fonts/l*.psf   /usr/share/fonts/psf/l/
cp   /home/temp_user/Theme/fonts/m*.psf   /usr/share/fonts/psf/m/
cp   /home/temp_user/Theme/fonts/n*.psf   /usr/share/fonts/psf/n/
cp   /home/temp_user/Theme/fonts/o*.psf   /usr/share/fonts/psf/o/
cp   /home/temp_user/Theme/fonts/p*.psf   /usr/share/fonts/psf/p/
cp   /home/temp_user/Theme/fonts/q*.psf   /usr/share/fonts/psf/q/
cp   /home/temp_user/Theme/fonts/r*.psf   /usr/share/fonts/psf/r/
cp   /home/temp_user/Theme/fonts/s*.psf   /usr/share/fonts/psf/s/
cp   /home/temp_user/Theme/fonts/t*.psf   /usr/share/fonts/psf/t/
cp   /home/temp_user/Theme/fonts/u*.psf   /usr/share/fonts/psf/u/
cp   /home/temp_user/Theme/fonts/v*.psf   /usr/share/fonts/psf/v/
cp   /home/temp_user/Theme/fonts/w*.psf   /usr/share/fonts/psf/w/
cp   /home/temp_user/Theme/fonts/x*.psf   /usr/share/fonts/psf/x/
cp   /home/temp_user/Theme/fonts/y*.psf   /usr/share/fonts/psf/y/
cp   /home/temp_user/Theme/fonts/z*.psf   /usr/share/fonts/psf/z/
cp   /home/temp_user/Theme/fonts/0*.psf   /usr/share/fonts/psf/0/
cp   /home/temp_user/Theme/fonts/1*.psf   /usr/share/fonts/psf/1/
cp   /home/temp_user/Theme/fonts/2*.psf   /usr/share/fonts/psf/2/
cp   /home/temp_user/Theme/fonts/3*.psf   /usr/share/fonts/psf/3/
cp   /home/temp_user/Theme/fonts/4*.psf   /usr/share/fonts/psf/4/
cp   /home/temp_user/Theme/fonts/5*.psf   /usr/share/fonts/psf/5/
cp   /home/temp_user/Theme/fonts/6*.psf   /usr/share/fonts/psf/6/
cp   /home/temp_user/Theme/fonts/7*.psf   /usr/share/fonts/psf/7/
cp   /home/temp_user/Theme/fonts/8*.psf   /usr/share/fonts/psf/8/
cp   /home/temp_user/Theme/fonts/9*.psf   /usr/share/fonts/psf/9/
cp   /home/temp_user/Theme/fonts/[*.psf   /usr/share/fonts/psf/other/

echo SCR 
cp   /home/temp_user/Theme/fonts/_*.scr   /usr/share/fonts/scr/other/
cp   /home/temp_user/Theme/fonts/a*.scr   /usr/share/fonts/scr/a/
cp   /home/temp_user/Theme/fonts/b*.scr   /usr/share/fonts/scr/b/
cp   /home/temp_user/Theme/fonts/c*.scr   /usr/share/fonts/scr/c/
cp   /home/temp_user/Theme/fonts/d*.scr   /usr/share/fonts/scr/d/
cp   /home/temp_user/Theme/fonts/e*.scr   /usr/share/fonts/scr/e/
cp   /home/temp_user/Theme/fonts/f*.scr   /usr/share/fonts/scr/f/
cp   /home/temp_user/Theme/fonts/g*.scr   /usr/share/fonts/scr/g/
cp   /home/temp_user/Theme/fonts/h*.scr   /usr/share/fonts/scr/h/
cp   /home/temp_user/Theme/fonts/i*.scr   /usr/share/fonts/scr/i/
cp   /home/temp_user/Theme/fonts/j*.scr   /usr/share/fonts/scr/j/
cp   /home/temp_user/Theme/fonts/k*.scr   /usr/share/fonts/scr/k/
cp   /home/temp_user/Theme/fonts/l*.scr   /usr/share/fonts/scr/l/
cp   /home/temp_user/Theme/fonts/m*.scr   /usr/share/fonts/scr/m/
cp   /home/temp_user/Theme/fonts/n*.scr   /usr/share/fonts/scr/n/
cp   /home/temp_user/Theme/fonts/o*.scr   /usr/share/fonts/scr/o/
cp   /home/temp_user/Theme/fonts/p*.scr   /usr/share/fonts/scr/p/
cp   /home/temp_user/Theme/fonts/q*.scr   /usr/share/fonts/scr/q/
cp   /home/temp_user/Theme/fonts/r*.scr   /usr/share/fonts/scr/r/
cp   /home/temp_user/Theme/fonts/s*.scr   /usr/share/fonts/scr/s/
cp   /home/temp_user/Theme/fonts/t*.scr   /usr/share/fonts/scr/t/
cp   /home/temp_user/Theme/fonts/u*.scr   /usr/share/fonts/scr/u/
cp   /home/temp_user/Theme/fonts/v*.scr   /usr/share/fonts/scr/v/
cp   /home/temp_user/Theme/fonts/w*.scr   /usr/share/fonts/scr/w/
cp   /home/temp_user/Theme/fonts/x*.scr   /usr/share/fonts/scr/x/
cp   /home/temp_user/Theme/fonts/y*.scr   /usr/share/fonts/scr/y/
cp   /home/temp_user/Theme/fonts/z*.scr   /usr/share/fonts/scr/z/
cp   /home/temp_user/Theme/fonts/0*.scr   /usr/share/fonts/scr/0/
cp   /home/temp_user/Theme/fonts/1*.scr   /usr/share/fonts/scr/1/
cp   /home/temp_user/Theme/fonts/2*.scr   /usr/share/fonts/scr/2/
cp   /home/temp_user/Theme/fonts/3*.scr   /usr/share/fonts/scr/3/
cp   /home/temp_user/Theme/fonts/4*.scr   /usr/share/fonts/scr/4/
cp   /home/temp_user/Theme/fonts/5*.scr   /usr/share/fonts/scr/5/
cp   /home/temp_user/Theme/fonts/6*.scr   /usr/share/fonts/scr/6/
cp   /home/temp_user/Theme/fonts/7*.scr   /usr/share/fonts/scr/7/
cp   /home/temp_user/Theme/fonts/8*.scr   /usr/share/fonts/scr/8/
cp   /home/temp_user/Theme/fonts/9*.scr   /usr/share/fonts/scr/9/
cp   /home/temp_user/Theme/fonts/[*.scr   /usr/share/fonts/scr/other/

echo SFD
cp   /home/temp_user/Theme/fonts/_*.sfd   /usr/share/fonts/sfd/other/
cp   /home/temp_user/Theme/fonts/a*.sfd   /usr/share/fonts/sfd/a/
cp   /home/temp_user/Theme/fonts/b*.sfd   /usr/share/fonts/sfd/b/
cp   /home/temp_user/Theme/fonts/c*.sfd   /usr/share/fonts/sfd/c/
cp   /home/temp_user/Theme/fonts/d*.sfd   /usr/share/fonts/sfd/d/
cp   /home/temp_user/Theme/fonts/e*.sfd   /usr/share/fonts/sfd/e/
cp   /home/temp_user/Theme/fonts/f*.sfd   /usr/share/fonts/sfd/f/
cp   /home/temp_user/Theme/fonts/g*.sfd   /usr/share/fonts/sfd/g/
cp   /home/temp_user/Theme/fonts/h*.sfd   /usr/share/fonts/sfd/h/
cp   /home/temp_user/Theme/fonts/i*.sfd   /usr/share/fonts/sfd/i/
cp   /home/temp_user/Theme/fonts/j*.sfd   /usr/share/fonts/sfd/j/
cp   /home/temp_user/Theme/fonts/k*.sfd   /usr/share/fonts/sfd/k/
cp   /home/temp_user/Theme/fonts/l*.sfd   /usr/share/fonts/sfd/l/
cp   /home/temp_user/Theme/fonts/m*.sfd   /usr/share/fonts/sfd/m/
cp   /home/temp_user/Theme/fonts/n*.sfd   /usr/share/fonts/sfd/n/
cp   /home/temp_user/Theme/fonts/o*.sfd   /usr/share/fonts/sfd/o/
cp   /home/temp_user/Theme/fonts/p*.sfd   /usr/share/fonts/sfd/p/
cp   /home/temp_user/Theme/fonts/q*.sfd   /usr/share/fonts/sfd/q/
cp   /home/temp_user/Theme/fonts/r*.sfd   /usr/share/fonts/sfd/r/
cp   /home/temp_user/Theme/fonts/s*.sfd   /usr/share/fonts/sfd/s/
cp   /home/temp_user/Theme/fonts/t*.sfd   /usr/share/fonts/sfd/t/
cp   /home/temp_user/Theme/fonts/u*.sfd   /usr/share/fonts/sfd/u/
cp   /home/temp_user/Theme/fonts/v*.sfd   /usr/share/fonts/sfd/v/
cp   /home/temp_user/Theme/fonts/w*.sfd   /usr/share/fonts/sfd/w/
cp   /home/temp_user/Theme/fonts/x*.sfd   /usr/share/fonts/sfd/x/
cp   /home/temp_user/Theme/fonts/y*.sfd   /usr/share/fonts/sfd/y/
cp   /home/temp_user/Theme/fonts/z*.sfd   /usr/share/fonts/sfd/z/
cp   /home/temp_user/Theme/fonts/0*.sfd   /usr/share/fonts/sfd/0/
cp   /home/temp_user/Theme/fonts/1*.sfd   /usr/share/fonts/sfd/1/
cp   /home/temp_user/Theme/fonts/2*.sfd   /usr/share/fonts/sfd/2/
cp   /home/temp_user/Theme/fonts/3*.sfd   /usr/share/fonts/sfd/3/
cp   /home/temp_user/Theme/fonts/4*.sfd   /usr/share/fonts/sfd/4/
cp   /home/temp_user/Theme/fonts/5*.sfd   /usr/share/fonts/sfd/5/
cp   /home/temp_user/Theme/fonts/6*.sfd   /usr/share/fonts/sfd/6/
cp   /home/temp_user/Theme/fonts/7*.sfd   /usr/share/fonts/sfd/7/
cp   /home/temp_user/Theme/fonts/8*.sfd   /usr/share/fonts/sfd/8/
cp   /home/temp_user/Theme/fonts/9*.sfd   /usr/share/fonts/sfd/9/
cp   /home/temp_user/Theme/fonts/[*.sfd   /usr/share/fonts/sfd/other/

echo SFI
cp   /home/temp_user/Theme/fonts/_*.sfi   /usr/share/fonts/sfi/other/
cp   /home/temp_user/Theme/fonts/a*.sfi   /usr/share/fonts/sfi/a/
cp   /home/temp_user/Theme/fonts/b*.sfi   /usr/share/fonts/sfi/b/
cp   /home/temp_user/Theme/fonts/c*.sfi   /usr/share/fonts/sfi/c/
cp   /home/temp_user/Theme/fonts/d*.sfi   /usr/share/fonts/sfi/d/
cp   /home/temp_user/Theme/fonts/e*.sfi   /usr/share/fonts/sfi/e/
cp   /home/temp_user/Theme/fonts/f*.sfi   /usr/share/fonts/sfi/f/
cp   /home/temp_user/Theme/fonts/g*.sfi   /usr/share/fonts/sfi/g/
cp   /home/temp_user/Theme/fonts/h*.sfi   /usr/share/fonts/sfi/h/
cp   /home/temp_user/Theme/fonts/i*.sfi   /usr/share/fonts/sfi/i/
cp   /home/temp_user/Theme/fonts/j*.sfi   /usr/share/fonts/sfi/j/
cp   /home/temp_user/Theme/fonts/k*.sfi   /usr/share/fonts/sfi/k/
cp   /home/temp_user/Theme/fonts/l*.sfi   /usr/share/fonts/sfi/l/
cp   /home/temp_user/Theme/fonts/m*.sfi   /usr/share/fonts/sfi/m/
cp   /home/temp_user/Theme/fonts/n*.sfi   /usr/share/fonts/sfi/n/
cp   /home/temp_user/Theme/fonts/o*.sfi   /usr/share/fonts/sfi/o/
cp   /home/temp_user/Theme/fonts/p*.sfi   /usr/share/fonts/sfi/p/
cp   /home/temp_user/Theme/fonts/q*.sfi   /usr/share/fonts/sfi/q/
cp   /home/temp_user/Theme/fonts/r*.sfi   /usr/share/fonts/sfi/r/
cp   /home/temp_user/Theme/fonts/s*.sfi   /usr/share/fonts/sfi/s/
cp   /home/temp_user/Theme/fonts/t*.sfi   /usr/share/fonts/sfi/t/
cp   /home/temp_user/Theme/fonts/u*.sfi   /usr/share/fonts/sfi/u/
cp   /home/temp_user/Theme/fonts/v*.sfi   /usr/share/fonts/sfi/v/
cp   /home/temp_user/Theme/fonts/w*.sfi   /usr/share/fonts/sfi/w/
cp   /home/temp_user/Theme/fonts/x*.sfi   /usr/share/fonts/sfi/x/
cp   /home/temp_user/Theme/fonts/y*.sfi   /usr/share/fonts/sfi/y/
cp   /home/temp_user/Theme/fonts/z*.sfi   /usr/share/fonts/sfi/z/
cp   /home/temp_user/Theme/fonts/0*.sfi   /usr/share/fonts/sfi/0/
cp   /home/temp_user/Theme/fonts/1*.sfi   /usr/share/fonts/sfi/1/
cp   /home/temp_user/Theme/fonts/2*.sfi   /usr/share/fonts/sfi/2/
cp   /home/temp_user/Theme/fonts/3*.sfi   /usr/share/fonts/sfi/3/
cp   /home/temp_user/Theme/fonts/4*.sfi   /usr/share/fonts/sfi/4/
cp   /home/temp_user/Theme/fonts/5*.sfi   /usr/share/fonts/sfi/5/
cp   /home/temp_user/Theme/fonts/6*.sfi   /usr/share/fonts/sfi/6/
cp   /home/temp_user/Theme/fonts/7*.sfi   /usr/share/fonts/sfi/7/
cp   /home/temp_user/Theme/fonts/8*.sfi   /usr/share/fonts/sfi/8/
cp   /home/temp_user/Theme/fonts/9*.sfi   /usr/share/fonts/sfi/9/
cp   /home/temp_user/Theme/fonts/[*.sfi   /usr/share/fonts/sfi/other/

echo SFL
cp   /home/temp_user/Theme/fonts/_*.sfl   /usr/share/fonts/sfl/other/
cp   /home/temp_user/Theme/fonts/a*.sfl   /usr/share/fonts/sfl/a/
cp   /home/temp_user/Theme/fonts/b*.sfl   /usr/share/fonts/sfl/b/
cp   /home/temp_user/Theme/fonts/c*.sfl   /usr/share/fonts/sfl/c/
cp   /home/temp_user/Theme/fonts/d*.sfl   /usr/share/fonts/sfl/d/
cp   /home/temp_user/Theme/fonts/e*.sfl   /usr/share/fonts/sfl/e/
cp   /home/temp_user/Theme/fonts/f*.sfl   /usr/share/fonts/sfl/f/
cp   /home/temp_user/Theme/fonts/g*.sfl   /usr/share/fonts/sfl/g/
cp   /home/temp_user/Theme/fonts/h*.sfl   /usr/share/fonts/sfl/h/
cp   /home/temp_user/Theme/fonts/i*.sfl   /usr/share/fonts/sfl/i/
cp   /home/temp_user/Theme/fonts/j*.sfl   /usr/share/fonts/sfl/j/
cp   /home/temp_user/Theme/fonts/k*.sfl   /usr/share/fonts/sfl/k/
cp   /home/temp_user/Theme/fonts/l*.sfl   /usr/share/fonts/sfl/l/
cp   /home/temp_user/Theme/fonts/m*.sfl   /usr/share/fonts/sfl/m/
cp   /home/temp_user/Theme/fonts/n*.sfl   /usr/share/fonts/sfl/n/
cp   /home/temp_user/Theme/fonts/o*.sfl   /usr/share/fonts/sfl/o/
cp   /home/temp_user/Theme/fonts/p*.sfl   /usr/share/fonts/sfl/p/
cp   /home/temp_user/Theme/fonts/q*.sfl   /usr/share/fonts/sfl/q/
cp   /home/temp_user/Theme/fonts/r*.sfl   /usr/share/fonts/sfl/r/
cp   /home/temp_user/Theme/fonts/s*.sfl   /usr/share/fonts/sfl/s/
cp   /home/temp_user/Theme/fonts/t*.sfl   /usr/share/fonts/sfl/t/
cp   /home/temp_user/Theme/fonts/u*.sfl   /usr/share/fonts/sfl/u/
cp   /home/temp_user/Theme/fonts/v*.sfl   /usr/share/fonts/sfl/v/
cp   /home/temp_user/Theme/fonts/w*.sfl   /usr/share/fonts/sfl/w/
cp   /home/temp_user/Theme/fonts/x*.sfl   /usr/share/fonts/sfl/x/
cp   /home/temp_user/Theme/fonts/y*.sfl   /usr/share/fonts/sfl/y/
cp   /home/temp_user/Theme/fonts/z*.sfl   /usr/share/fonts/sfl/z/
cp   /home/temp_user/Theme/fonts/0*.sfl   /usr/share/fonts/sfl/0/
cp   /home/temp_user/Theme/fonts/1*.sfl   /usr/share/fonts/sfl/1/
cp   /home/temp_user/Theme/fonts/2*.sfl   /usr/share/fonts/sfl/2/
cp   /home/temp_user/Theme/fonts/3*.sfl   /usr/share/fonts/sfl/3/
cp   /home/temp_user/Theme/fonts/4*.sfl   /usr/share/fonts/sfl/4/
cp   /home/temp_user/Theme/fonts/5*.sfl   /usr/share/fonts/sfl/5/
cp   /home/temp_user/Theme/fonts/6*.sfl   /usr/share/fonts/sfl/6/
cp   /home/temp_user/Theme/fonts/7*.sfl   /usr/share/fonts/sfl/7/
cp   /home/temp_user/Theme/fonts/8*.sfl   /usr/share/fonts/sfl/8/
cp   /home/temp_user/Theme/fonts/9*.sfl   /usr/share/fonts/sfl/9/
cp   /home/temp_user/Theme/fonts/[*.sfl   /usr/share/fonts/sfl/other/

echo SNF
cp   /home/temp_user/Theme/fonts/_*.snf   /usr/share/fonts/snf/other/
cp   /home/temp_user/Theme/fonts/a*.snf   /usr/share/fonts/snf/a/
cp   /home/temp_user/Theme/fonts/b*.snf   /usr/share/fonts/snf/b/
cp   /home/temp_user/Theme/fonts/c*.snf   /usr/share/fonts/snf/c/
cp   /home/temp_user/Theme/fonts/d*.snf   /usr/share/fonts/snf/d/
cp   /home/temp_user/Theme/fonts/e*.snf   /usr/share/fonts/snf/e/
cp   /home/temp_user/Theme/fonts/f*.snf   /usr/share/fonts/snf/f/
cp   /home/temp_user/Theme/fonts/g*.snf   /usr/share/fonts/snf/g/
cp   /home/temp_user/Theme/fonts/h*.snf   /usr/share/fonts/snf/h/
cp   /home/temp_user/Theme/fonts/i*.snf   /usr/share/fonts/snf/i/
cp   /home/temp_user/Theme/fonts/j*.snf   /usr/share/fonts/snf/j/
cp   /home/temp_user/Theme/fonts/k*.snf   /usr/share/fonts/snf/k/
cp   /home/temp_user/Theme/fonts/l*.snf   /usr/share/fonts/snf/l/
cp   /home/temp_user/Theme/fonts/m*.snf   /usr/share/fonts/snf/m/
cp   /home/temp_user/Theme/fonts/n*.snf   /usr/share/fonts/snf/n/
cp   /home/temp_user/Theme/fonts/o*.snf   /usr/share/fonts/snf/o/
cp   /home/temp_user/Theme/fonts/p*.snf   /usr/share/fonts/snf/p/
cp   /home/temp_user/Theme/fonts/q*.snf   /usr/share/fonts/snf/q/
cp   /home/temp_user/Theme/fonts/r*.snf   /usr/share/fonts/snf/r/
cp   /home/temp_user/Theme/fonts/s*.snf   /usr/share/fonts/snf/s/
cp   /home/temp_user/Theme/fonts/t*.snf   /usr/share/fonts/snf/t/
cp   /home/temp_user/Theme/fonts/u*.snf   /usr/share/fonts/snf/u/
cp   /home/temp_user/Theme/fonts/v*.snf   /usr/share/fonts/snf/v/
cp   /home/temp_user/Theme/fonts/w*.snf   /usr/share/fonts/snf/w/
cp   /home/temp_user/Theme/fonts/x*.snf   /usr/share/fonts/snf/x/
cp   /home/temp_user/Theme/fonts/y*.snf   /usr/share/fonts/snf/y/
cp   /home/temp_user/Theme/fonts/z*.snf   /usr/share/fonts/snf/z/
cp   /home/temp_user/Theme/fonts/0*.snf   /usr/share/fonts/snf/0/
cp   /home/temp_user/Theme/fonts/1*.snf   /usr/share/fonts/snf/1/
cp   /home/temp_user/Theme/fonts/2*.snf   /usr/share/fonts/snf/2/
cp   /home/temp_user/Theme/fonts/3*.snf   /usr/share/fonts/snf/3/
cp   /home/temp_user/Theme/fonts/4*.snf   /usr/share/fonts/snf/4/
cp   /home/temp_user/Theme/fonts/5*.snf   /usr/share/fonts/snf/5/
cp   /home/temp_user/Theme/fonts/6*.snf   /usr/share/fonts/snf/6/
cp   /home/temp_user/Theme/fonts/7*.snf   /usr/share/fonts/snf/7/
cp   /home/temp_user/Theme/fonts/8*.snf   /usr/share/fonts/snf/8/
cp   /home/temp_user/Theme/fonts/9*.snf   /usr/share/fonts/snf/9/
cp   /home/temp_user/Theme/fonts/[*.snf   /usr/share/fonts/snf/other/

echo SPD
cp   /home/temp_user/Theme/fonts/_*.spd   /usr/share/fonts/spd/other/
cp   /home/temp_user/Theme/fonts/a*.spd   /usr/share/fonts/spd/a/
cp   /home/temp_user/Theme/fonts/b*.spd   /usr/share/fonts/spd/b/
cp   /home/temp_user/Theme/fonts/c*.spd   /usr/share/fonts/spd/c/
cp   /home/temp_user/Theme/fonts/d*.spd   /usr/share/fonts/spd/d/
cp   /home/temp_user/Theme/fonts/e*.spd   /usr/share/fonts/spd/e/
cp   /home/temp_user/Theme/fonts/f*.spd   /usr/share/fonts/spd/f/
cp   /home/temp_user/Theme/fonts/g*.spd   /usr/share/fonts/spd/g/
cp   /home/temp_user/Theme/fonts/h*.spd   /usr/share/fonts/spd/h/
cp   /home/temp_user/Theme/fonts/i*.spd   /usr/share/fonts/spd/i/
cp   /home/temp_user/Theme/fonts/j*.spd   /usr/share/fonts/spd/j/
cp   /home/temp_user/Theme/fonts/k*.spd   /usr/share/fonts/spd/k/
cp   /home/temp_user/Theme/fonts/l*.spd   /usr/share/fonts/spd/l/
cp   /home/temp_user/Theme/fonts/m*.spd   /usr/share/fonts/spd/m/
cp   /home/temp_user/Theme/fonts/n*.spd   /usr/share/fonts/spd/n/
cp   /home/temp_user/Theme/fonts/o*.spd   /usr/share/fonts/spd/o/
cp   /home/temp_user/Theme/fonts/p*.spd   /usr/share/fonts/spd/p/
cp   /home/temp_user/Theme/fonts/q*.spd   /usr/share/fonts/spd/q/
cp   /home/temp_user/Theme/fonts/r*.spd   /usr/share/fonts/spd/r/
cp   /home/temp_user/Theme/fonts/s*.spd   /usr/share/fonts/spd/s/
cp   /home/temp_user/Theme/fonts/t*.spd   /usr/share/fonts/spd/t/
cp   /home/temp_user/Theme/fonts/u*.spd   /usr/share/fonts/spd/u/
cp   /home/temp_user/Theme/fonts/v*.spd   /usr/share/fonts/spd/v/
cp   /home/temp_user/Theme/fonts/w*.spd   /usr/share/fonts/spd/w/
cp   /home/temp_user/Theme/fonts/x*.spd   /usr/share/fonts/spd/x/
cp   /home/temp_user/Theme/fonts/y*.spd   /usr/share/fonts/spd/y/
cp   /home/temp_user/Theme/fonts/z*.spd   /usr/share/fonts/spd/z/
cp   /home/temp_user/Theme/fonts/0*.spd   /usr/share/fonts/spd/0/
cp   /home/temp_user/Theme/fonts/1*.spd   /usr/share/fonts/spd/1/
cp   /home/temp_user/Theme/fonts/2*.spd   /usr/share/fonts/spd/2/
cp   /home/temp_user/Theme/fonts/3*.spd   /usr/share/fonts/spd/3/
cp   /home/temp_user/Theme/fonts/4*.spd   /usr/share/fonts/spd/4/
cp   /home/temp_user/Theme/fonts/5*.spd   /usr/share/fonts/spd/5/
cp   /home/temp_user/Theme/fonts/6*.spd   /usr/share/fonts/spd/6/
cp   /home/temp_user/Theme/fonts/7*.spd   /usr/share/fonts/spd/7/
cp   /home/temp_user/Theme/fonts/8*.spd   /usr/share/fonts/spd/8/
cp   /home/temp_user/Theme/fonts/9*.spd   /usr/share/fonts/spd/9/
cp   /home/temp_user/Theme/fonts/[*.spd   /usr/share/fonts/spd/other/

echo t2

cp   /home/temp_user/Theme/fonts/a*.t2   /usr/share/fonts/t2/a/
cp   /home/temp_user/Theme/fonts/b*.t2   /usr/share/fonts/t2/b/
cp   /home/temp_user/Theme/fonts/c*.t2   /usr/share/fonts/t2/c/
cp   /home/temp_user/Theme/fonts/d*.t2   /usr/share/fonts/t2/d/
cp   /home/temp_user/Theme/fonts/e*.t2   /usr/share/fonts/t2/e/
cp   /home/temp_user/Theme/fonts/f*.t2   /usr/share/fonts/t2/f/
cp   /home/temp_user/Theme/fonts/g*.t2   /usr/share/fonts/t2/g/
cp   /home/temp_user/Theme/fonts/h*.t2   /usr/share/fonts/t2/h/
cp   /home/temp_user/Theme/fonts/i*.t2   /usr/share/fonts/t2/i/
cp   /home/temp_user/Theme/fonts/j*.t2   /usr/share/fonts/t2/j/
cp   /home/temp_user/Theme/fonts/k*.t2   /usr/share/fonts/t2/k/
cp   /home/temp_user/Theme/fonts/l*.t2   /usr/share/fonts/t2/l/
cp   /home/temp_user/Theme/fonts/m*.t2   /usr/share/fonts/t2/m/
cp   /home/temp_user/Theme/fonts/n*.t2   /usr/share/fonts/t2/n/
cp   /home/temp_user/Theme/fonts/o*.t2   /usr/share/fonts/t2/o/
cp   /home/temp_user/Theme/fonts/p*.t2   /usr/share/fonts/t2/p/
cp   /home/temp_user/Theme/fonts/q*.t2   /usr/share/fonts/t2/q/
cp   /home/temp_user/Theme/fonts/r*.t2   /usr/share/fonts/t2/r/
cp   /home/temp_user/Theme/fonts/s*.t2   /usr/share/fonts/t2/s/
cp   /home/temp_user/Theme/fonts/t*.t2   /usr/share/fonts/t2/t/
cp   /home/temp_user/Theme/fonts/u*.t2   /usr/share/fonts/t2/u/
cp   /home/temp_user/Theme/fonts/v*.t2   /usr/share/fonts/t2/v/
cp   /home/temp_user/Theme/fonts/w*.t2   /usr/share/fonts/t2/w/
cp   /home/temp_user/Theme/fonts/x*.t2   /usr/share/fonts/t2/x/
cp   /home/temp_user/Theme/fonts/y*.t2   /usr/share/fonts/t2/y/
cp   /home/temp_user/Theme/fonts/z*.t2   /usr/share/fonts/t2/z/
cp   /home/temp_user/Theme/fonts/0*.t2   /usr/share/fonts/t2/0/
cp   /home/temp_user/Theme/fonts/1*.t2   /usr/share/fonts/t2/1/
cp   /home/temp_user/Theme/fonts/2*.t2   /usr/share/fonts/t2/2/
cp   /home/temp_user/Theme/fonts/3*.t2   /usr/share/fonts/t2/3/
cp   /home/temp_user/Theme/fonts/4*.t2   /usr/share/fonts/t2/4/
cp   /home/temp_user/Theme/fonts/5*.t2   /usr/share/fonts/t2/5/
cp   /home/temp_user/Theme/fonts/6*.t2   /usr/share/fonts/t2/6/
cp   /home/temp_user/Theme/fonts/7*.t2   /usr/share/fonts/t2/7/
cp   /home/temp_user/Theme/fonts/8*.t2   /usr/share/fonts/t2/8/
cp   /home/temp_user/Theme/fonts/9*.t2   /usr/share/fonts/t2/9/
cp   /home/temp_user/Theme/fonts/[*.t2   /usr/share/fonts/t2/other/

echo TTC
cp   /home/temp_user/Theme/fonts/_*.ttc   /usr/share/fonts/ttc/other/
cp   /home/temp_user/Theme/fonts/a*.ttc   /usr/share/fonts/ttc/a/
cp   /home/temp_user/Theme/fonts/b*.ttc   /usr/share/fonts/ttc/b/
cp   /home/temp_user/Theme/fonts/c*.ttc   /usr/share/fonts/ttc/c/
cp   /home/temp_user/Theme/fonts/d*.ttc   /usr/share/fonts/ttc/d/
cp   /home/temp_user/Theme/fonts/e*.ttc   /usr/share/fonts/ttc/e/
cp   /home/temp_user/Theme/fonts/f*.ttc   /usr/share/fonts/ttc/f/
cp   /home/temp_user/Theme/fonts/g*.ttc   /usr/share/fonts/ttc/g/
cp   /home/temp_user/Theme/fonts/h*.ttc   /usr/share/fonts/ttc/h/
cp   /home/temp_user/Theme/fonts/i*.ttc   /usr/share/fonts/ttc/i/
cp   /home/temp_user/Theme/fonts/j*.ttc   /usr/share/fonts/ttc/j/
cp   /home/temp_user/Theme/fonts/k*.ttc   /usr/share/fonts/ttc/k/
cp   /home/temp_user/Theme/fonts/l*.ttc   /usr/share/fonts/ttc/l/
cp   /home/temp_user/Theme/fonts/m*.ttc   /usr/share/fonts/ttc/m/
cp   /home/temp_user/Theme/fonts/n*.ttc   /usr/share/fonts/ttc/n/
cp   /home/temp_user/Theme/fonts/o*.ttc   /usr/share/fonts/ttc/o/
cp   /home/temp_user/Theme/fonts/p*.ttc   /usr/share/fonts/ttc/p/
cp   /home/temp_user/Theme/fonts/q*.ttc   /usr/share/fonts/ttc/q/
cp   /home/temp_user/Theme/fonts/r*.ttc   /usr/share/fonts/ttc/r/
cp   /home/temp_user/Theme/fonts/s*.ttc   /usr/share/fonts/ttc/s/
cp   /home/temp_user/Theme/fonts/t*.ttc   /usr/share/fonts/ttc/t/
cp   /home/temp_user/Theme/fonts/u*.ttc   /usr/share/fonts/ttc/u/
cp   /home/temp_user/Theme/fonts/v*.ttc   /usr/share/fonts/ttc/v/
cp   /home/temp_user/Theme/fonts/w*.ttc   /usr/share/fonts/ttc/w/
cp   /home/temp_user/Theme/fonts/x*.ttc   /usr/share/fonts/ttc/x/
cp   /home/temp_user/Theme/fonts/y*.ttc   /usr/share/fonts/ttc/y/
cp   /home/temp_user/Theme/fonts/z*.ttc   /usr/share/fonts/ttc/z/
cp   /home/temp_user/Theme/fonts/0*.ttc   /usr/share/fonts/ttc/0/
cp   /home/temp_user/Theme/fonts/1*.ttc   /usr/share/fonts/ttc/1/
cp   /home/temp_user/Theme/fonts/2*.ttc   /usr/share/fonts/ttc/2/
cp   /home/temp_user/Theme/fonts/3*.ttc   /usr/share/fonts/ttc/3/
cp   /home/temp_user/Theme/fonts/4*.ttc   /usr/share/fonts/ttc/4/
cp   /home/temp_user/Theme/fonts/5*.ttc   /usr/share/fonts/ttc/5/
cp   /home/temp_user/Theme/fonts/6*.ttc   /usr/share/fonts/ttc/6/
cp   /home/temp_user/Theme/fonts/7*.ttc   /usr/share/fonts/ttc/7/
cp   /home/temp_user/Theme/fonts/8*.ttc   /usr/share/fonts/ttc/8/
cp   /home/temp_user/Theme/fonts/9*.ttc   /usr/share/fonts/ttc/9/
cp   /home/temp_user/Theme/fonts/[*.ttc   /usr/share/fonts/ttc/other/

echo TTF 
cp   /home/temp_user/Theme/fonts/_*.ttf   /usr/share/fonts/ttf/other/
cp   /home/temp_user/Theme/fonts/a*.ttf   /usr/share/fonts/ttf/a/
cp   /home/temp_user/Theme/fonts/b*.ttf   /usr/share/fonts/ttf/b/
cp   /home/temp_user/Theme/fonts/c*.ttf   /usr/share/fonts/ttf/c/
cp   /home/temp_user/Theme/fonts/d*.ttf   /usr/share/fonts/ttf/d/
cp   /home/temp_user/Theme/fonts/e*.ttf   /usr/share/fonts/ttf/e/
cp   /home/temp_user/Theme/fonts/f*.ttf   /usr/share/fonts/ttf/f/
cp   /home/temp_user/Theme/fonts/g*.ttf   /usr/share/fonts/ttf/g/
cp   /home/temp_user/Theme/fonts/h*.ttf   /usr/share/fonts/ttf/h/
cp   /home/temp_user/Theme/fonts/i*.ttf   /usr/share/fonts/ttf/i/
cp   /home/temp_user/Theme/fonts/j*.ttf   /usr/share/fonts/ttf/j/
cp   /home/temp_user/Theme/fonts/k*.ttf   /usr/share/fonts/ttf/k/
cp   /home/temp_user/Theme/fonts/l*.ttf   /usr/share/fonts/ttf/l/
cp   /home/temp_user/Theme/fonts/m*.ttf   /usr/share/fonts/ttf/m/
cp   /home/temp_user/Theme/fonts/n*.ttf   /usr/share/fonts/ttf/n/
cp   /home/temp_user/Theme/fonts/o*.ttf   /usr/share/fonts/ttf/o/
cp   /home/temp_user/Theme/fonts/p*.ttf   /usr/share/fonts/ttf/p/
cp   /home/temp_user/Theme/fonts/q*.ttf   /usr/share/fonts/ttf/q/
cp   /home/temp_user/Theme/fonts/r*.ttf   /usr/share/fonts/ttf/r/
cp   /home/temp_user/Theme/fonts/s*.ttf   /usr/share/fonts/ttf/s/
cp   /home/temp_user/Theme/fonts/t*.ttf   /usr/share/fonts/ttf/t/
cp   /home/temp_user/Theme/fonts/u*.ttf   /usr/share/fonts/ttf/u/
cp   /home/temp_user/Theme/fonts/v*.ttf   /usr/share/fonts/ttf/v/
cp   /home/temp_user/Theme/fonts/w*.ttf   /usr/share/fonts/ttf/w/
cp   /home/temp_user/Theme/fonts/x*.ttf   /usr/share/fonts/ttf/x/
cp   /home/temp_user/Theme/fonts/y*.ttf   /usr/share/fonts/ttf/y/
cp   /home/temp_user/Theme/fonts/z*.ttf   /usr/share/fonts/ttf/z/
cp   /home/temp_user/Theme/fonts/0*.ttf   /usr/share/fonts/ttf/0/
cp   /home/temp_user/Theme/fonts/1*.ttf   /usr/share/fonts/ttf/1/
cp   /home/temp_user/Theme/fonts/2*.ttf   /usr/share/fonts/ttf/2/
cp   /home/temp_user/Theme/fonts/3*.ttf   /usr/share/fonts/ttf/3/
cp   /home/temp_user/Theme/fonts/4*.ttf   /usr/share/fonts/ttf/4/
cp   /home/temp_user/Theme/fonts/5*.ttf   /usr/share/fonts/ttf/5/
cp   /home/temp_user/Theme/fonts/6*.ttf   /usr/share/fonts/ttf/6/
cp   /home/temp_user/Theme/fonts/7*.ttf   /usr/share/fonts/ttf/7/
cp   /home/temp_user/Theme/fonts/8*.ttf   /usr/share/fonts/ttf/8/
cp   /home/temp_user/Theme/fonts/9*.ttf   /usr/share/fonts/ttf/9/
cp   /home/temp_user/Theme/fonts/[*.ttf   /usr/share/fonts/ttf/other/

echo XFT
cp   /home/temp_user/Theme/fonts/_*.xft   /usr/share/fonts/xft/other/
cp   /home/temp_user/Theme/fonts/a*.xft   /usr/share/fonts/xft/a/
cp   /home/temp_user/Theme/fonts/b*.xft   /usr/share/fonts/xft/b/
cp   /home/temp_user/Theme/fonts/c*.xft   /usr/share/fonts/xft/c/
cp   /home/temp_user/Theme/fonts/d*.xft   /usr/share/fonts/xft/d/
cp   /home/temp_user/Theme/fonts/e*.xft   /usr/share/fonts/xft/e/
cp   /home/temp_user/Theme/fonts/f*.xft   /usr/share/fonts/xft/f/
cp   /home/temp_user/Theme/fonts/g*.xft   /usr/share/fonts/xft/g/
cp   /home/temp_user/Theme/fonts/h*.xft   /usr/share/fonts/xft/h/
cp   /home/temp_user/Theme/fonts/i*.xft   /usr/share/fonts/xft/i/
cp   /home/temp_user/Theme/fonts/j*.xft   /usr/share/fonts/xft/j/
cp   /home/temp_user/Theme/fonts/k*.xft   /usr/share/fonts/xft/k/
cp   /home/temp_user/Theme/fonts/l*.xft   /usr/share/fonts/xft/l/
cp   /home/temp_user/Theme/fonts/m*.xft   /usr/share/fonts/xft/m/
cp   /home/temp_user/Theme/fonts/n*.xft   /usr/share/fonts/xft/n/
cp   /home/temp_user/Theme/fonts/o*.xft   /usr/share/fonts/xft/o/
cp   /home/temp_user/Theme/fonts/p*.xft   /usr/share/fonts/xft/p/
cp   /home/temp_user/Theme/fonts/q*.xft   /usr/share/fonts/xft/q/
cp   /home/temp_user/Theme/fonts/r*.xft   /usr/share/fonts/xft/r/
cp   /home/temp_user/Theme/fonts/s*.xft   /usr/share/fonts/xft/s/
cp   /home/temp_user/Theme/fonts/t*.xft   /usr/share/fonts/xft/t/
cp   /home/temp_user/Theme/fonts/u*.xft   /usr/share/fonts/xft/u/
cp   /home/temp_user/Theme/fonts/v*.xft   /usr/share/fonts/xft/v/
cp   /home/temp_user/Theme/fonts/w*.xft   /usr/share/fonts/xft/w/
cp   /home/temp_user/Theme/fonts/x*.xft   /usr/share/fonts/xft/x/
cp   /home/temp_user/Theme/fonts/y*.xft   /usr/share/fonts/xft/y/
cp   /home/temp_user/Theme/fonts/z*.xft   /usr/share/fonts/xft/z/
cp   /home/temp_user/Theme/fonts/0*.xft   /usr/share/fonts/xft/0/
cp   /home/temp_user/Theme/fonts/1*.xft   /usr/share/fonts/xft/1/
cp   /home/temp_user/Theme/fonts/2*.xft   /usr/share/fonts/xft/2/
cp   /home/temp_user/Theme/fonts/3*.xft   /usr/share/fonts/xft/3/
cp   /home/temp_user/Theme/fonts/4*.xft   /usr/share/fonts/xft/4/
cp   /home/temp_user/Theme/fonts/5*.xft   /usr/share/fonts/xft/5/
cp   /home/temp_user/Theme/fonts/6*.xft   /usr/share/fonts/xft/6/
cp   /home/temp_user/Theme/fonts/7*.xft   /usr/share/fonts/xft/7/
cp   /home/temp_user/Theme/fonts/8*.xft   /usr/share/fonts/xft/8/
cp   /home/temp_user/Theme/fonts/9*.xft   /usr/share/fonts/xft/9/
cp   /home/temp_user/Theme/fonts/[*.xft   /usr/share/fonts/xft/other/

echo end of file

cd /usr/share/fonts/
fc-cache -f -v


```

I used "cp" rather than "mv", to ensure that in the event of something going wrong, the original files would still be available.

There are more elegant ways of doing thing sort. I was taught badly --- disregard elegance at all costs.

jonathon

---

