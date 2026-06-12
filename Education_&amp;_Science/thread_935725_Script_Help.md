---
title: "Script Help"
date: 2008-10-02
forum: Education &amp; Science
---

### Post by ergonomicdesign on 2008-10-02
Hello, I was wondering if anyone could give me a clue on how to solve this problem posed to me by a friend:

"When I put lecture notes on-line, I often have to start with a PPT file, since that's what most of my colleagues use. Exporting to html from OpenOffice (or PPT) gives a series of separate pages with "next" and "previous" links....But lecture notes are much more readable in linear format. An example is Dr. Frost's skin or respiratory system lectures, which I converted to a linear format by hand-editing the html pages I got from an OpenOffice export. But that's a lot of work. Seems like a simple script could go through the separate OO html pages and reorganize things into a linear structure. That would be really convenient."

Is there a quick way to do this? A script that he/I could make? Any help would be appreciated!

-Z

---

### Post by glinsvad on 2008-10-07
> **ergonomicdesign said:**
> 
"Exporting to html from OpenOffice (or PPT) gives a series of separate pages..."
-Z

Either you could export directly to PDF, which produces the correct output, or use online PPT-to-PDF conversion - this is especially useful for MS-office generated PPT which may or may not be displayed correctly by OpenOffice. I use [drawloop.com]("http://www.drawloop.com/"), which is free but requires login.

---

### Post by Catalyst2Death on 2008-10-07
If I understood correctly, you want to take the individual html pages spat out by open office, and convert them to one long page in html.

I think you could do it by running sed and awk over the the files... 

Pseudo code would be something like this:

Open first two slides, 

```
sed 's.<a href=next_page.html>Next</a>.<BR>.g' | sed 's.<a href=prev_page.html>Previous</a>..g'
```

This would strip the next and previous buttons, next we need to append the two together.
You could loop through the two files and echo each line out to a new one.  Once you have linearized.html then you repeat the process with the next slide and append it to linearized.html

Here is a short script that I used to copy a list of files from one partition to another using a file which contained the file names... I think it could be easily adapted to your case:

```
# This script copies files from another distro to the current one
# Adapted from code found at:  http://ubuntuforums.org/showthread.php?t=546495&highlight=bash+script+redirect+file+input
# Written by David Bjergaard 06/24/08 # `$file sed 's./media/disk..g'`"
path_to_txt="$HOME/dvd_files.txt"
# Save keyboard input and re-route stdin to our file
exec 6<&0
exec < $path_to_txt
numLines=`wc -l < $path_to_txt`
for i in `seq 1 "$numLines"`
do
    read filename
    files["$i"]="$filename"
done

#Restore Keyboard input
exec 0<&6 6<&-

#iterate through array, and perform file copies
for file in ${files[@]}
do
    file_temp=$file
    echo -n "sudo scp -rv $file_temp "
    echo  $file | sed 's./media/disk..g'
```

Happy scripting!

    Dave

---

