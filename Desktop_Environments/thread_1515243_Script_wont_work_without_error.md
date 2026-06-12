---
title: "Script wont work without error"
date: 2010-06-22
forum: Desktop Environments
---

### Post by MalibuNL on 2010-06-22
Hi all,

I was using OpenSuse before, and due a crash - decided to go back to ubuntu.
I wrote a script in OpenSuse to measure temperatures from one of my snmp-enabled devices.

The script was running great and smoothless on OpenSuse, but when i transfer it to Ubuntu, it runs with errors, and some of the output is incorrect.

I've spent 1,5 day now finding why, but i cant find it - hope someone might be able to help me further.

The script as im running is this one:

```
#!/bin/bash
temp1=`/usr/bin/snmpget -v 1 -c Bla 172.19.37.253 .1.3.6.1.4.1.5528.100.4.1.1.1.7.2716713264`
humi1=`/usr/bin/snmpget -v 1 -c Bla 172.19.37.253 .1.3.6.1.4.1.5528.100.4.1.2.1.7.976244450`
dew1=`/usr/bin/snmpget -v 1 -c Bla 172.19.37.253 .1.3.6.1.4.1.5528.100.4.1.3.1.7.2634873273`
temp2=`/usr/bin/snmpget -v 1 -c Bla 172.19.37.253 .1.3.6.1.4.1.5528.100.4.1.1.1.7.2628357572`
humi2=`/usr/bin/snmpget -v 1 -c Bla 172.19.37.253 .1.3.6.1.4.1.5528.100.4.1.2.1.7.2804425567`
dew2=`/usr/bin/snmpget -v 1 -c Bla 172.19.37.253 .1.3.6.1.4.1.5528.100.4.1.3.1.7.1807639405`
leak=`/usr/bin/snmpget -v 1 -c Bla 172.19.37.253 .1.3.6.1.4.1.5528.100.4.2.10.1.7.399845582`
t1=${temp1##S* }
t1p=${#t1}-2
t1=${t1:0:$t1p}.${t1:$t1p:2}
h1=${humi1##S* }
d1=${dew1##S* }
t2=${temp2##S* }
t2p=${#t2}-2
t2=${t2:0:$t2p}.${t2:$t2p:2}
h2=${humi2##S* }
d2=${dew2##S* }
l1=${leak#S* }
l1p=${#l1}
l1=${l1:11:$l1p }
dd=`date +%Y-%m-%d\ %T`
mysql -u Temp_Check -ppassword -h localhost -D Temp_srvroom -e "insert temperature values('${dd}',${t1},${h1},${d1},${t2},${h2},${d2},'${l1}')"
exit 0
```

Errors i receive are:

```
")syntax error: invalid arithmetic operator (error token is "
")syntax error: invalid arithmetic operator (error token is "
")syntax error: invalid arithmetic operator (error token is "
: numeric argument requirede 24: exit: 0
```

Thanks in advance. Hope to learn alot about ubuntu in the future - as im an old Suse user :lolflag:

---

### Post by DaithiF on 2010-06-22
Hi,
I would try echo'ing out your mysql insert statement.  My guess would be that one of the numeric parameters has some non-numeric characters left over from the cleanups above.

```
echo "insert temperature values('${dd}',${t1},${h1},${d1},${t2},${h2},${d2},'${l1}')"
```

---

### Post by MalibuNL on 2010-06-22
As requested... i c that )=STRING:" is in which only should start at No Leak.
As i did :11 to arrange this in OpenSuse, i guess this is not the correct way in Ubuntu? 


```
command not foundned: line 2: 
")syntax error: invalid arithmetic operator (error token is "
")syntax error: invalid arithmetic operator (error token is "
 ")syntax error: invalid arithmetic operator (error token is "
')= STRING: "No Leak"lues('2010-06-22 09:52:03
: numeric argument requirede 26: exit: 0


```

---

