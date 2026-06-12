---
title: "Bash Loop Help"
date: 2008-12-12
forum: General Help
---

### Post by joec369 on 2008-12-12
Hello,

I'm trying to write a simple script. Here is what I have so far:
#! /bin/bash
echo "$USERNAME Please Login With Password!!"
COUNT=5
while [ COUNT > 0 ] ; do 
echo "Login Name: $USERNAME "
echo "Password:" 
read Psword 
if [ $PASSWORD = $PSWORD ] ; then
echo "Login Successful"
let COUNT=COUNT-5 
else 
if [ $PASSWORD != $PSWORD ] ; then
echo "Wrong Password!!"
let COUNT=COUNT-1
fi 
fi
done

Basically what I'm trying to do is to compare variables $PASSWORD to $PSWORD. If they are equal the just echo "Login Good" if they are not the same, then echo "Wrong Password." Now the part I can't figure out. I want to limit the number of failed attempts to five. So basically limit the endless while loop to only five go arounds. I've been trying to mess with this COUNT thing, but I don't know if it's what I need or not. 

Any Help Greatly apreciated!!!!!

---

### Post by Wayne_V on 2008-12-12
A few things:

1) you 'read Psword' but test '[ $PASSWORD = $PSWORD ]'.   Case is relevent

2) need to use $count in the while loop test

3) to compare integers use -eq  -ne -lt -le -gt or -ge (while [ $count -gt 0 ])

4) to compare strings you need to quote them (and also use == to be correct): '[ "$PASSWORD" == "$PSWORD" ]'

5) no need for the second if.  If the first '==' is false then '!=' is implied

So the final script:

> #! /bin/bash
echo "$USERNAME Please Login With Password!!"
COUNT=5
while [ $COUNT -gt 0 ] ; do
    echo "Login Name: $USERNAME "
    echo "Password:"
    read PSWORD
    if [ "$PASSWORD" == "$PSWORD" ] ; then
        echo "Login Successful"
        let COUNT=COUNT-5
    else
        echo "Wrong Password!!"
        let COUNT=COUNT-1
    fi
done

---

### Post by geirha on 2008-12-12
The > is already reserved for redirection, so your while is creating an empty file named "0". You need to use -gt (greater than) or -lt (lesser than) instead.

```
$ COUNT=5
$ while [ $COUNT -gt 0 ]; do echo -n $((COUNT--)); done; echo
54321
$ 
```
Read the man-page for the [ command.
```
man [
```

Also, variable names are case sensitive, so Psword is not the same as PSWORD.

EDIT: BTW, you can make read not echo the input by adding the -s (silent) option.

```
read -s PSWORD
```

---

### Post by Slim Odds on 2008-12-12
if you're using bash version 3, loops are easier
```
0> for i in {0..5}; do echo $i;done
0
1
2
3
4
5
0> for i in {5..0}; do echo $i;done
5
4
3
2
1
0

```

---

### Post by Wayne_V on 2008-12-12
another example:

```
#! /bin/bash
echo "$USERNAME Please Login With Password!!"
PASS=${PASSWORD:=password}
COUNT=4
echo "Login Name: $USERNAME "

while [ true ]
do
    read -s -t 5 -p "Password: " PSWORD
    R=$?
    if [ $R -ne 0 ] || [ "$PSWORD" == "$PASS" ] || [ $COUNT -le 0 ]
    then
        break;
    else
        echo "wrong"
        let COUNT=COUNT-1
    fi
done

if [ $COUNT -gt 0 ] && [ "x$PSWORD" != "x" ]
then
    echo "correct password: $PSWORD"
else
    echo "failed [$PSWORD / $COUNT]"
fi

```

---

