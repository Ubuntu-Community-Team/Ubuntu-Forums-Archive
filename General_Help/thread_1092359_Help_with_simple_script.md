---
title: "Help with simple script"
date: 2009-03-10
forum: General Help
---

### Post by geo909 on 2009-03-10
Hello everybody,

I need some help with a simple shell script. Here's
the deal: I have a huge amount of mp3s (a 47-hour
narration cut down in 6-7 minute mp3s!!). Their naming
scheme does not really help to distinguish the order (crucial!)
so I was thinking about reanaming them in respect to the
moment created (that is the correct order).

So, the naming scheme will be:
1.mp3, 2.mp3, 3.mp3, 4.mp3, ...

where 1.mp3 is the file first created, 2.mp3
the second newest etc..

I am not familiar with the scripting language,
but I guess it must be something simple, like:

```
#!/bin/bash

N=1;
for FILE in 'ls -someoption'; do
mv "$FILE" "$N.mp3"

N=N+1
done 

```

Hmm.. Is the above correct?

ls -someoption should sort files by the day of creation.
Is that "modification time"? I have played some files, but really
didn't "modify" them in any way. Any ideas of what should be the
correct flag here?

ALso I am not sure if the quotes should be used for "$FILE"
and "N.mp3"..
ANyway, I am searching around and there are many great pages for
shell scripting but I am kinda lost, so any help would be really 
appreciated...

Thanks

---

### Post by pyrofreek_9 on 2009-03-10
I think you'd be looking for something like this:

```
#!/bin/bash

n=1

ls -t -1 | while read file
do
    mv "$file" $n.mp3
    ((n++))
done
```

---

### Post by unutbu on 2009-03-10
Use ls -tr -1 to reverse the order of the listing.
This way, the oldest file gets named 1.mp3.

Also, to increment N, I think pyrofreek_9 meant N=$((N+1))

[PHP]N=1
ls -tr -1 | while read file
do
    mv "$file" "$N.mp3"
    N=$((N+1))
done
[/PHP]

---

### Post by heindsight on 2009-03-10
Sorting the files by modification time should work. You can use the -t flag to **ls** to sort files by modification time.

A for loop can work for what you want to do, but you may run into difficulty with filenames that contain spaces. To avoid that you could change the IFS variable, which tells the shell at which characters separate "words". However, I usually find it easier to use a while loop instead.

Quotes aren't necessary, but a good idea to avoid problems with spaces in names.

I would do it like:
```

#!/bin/sh
N=1
ls -tr *.mp3 | while read name; do
    mv "$name" "$N.mp3"
    N=$((N+1))
done

```

EDIT:
hehe, I'm a bit slow with the typing it seems :) 
unutbu makes a good point regarding the use of -r to reverse the output, the way I had it originally would have made the last file created 1.mp3 instead of the other way round...

---

### Post by geo909 on 2009-03-10
Thanks you all, guys, that was really helpful!

heindsight, could you please explain the thing with the space in the names?
The names are indeed full of spaces (below my ls -tr, and my files in the
correct order - thanks unutbu!):


```

The Count of Monte Cristo (Unabridged), Part 1.mp3
The Count of Monte Cristo (Unabridged), Part 11.mp3
The Count of Monte Cristo (Unabridged), Part 12.mp3
The Count of Monte Cristo (Unabridged), Part 13.mp3
The Count of Monte Cristo (Unabridged), Part 14.mp3
The Count of Monte Cristo (Unabridged), Part 15.mp3
The Count of Monte Cristo (Unabridged), Part 16.mp3
The Count of Monte Cristo (Unabridged), Part 17.mp3
The Count of Monte Cristo (Unabridged), Part 18.mp3
The Count of Monte Cristo (Unabridged), Part 19.mp3
The Count of Monte Cristo (Unabridged), Part 110.mp3
The Count of Monte Cristo (Unabridged), Part 111.mp3
The Count of Monte Cristo (Unabridged), Part 112.mp3
The Count of Monte Cristo (Unabridged), Part 113.mp3
The Count of Monte Cristo (Unabridged), Part 114.mp3
The Count of Monte Cristo (Unabridged), Part 115.mp3

.
.
.

The Count of Monte Cristo (Unabridged), Part 656.mp3
The Count of Monte Cristo (Unabridged), Part 657.mp3
The Count of Monte Cristo (Unabridged), Part 658.mp3
```

"ls -tr *mp3" will present things as above, with all the spaces.
(What's IFS?!). Is the line 
```
ls -tr *.mp3 | while read name; do
```
going to fix that? (OK, I guess I should run an example here, lazy me! :))

---

### Post by heindsight on 2009-03-10
Well, when you use a **for** loop like:
```
for name in $(ls -tr *.mp3); do COMMANDS; done
```
the shell splits the output of the **ls** command into a list of "words". For each word in the list $name takes the word as value and then the COMMANDS are executed for that value of $name. 

The builtin shell variable **IFS** determines where words are split - IFS is a string variable and any character in **IFS** is used as a word delimiter. Normally **IFS** contains all the whitespace characters. Thus under normal operation the output of the **ls** command will be split at spaces, which means that filenames with spaces will be split into more than one word - in other words if you have a file called "Foo Bar.mp3" then the COMMANDS of the **for** loop will be executed for $name with the value "Foo" and then with the value "Bar.mp3" which obviously is not what you want.

