---
title: "Nautilus script question..."
date: 2005-06-14
forum: Desktop Environments
---

### Post by Andrei on 2005-06-14
I am a bit of a n00b when it comes to linux and i have had one issue bugging me for a while...

Every so often...i'll make a file somewhere or mount a partition and it will be owned by root...now as i often actually want to access my mounted filesystems and files, (surprise, surprise!) i am getting rather frustrated with having to go through terminal and manually change ownership of said item...

I have a Nautilus script for opening a file as root, and i have tried to modify it to do a "chown" command on the selected file....but unfortunately it does not seem to like Nautilus's way of passing selected file names...

If anyone knows how i might be able to get over this Issue, it would be greatly appreciated thanks...

Btw...this is the srcipt i am currently trying to use:

```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-sudo "chown <insert user name here> $uri" &
done
```

Hope someone can help  :???:

---

### Post by GrumpySmurf on 2005-06-14
Rather than changing the permissions of the files, you can mount the partitions as another user.  Here's a sample using a FAT32 filesystem:

```
$ sudo mount -t vfat -o user=username,umask=0022 /dev/hdc1 /mnt/windows
```
The manual page for mount has more details.  'man mount'.

---

### Post by Andrei on 2005-06-14
I know that...but i would still like to be able to take ownership of a particular file...every so often i create one as root and it bugs me that i have to go through terminal to do it...it's just a convenience thing

---

### Post by shakin on 2005-06-14
I got you covered. Nautilus annoyingly passes the filename prepended with file:// for use in the Nautilus address bar.

Whenever you need the real filename, reference the variable this way: ${uri:7}

That will strip off the first seven characters.

Once you get this script working, please post it in the how-to section because I think a lot of people will get a use out of it. If you need a template for a Nautilus script how-to have a look at [this one](http://ubuntuforums.org/showthread.php?t=33584).

---

### Post by Andrei on 2005-06-14
Tried that...still didn't work...i found a scripting reference site and i've got the script working for one file only atm...multiple files are a bit more complicated...and i have exams to study for  ](*,) 
So i'm going to post the code i have done...and what i think needs to be done, and let someone else take over from here if they want...

Here's the code

```

#!/bin/bash

file
l_file
c_file
end_loop

for l_file in $NAUTILUS_SCRIPT_SELECTED_URIS	# Merges all selected files
do
	c_file=$c_file'"'"${l_file:7}"'"'
done

c_file=${c_file//'""'/'#'}			# Marks each individual file path start with '#'
c_file=$c_file'#'				# Appends another '#' to the end of the string
c_file=${c_file:1}				# Strip leading '#'
c_file=${c_file//'%20'/' '}			# Converts '%20' to spaces

end_loop=1					# Loop control

{
echo $c_file

# The following loop needs attention

while [ "$end_loop" -gt "0" ]
do
	file=${c_file:0:`expr index "$c_file" '#'`}
	c_file=${c_file:`expr index "$c_file" '#'`}
	file=${file%'#'}
	echo $file

	if [ "${#c_file}" -lt "1" ]
	do
		end_loop=0
	done
done
} &> $"/home/andrei/scriptlog.log"

# sudo chown andrei "$file" &> $"/home/andrei/errlog.log"

exit 0
```

The loop that is marked needs to basically parse the string of selected files into individual files and 'chown' them individually...shouldn't be too hard for someone who knows a bit more about scripting than me...

If anyone finishes this, feel free to post it in the HOWTO section...and post here saying that u have done so...so when i come back and finish this off...i don't duplicate the post  :) 

Cheers

---

### Post by motin on 2008-01-31
I have finished the script for you: [http://ubuntuforums.org/showthread.php?t=683945](http://ubuntuforums.org/showthread.php?t=683945)

(I too started out with 40+ of lines and loops and tempfiles, but everything worked out to only need aroun 2-3 lines as you can see in the above linked thread)

Cheers!

---

