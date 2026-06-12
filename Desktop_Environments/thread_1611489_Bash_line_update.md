---
title: "Bash line update"
date: 2010-11-01
forum: Desktop Environments
---

### Post by kkaldroma on 2010-11-01
This is more of a bash or scripting question but I can't find a solid answer anywhere.. so, sorry for the miss-post.

How do you update a single line of an output in a bash script. I have had to do the:
while...
   echo ... 
   sleep 1
   clear
   echo .....
thing, which looks terrible.

Is there a way to clear only a single line of output?

my goal is to mimic a single line animation, much like the '=>' '==>' ' ===>' we have all seen in other programs.

---

### Post by Old *ix Geek on 2010-11-02
Let me start off by saying that I hadn't even THOUGHT about anything like this in about 20 years...so, yeah, I'm a bit rusty. :eek:

With that said, I just knocked this out and if you use it as a starting point, it may do what you want.

```
while :
do tput cup 10 0
echo "=>"
sleep 1
tput cup 10 0
echo ""
echo "==>"
sleep 1
tput cup 10 0
echo ""
echo "===>"
sleep 1
tput cup 10 0
echo ""
echo "====>"
sleep 1
tput cup 10 0
echo ""
echo "=====>"
sleep 1
tput cup 10 0
echo ""
echo "======>"
sleep 1
done
```
and so on.

If you're not familiar with **tput**, definitely look at its man page. Briefly, the **tput cup 10 0** lines are placing the cursor at column 0 on line 10.

---

### Post by DaithiF on 2010-11-02
and an alternative using printf and \r to reset cursor back to the start of the current line:
```
lines="==========="
while :
do
        count=$(( count + 1 ))
        (( count == 10 )) && count=1
        printf "%s>%10s\r" ${lines:0:count} " "
        sleep 0.5
done

```

---

### Post by kkaldroma on 2010-11-03
Thank you for your help, this has cleaned up a number of my scripts.

---

