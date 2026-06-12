---
title: "help about wmctrl"
date: 2011-04-16
forum: Desktop Environments
---

### Post by wxuyec on 2011-04-16
I want to use wmctrl to focus my Adobe reader windows.
first I bind the <S-r> to "wmctrl -a "Adobe Reader"".
but when I have more than one Adobe windows, and
I can only pop up a certain one window, I can't go through
all the Adobe windows by hitting <S-r> again.
so I want to use the shell script. I write like this:
  1 #!/bin/sh
  2 
  3 a=$(wmctrl -l | grep "Adobe Reader" | awk '{print $4$5$6}' | wc -l)
  4 b=$(wmctrl -l | grep "Adobe Reader" | awk '{print $4$5$6}')
  5 #for((i==0;i<$a;i++));do
  6 #   c[i]=$(awk -F ' ' '{print $i}' $b);
  7 #   echo $c[i];
  8 #done;
  9 declare -a c;
 10 let i=0;
 11 for list in $b;
 12 do
 13 c[$i]=${list/-/ - };
 14 wmctrl -a ${c[i]}
 15 let i=i+1;
 16 done;
but it can only pop up all the Adobe windows. I can't go through them
one by one. so anybody gets some idea about it? 
Thank you in advance.

---

