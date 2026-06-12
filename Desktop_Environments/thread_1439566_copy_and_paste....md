---
title: "copy and paste..."
date: 2010-03-26
forum: Desktop Environments
---

### Post by JakeOfOz on 2010-03-26
Hi,
I want to sort my music folder, which is full of other folders containing music, I want all the files in one folder, so I made the following script:

#!/bin/bash
find -name ".mp3" | \
while read file
do
cp "$file" /Music/Sorted/

problem is, I want to edit some of the names, so i want the script to move all the found mp3s into the folder where the script is (so i can copy the script and  use it in other folders too)
any tips?

---

