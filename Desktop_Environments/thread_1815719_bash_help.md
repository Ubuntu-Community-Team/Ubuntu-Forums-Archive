---
title: "bash help"
date: 2011-07-31
forum: Desktop Environments
---

### Post by fdrake on 2011-07-31
ok i have a problem with "if" condition:
```

#!/bin/bash

playerId="0"; 


         if [ "$playerId" == "0" ];
                then
                echo "id is =empty"
                else
                echo "id is NOT empty"
           fi

playerId=$(ps --ppid "$parent" | grep "mplayer" | cut -d " " -f 1);
#when i do echo $playerId i have always a number ex. 32812. so it's never empty

         if [ "$playerId" == "0" ];
                then
                echo "id is =empty"
                else
                echo "id is NOT empty"
           fi



```
why it keeps saying:
```
"id is =empty"
"id is =empty"

instead of:

"id is =empty"
"id is NOT empty
```"

must be something stupid but ....

---

### Post by AlphaLexman on 2011-07-31
> **fdrake said:**
> ok i have a problem with "if" condition:
```

#!/bin/bash

playerId="0"; 


         if [ "$playerId" == "0" ];
                then
                echo "id is =empty"
                else
                echo "id is NOT empty"
           fi

playerId=$(ps --ppid "$parent" | grep "mplayer" | cut -d " " -f 1);
#when i do echo $playerId i have always a number ex. 32812. so it's never empty

         if [ "$playerId" == "0" ];
                then
                echo "id is =empty"
                else
                echo "id is NOT empty"
           fi



```
why it keeps saying:
```
"id is =empty"
"id is =empty"

instead of:

"id is =empty"
"id is NOT empty
```"

must be something stupid but ....

Where is the variable '**$parent**' set ??

---

### Post by fdrake on 2011-07-31
let me put the whole script maybe it's easier to understand

```

#!/bin/bash

#check if the input file has changed

file_t=$(ls -al input | cut -d " " -f 7)
file_t="$file_t";
echo "$file_t";

playerId="0"; #mplayer child PID
playerId="$playerId";

while :
        do

        file_n=$(ls -al input | cut -d " " -f 7)
        file_n="$file_n"
        echo "$file_n";                                 #check every 3 sec if the file "input" has been edited
        if [ "$file_t" != "$file_n" ];
                then
                echo "input has changed!"
                file_t=$file_n;                          #update the date of the "input" file           


#check first if you have any mplayer process running previously. id yes kill the child first and then make new process.

                               if [ "$playerId" == "0" ];
                                        then
                                        echo "id is =empty"
                                        else
                                        echo "id is NOT empty"
                                        kill -9 "$playerId"
                                fi


#This script executes every command line present in the input file (at the same time in the background)

                cat input | while read line; 
                                do

                                echo $line 
                                ($line | tee >> output) &

                                parent="$!";
                                playerId=$(ps --ppid "$parent" | grep "mplayer" | cut -d " " -f 1);
                                playerId="$playerId"
                                echo "$playerId";
  
                                done
                else
                :
                fi
        sleep 3
   done.


```

my problem is that in the 2nd if the condition is always true. so that the child process never gets killed...

---

### Post by fdrake on 2011-08-02
ok i solved the problem, it wasn't the loop the problem but the variable.mys solution was to write the result of a con=mmand in a file and then import that data line by line into a variable.

```
 
#check first if you have any mplayer process running previously. kill the child first and then make new process. 
 
                                cat ids | while read lineids;  
                                        do 
                                kill -9 $lineids 
                                        done 
 
 
 
#This script executes every command line present in the input file (at the same time in the background) 
 
                cat input | while read line;  
                                do 
                                echo $line  
                                ($line | tee >> output) & 
 
                                parent="$!"; 
                                ps --ppid "$parent" | grep "mplayer" | cut -d " " -f 1 | tee >> ids; 
                                echo "$(less ids)"; 
                                done 
                        echo "playerid : $(less ids)"; 
 
                else  
                : 
                fi 
        sleep 2 
        done 

-- VISUAL --                                                                                              48,0-1        Bot

```

---

