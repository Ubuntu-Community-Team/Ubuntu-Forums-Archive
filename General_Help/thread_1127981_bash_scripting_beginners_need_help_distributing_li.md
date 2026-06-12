---
title: "bash scripting beginners: need help distributing lines from a line"
date: 2009-04-17
forum: General Help
---

### Post by xingchow on 2009-04-17
I need help as I am quite new to bash scripting.

At the moment I am trying to input parameters that are the number of markers (person whos marking a test/exam/etc) when execution. Then from there, I need to extract each line from student ID List (10 in total so far), and distribute them evenly for each markers, but if theres 1 extra, just add that to the first marker.

I have tried head and tail but have gotten a bit confused! 

Can anyone help a newb out :-D?

> #!/bin/bash

num=$*

# This creates the number of marker folders.


cut -f1 -d" " ClassList.data > studentIDList
cut -f1 -d" " ClassList.data | wc -l > numOfSubmissions

if((num <=9 || num >= 1))
        then
        for((k=1; k <= num; k++))
        do
                mkdir Marker${k}
                touch MarkSheet${k}
                mv MarkSheet$k Marker$k
        done

else
        echo "Parameter error!"
fi

---