### Post by DaithiF on 2010-06-22
Hi,
You need to provide more information.  Which variable doesn't contain the result you expect?  I'm guessing its ll, but how can we help if we don't know:
1. what value the $leak variable starts out with
2. what value you want $ll to be left with after your substitutions, cleanups, etc.

thanks

---

### Post by MalibuNL on 2010-06-22
> **DaithiF said:**
> Hi,
You need to provide more information.  Which variable doesn't contain the result you expect?  I'm guessing its ll, but how can we help if we don't know:
1. what value the $leak variable starts out with
2. what value you want $ll to be left with after your substitutions, cleanups, etc.

thanks

I'm sorry.

1. The value it is posting out is =STRING("No Leak") or =STRING("Leak")
2. Value $l1 should be No Leak or Leak when finished
3. I'm using Ubuntu 10.04

---

### Post by DaithiF on 2010-06-22
Hi,
I don't know how this could have ever worked.  (Bash is bash, it shouldn't matter whether its Ubuntu or Suse)

this line:
**l1=${leak#S* }** has no effect, it leaves l1 with the same contents as $leak.  It says: strip from the left hand side of leak the shortest string you can which starts with 'S' and continues to the first space character.  Since $leak starts with a '=', nothing is matched.
**l1p=${#l1}**  then gives $l1p the value 18, being the length of the l1 string (or 15 if the string was leak rather than no leak)
**l1=${l1:11:$l1p }** then takes a substring of length 18 from $l1, starting at position 11, which results in **No Leak")**

and by the way, the choice of l1 as a variable name alongside the constant 11 is horribly confusing.

I would guess that the output of your snmpgets has changed subtlely, which throws out the attempted cleanups below.  

I would just start again, there are less confusing ways of parsing out the bit in quote marks from a string, some examples below...

leak='=STRING("No Leak")'
l1=${leak#*\"}
l1=${l1%\"*}
echo $l1

leak='=STRING("No Leak")'
l1=$(echo $leak | cut -d\" -f2)
echo $l1

leak='=STRING("No Leak")'
l1=$(echo $leak | sed 's/^.*("//;s/").*$//')
echo $l1

---

### Post by MalibuNL on 2010-06-23
Thanks for your help. The output is OK now, but errors seems to be still in.

Errors can be bad sometimes - but in this case, are they?

---

### Post by DaithiF on 2010-06-23
Hi,
taking a wild guess, did you edit/save this file on windows?  The syntax errors invalid arithmetic issues could be caused by having windows-style line endings on the lines where you are doing arithmetic (ie. where you are subtracting 2 from the lengths of variables.

install tofrodos and convert to unix line endings and try again.
```
sudo apt-get install tofrodos
dos2unix yourscript

```also, these lines:
t1p=${#t1}-2
don't actually perform arithmetic in the way you may expect.  Try this:
x="hello"
t1p=${#x}-2
echo $t1p
5-2

t1p=$(( ${#x}-2 ))
echo $t1p
3

the subtring expression ${variable:start:length} is able to correctly interpret the 5-2 and does the arithmetic for you, but you may get tripped up by this elsewhere, so better to use the $(( .... )) form of doing arithmetic.

---

### Post by MalibuNL on 2010-06-23
> **DaithiF said:**
> Hi,
taking a wild guess, did you edit/save this file on windows?  The syntax errors invalid arithmetic issues could be caused by having windows-style line endings on the lines where you are doing arithmetic (ie. where you are subtracting 2 from the lengths of variables.


Im working on it via my Ubuntu Desktop - but i had it once on my windows desktop.

I'll try dos2unix, maybe something went wrong when i had it on my XP desktop...

EDIT:
Ok, installed the package and runned the command "fromdos <script>", errors are gone now.
I guess the transfer from suse to ubuntu using FTP on my windows client resulted in this errors.

Scripts running fine! thanks for the great help!

---

### Post by DaithiF on 2010-06-23
great, you're welcome.

and welcome to Ubuntu.

---

