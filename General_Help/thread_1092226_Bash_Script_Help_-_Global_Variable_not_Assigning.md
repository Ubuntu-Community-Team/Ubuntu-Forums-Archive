---
title: "Bash Script Help - Global Variable not Assigning"
date: 2009-03-10
forum: General Help
---

### Post by g33kdot on 2009-03-10
Hello.

I'm trying to write a script to detect is a program is currently running, and then do something to it. Currently trying to get the base code to work and running into a block with my global array variable not populating. To be more specific, it populates while in my function, but seems to act like a local variable and dies after the function ends. I've added some echos to prove this.

I'm betting this is something simple I'm missing...any help?

```
#!/bin/bash

#remote startup script

##GLOBAL
# array LIST, stores output
####SUPPOSED to be a global array variable, LIST that is currently empty
declare -a LIST
PANDORA="xulrunner-bin"

##FUNCTIONS
#search function
search() {
echo "in search function..."
i=0
ps -A | grep $1 | while read line
do
    LIST[ $i ]=`echo $line | cut -d" " -f1`
    echo "LIST contains ${LIST[$i]}"
    echo "LIST contains ${#LIST[*]} items"
#####WORKS HERE
    (( i++ ))
done
}

##MAIN
if [ $1 == "pandora" ]
then
##Pandora Radio
search $PANDORA
#####DIES HERE, after run
echo "LIST contains ${#LIST[*]} items"

#####ALWAYS comes up with 0
if [ ${#LIST[@]} -eq 0 ]
then
 	echo "DEBUG: $PANDORA' == 0"
	
elif [ ${#LIST[@]} -eq 1 ]
then
	echo "DEBUG: $PANDORA == 1"
elif [  ${#LIST[@]} -gt 1 ]
then
	echo "DEBUG: $PANDORA > 1"

else
	echo "DEBUG: search using $SEARCH $PANDORA unsuccessful, unknown error."
fi

##end MAIN
fi

```

Thanks in advance!! :D

---

### Post by pyrofreek_9 on 2009-03-10
As far as I know, functions can't change global variables like that.. I would do something like this:

```
#!/bin/bash

#remote startup script

##GLOBAL
# array LIST, stores output
####SUPPOSED to be a global array variable, LIST that is currently empty
declare -a LIST
PANDORA="xulrunner-bin"

##FUNCTIONS
#search function
search() {
echo "in search function..."
i=0
ps -A | grep $1 | while read line
do
    #LIST[ $i ]=`echo $line | cut -d" " -f1`
    echo $line  | cut -d" " -f1
    #echo "LIST contains ${LIST[$i]}" 1>&2
    #echo "LIST contains ${#LIST[*]} items" 1>&2
#####WORKS HERE
    (( i++ ))
    export LIST
done
}

##MAIN
if [ "$1" == "pandora" ]
then
##Pandora Radio
LIST=( `search $PANDORA` )
#####DIES HERE, after run
echo "LIST contains ${#LIST[*]} items"

#####ALWAYS comes up with 0
if [ ${#LIST[@]} -eq 0 ]
then
 	echo "DEBUG: $PANDORA' == 0"
	
elif [ ${#LIST[@]} -eq 1 ]
then
	echo "DEBUG: $PANDORA == 1"
elif [  ${#LIST[@]} -gt 1 ]
then
	echo "DEBUG: $PANDORA > 1"

else
	echo "DEBUG: search using $SEARCH $PANDORA unsuccessful, unknown error."
fi

##end MAIN
fi
```

---

### Post by heindsight on 2009-03-10
I believe the problem is that pipelines are executed in subshells.
That is, when you do:
```
ps -A | grep $1 | while read line
do
    LIST[ $i ]=`echo $line | cut -d" " -f1`
    echo "LIST contains ${LIST[$i]}"
    echo "LIST contains ${#LIST[*]} items"
#####WORKS HERE
    (( i++ ))
done

```
Those commands are executed in a separate shell and thus the LIST array that you're assigning to is not the same LIST array that you declared at the top of your script. You can verify this by putting an:
```
echo ${LIST[*]}
```right after **done**(inside the search function).

Don't despair though, there's a much easier way of doing all of this. The pgrep command does exactly what you're trying to achieve with your search function. You can therefore rewrite your whole script like:
```
#!/bin/bash

#remote startup script

##GLOBAL
# array LIST, stores output
####SUPPOSED to be a global array variable, LIST that is currently empty
declare -a LIST
PANDORA="xulrunner-bin"

##MAIN
if [ $1 == "pandora" ]; then
  LIST=( `pgrep $PANDORA` )

  echo "LIST contains ${#LIST[*]} items"

  if [ ${#LIST[@]} -eq 0 ]; then
    echo "DEBUG: $PANDORA' == 0"
  elif [ ${#LIST[@]} -eq 1 ]; then
    echo "DEBUG: $PANDORA == 1"
  elif [  ${#LIST[@]} -gt 1 ]; then
    echo "DEBUG: $PANDORA > 1"
  else
    echo "DEBUG: search using $SEARCH $PANDORA unsuccessful, unknown error."
  fi

##end MAIN
fi
```

---

### Post by g33kdot on 2009-03-10
> **heindsight said:**
> I believe the problem is that pipelines are executed in subshells.
That is, when you do:
```
ps -A | grep $1 | while read line
do
    LIST[ $i ]=`echo $line | cut -d" " -f1`
    echo "LIST contains ${LIST[$i]}"
    echo "LIST contains ${#LIST[*]} items"
#####WORKS HERE
    (( i++ ))
done

```
Those commands are executed in a separate shell and thus the LIST array that you're assigning to is not the same LIST array that you declared at the top of your script. You can verify this by putting an:
```
echo ${LIST[*]}
```right after **done**(inside the search function).

Don't despair though, there's a much easier way of doing all of this. The pgrep command does exactly what you're trying to achieve with your search function. You can therefore rewrite your whole script like:
```
#!/bin/bash

#remote startup script

##GLOBAL
# array LIST, stores output
####SUPPOSED to be a global array variable, LIST that is currently empty
declare -a LIST
PANDORA="xulrunner-bin"

##MAIN
if [ $1 == "pandora" ]; then
  LIST=( `pgrep $PANDORA` )

  echo "LIST contains ${#LIST[*]} items"

  if [ ${#LIST[@]} -eq 0 ]; then
    echo "DEBUG: $PANDORA' == 0"
  elif [ ${#LIST[@]} -eq 1 ]; then
    echo "DEBUG: $PANDORA == 1"
  elif [  ${#LIST[@]} -gt 1 ]; then
    echo "DEBUG: $PANDORA > 1"
  else
    echo "DEBUG: search using $SEARCH $PANDORA unsuccessful, unknown error."
  fi

##end MAIN
fi
```

That should work great! THanks so much!

---

