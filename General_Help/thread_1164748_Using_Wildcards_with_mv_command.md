---
title: "Using Wildcards with mv command"
date: 2009-05-19
forum: General Help
---

### Post by linorics on 2009-05-19
I am trying to write a script and I have some files eg. 16_05_2009.0.bak 15_05_2009.1.bak. What I need to do is rename part of there name. so 16_05_2009.0.bak can become 16_05_2009.1.bak then 16_05_2009.2.bak etc. 

I know I can use the mv command to rename a file like 

```
mv 16_05_2009.0.bak 16_05_2009.1.bak
```

But is there a way I can use wildcards to preserve the date in the name. I know I can do the following.

```
mv *.0.bak /Path/to/workingDir/
```

And it will keep the name the same. But I need to do something like.

```
mv *.0.bak *.1.bak
```

I want to keep the first part of the name the same and just change the .0.bak part. Any Ideas??

---

### Post by asmoore82 on 2009-05-19
```

for file in *.0.bak
do
   mv -v "$file" "${file%.0.bak}.1.bak"
done

```

I LOVE this stuff. :KS

---

### Post by linorics on 2009-05-19
Perfect!! Thanks so much

If you have a sec could you explain the mv -v "$file" "${file%.0.bak}.1.bak" part.

---

### Post by asmoore82 on 2009-05-19
If you plan to continue to rotate the numbers up,
you will have to process from high to low ...

or else all of the *.0.bak files that were just processed to *.1.bak
will get caught in the next step of taking *.1.bak to *.2.bak

---

### Post by asmoore82 on 2009-05-20
I'm not sure how you create these files initially but an automated datestamp in standard ISO order may help - `date +%F`

something in the form of

```

for file in *
do
   cp -v "$file" "/path/to/backups/$( date +%F )_${file}.backup"
done

```

---

### Post by linorics on 2009-05-20
Yeah I get that. but in the "${file%.0.bak}.1.bak" string, what causes the .0.bak to be erased?

---

### Post by asmoore82 on 2009-05-20
> **linorics said:**
> Perfect!! Thanks so much

If you have a sec could you explain the mv -v "$file" "${file%.0.bak}.1.bak" part.

in BASH scripting

$file is the abbreviated form of variable reference
${file} is the full formal way
${file%string} is a way of saying "$file" but leave string off of the end
${file#string} is a way of saying "$file" but leave string off of the beginning

the % and # become much more powerful when you realize that string can contain wildcards:
${file%.*} is like "take off the extension"

if you double up on % or # it makes the wildcard "greedy":
if $file is "my.archive.tar.gz",
${file%.*}  will shorten it to "my.archive.tar"
${file%%.*} will shorten it to "my"
${file#*.}  will shorten it to "archive.tar.gz"
${file##*.} will shorten it to "gz"

It is important to remember that shells are text-processing powerhouses -
numbers not so much.

---

### Post by geirha on 2009-05-20
You'll probably want to do something like this:
```

date=16_05_2009

# Find the first available number ($i)
i=0
while [ -f "$date.$i.bak" ]; do
  i=$((i+1))
done

# Rename the files
while [ $i -gt 0 ]; do
  mv "$date.$((i-1)).bak" "$date.$i.bak"
  i=$((i-1))
done

```

---

### Post by asmoore82 on 2009-05-20
> **geirha said:**
> You'll probably want to do something like this:
```

date=16_05_2009

# Find the first available number ($i)
i=0
while [ -f "$date.$i.bak" ]; do
  i=$((i+1))
done

# Rename the files
while [ $i -gt 0 ]; do
  mv "$date.$((i-1)).bak" "$date.$i.bak"
  i=$((i-1))
done

```

The first while loop goes one loop too far - not stopping until it has found the first invalid number.
it could be immediately followed by a ```
i="$((i-1))"
```

But the whole thing sort of leaves behind the original premise of *.bak

---

### Post by linorics on 2009-05-20
Okay I got it working. Here it is if anyone is interested. 

##########################################################
##			Backup Script			##
##	Grabs files and makes increments of them.	##
##########################################################
#! /bin/bash

#### Setup and Config ####
##########################

## Enter the dir directory you want to backup
# /bin will backup the file bin and everything inside
# /bin/ will back up all files inside bin but not the file
srcDir="/home/chris/Desktop/files/"


## Enter the location of you backup location
# eg. /hardrive2/backups/
bakDir="/home/chris/scripts/"


## How many backups would you like to keep
# Note: The only size increase is from newly added or updated files
incNum=3



#### Logic and Commands ####
############################
curDate=`date +%d_%b_%Y`

## Remove oldest dir
echo
echo "Removing backup number $incNum" 

rm -rf $bakDir*.$incNum

## Move file one up
for (( i=incNum; i>1; i-- ))
do
	j=$(( $i - 1 ))
	echo
	echo "Moving file " $j " to $i"
	echo "########################"

	for file in *.$j
	do 
		mv -v "$bakDir$file" "$bakDir${file%.*}.$i"
	done
done

## Grab files and move to backup location
echo
echo "Copying all files from $srcDir to $bakDir$curDate.1"
mkdir $bakDir$curDate.1
rsync -av --delete $srcDir  $bakDir*.1

---