To avoid this kind of situation, you can set the value of IFS to something other than the default, for example just a newline character (or in some cases a NULL character), however I usually find it easier to simply pipe the output of such an **ls** command to a while loop (as in the example I gave before. When you do:
```
ls -tr *.mp3 | while read name; do COMMANDS; done
```
then the names of the mp3 files are printed by **ls** (one per line) to the standard input of the **read** command.
```
while read name; do COMMANDS; done
```
then reads one line (ie one mp3 filename) at a time into the $name variable (placing the entire line into the variable without splitting it). and so the COMMANDS are executed once for each .mp3 file as you'd expect.

Another problem with spaces arises when you pass names with spaces as arguments to commands. Once again, the shell splits arguments into words at characters in the IFS variable. So if $name has the value "Foo Bar.mp3" and you do:
```
mv $name 1.mp3
```
then $name will be split into Foo and Bar.mp3 and **mv** will complain about non-existent files (or try to move existing files Foo and Bar.mp3 into a directory called 1.mp3). Once again, you could modify **IFS** to get around this, but I generally find it better to use quoting (quoted text is generally treated as a single word). Thus,
```
mv "$name" 1.mp3
```
will correctly rename "Foo Bar.mp3" to 1.mp3

---

### Post by geo909 on 2009-03-10
Woa, that was a *good* explanation, I think that now I am much more capable of writing such small scripts that make my life easier!!
Thank you so much for taking the time to write this! I will save it somewhere for future reference!

---

### Post by geo909 on 2009-03-10
Well, I have another question..

Could you tell me why the following script works

```
#!/bin/bash

N=1
i=1

ls -tr -1 "The Count of Monte Cristo (Unabridged), Part $i"* | while read name; do
    echo "$name" 
    echo "$N.mp3"
    N=$((N+1))
done

```

whereas the following does *not* work?!
```

#!/bin/bash

N=1

for i in 1 2 3 4 5 6 do

ls -tr -1 "The Count of Monte Cristo (Unabridged), Part $i"* | while read name; do
    echo "$name" 
    echo "$N.mp3"
    N=$((N+1))
done
done

```

Here is the output:
```
./MYSCRIPT: line 7: syntax error near unexpected token `ls'
./MYSCRIPT: line 7: `ls -tr -1 "The Count of Monte Cristo (Unabridged), Part $i"* | while read name; do'

```

WHat is the difference if I assign a value in i in a for loop?! :-/

Thanks again..

---

### Post by heindsight on 2009-03-11
> **geo909 said:**
> Well, I have another question..

Could you tell me why the following script works

```
#!/bin/bash

N=1
i=1

ls -tr -1 "The Count of Monte Cristo (Unabridged), Part $i"* | while read name; do
    echo "$name" 
    echo "$N.mp3"
    N=$((N+1))
done

```

First thing I notice is that here, $i is always 1. So this lists all files with names that start with "The Count of Monte Cristo (Unabridged), Part 1", and loops over those names.

> **geo909 said:**
> 
whereas the following does *not* work?!
```

#!/bin/bash

N=1

for i in 1 2 3 4 5 6 do

ls -tr -1 "The Count of Monte Cristo (Unabridged), Part $i"* | while read name; do
    echo "$name" 
    echo "$N.mp3"
    N=$((N+1))
done
done

```

Here is the output:
```
./MYSCRIPT: line 7: syntax error near unexpected token `ls'
./MYSCRIPT: line 7: `ls -tr -1 "The Count of Monte Cristo (Unabridged), Part $i"* | while read name; do'

```

WHat is the difference if I assign a value in i in a for loop?! :-/

Thanks again..
The first problem here is that you need a **;** before the **do**. In other words change your **for** loop to:
```
for i in 1 2 3 4 5 6; do
```
That should get rid of the error you've been getting. With that modification you'll first loop through all filenames starting with "The Count of Monte Cristo (Unabridged), Part 1", then names starting with "The Count of Monte Cristo (Unabridged), Part 2", etc.

However here you will encounter the biggest drawback to piping output from a command (like **ls** in this case) to a loop. The problem is that each command in a "pipeline" like this is executed in a subshell. In other words, here your entire **while** loop is executed in a separate shell environment from the rest of your script, which means that the variable $N you use inside the **while** loop is not the same as the variable $N outside the loop. The effect this will have is that each for each value of $i, your $N will start counting from 1 again up to however many files there are for that $i.

In cases like this, I believe you are actually better off changing the value of **IFS** and using a for loop. So try it like this instead:
```
#!/bin/sh

N=1
IFS=$'\n'
for i in 1 2 3 4 5 6; do
    for name in $(ls -tr "The Count of Monte Cristo (Unabridged), Part $i"*); do
        echo "$name" 
        echo "$N.mp3"
        N=$((N+1))
    done
done
```
What we're doing here, is setting the value of **$IFS** so that words are only split at newline characters. **ls** will still output the filenames one per line, and this time instead of splitting words at every space, words will only be split at the ends of lines meaning that each file name will be treated as a single word, even if the name does contain spaces.

EDIT:
You may find this [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) usefull. It's the Advanced Bash-Scripting Guide.

---

### Post by geo909 on 2009-03-11
Thank you very much again. That helped me to understand some things.
Though the semicolon was what I used, I made a script that actually 
splits the mp3s in 6 folders in the right order (the book has 6 parts), so it is even more controllable. It worked fine! 


Thanks you very much for your time, you really helped.

---

