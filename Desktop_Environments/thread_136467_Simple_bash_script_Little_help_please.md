---
title: "Simple bash script: Little help please"
date: 2006-02-26
forum: Desktop Environments
---

### Post by harold4 on 2006-02-26
Not sure if this is the right area to put this, but here goes...

The purpose of this script is to check my external ip; changing the ip address in file ~/ip if the ip address has changed, as well as mail the new ip.

The following conditional stmt returns true, even when $var1 = $var2.

I tried debugging this by writing the lynx dump to file ip, copy contents of ip to file ip2 using gedit, then var1=`cat ip` var2=`cat ip2`
Also, after running cat on ip and ip2, echo $var1 and echo $var2 show the same visible results.  

I'm leaning towards this being a logic error.

any suggestions are appriciated.

```

var1=`lynx -dump http://checkip.dyndns.org`
var2=`cat ip`

## Debugging purposes
echo $var1
echo $var2

if [ "$var2" != "$var1" ]; then
	echo $var1 > ip
	echo $var1 | mail -s "IP" email@address.com
fi

```

---

### Post by cilynx on 2006-02-26
This works for me...

```

rcw@pyth:~$ cat ip

   Current IP Address: 72.128.94.214
rcw@pyth:~$ sh script.sh

   Current IP Address: 72.128.94.218

   Current IP Address: 72.128.94.214
Updating IP
rcw@pyth:~$ cat ip

   Current IP Address: 72.128.94.218
rcw@pyth:~$ sh script.sh

   Current IP Address: 72.128.94.218

   Current IP Address: 72.128.94.218
rcw@pyth:~$ cat ip

   Current IP Address: 72.128.94.218
rcw@pyth:~$ cat script.sh
var1=`lynx -dump http://checkip.dyndns.org`
var2=`cat ip`

## Debugging purposes

echo "$var1"
echo "$var2"

if [ "$var2" != "$var1" ]
then
   echo "Updating IP"
   echo "$var1" > ip
fi
rcw@pyth:~$

```

---

### Post by harold4 on 2006-02-26
I did not have the .sh extension on the script... duh.  Thx for the insight.  Just started learning bash earlier today :)

Is there any adverse effect for having the ; in the if stmt? ## ] ; then.  Noticed that you took it out of the edited script

---

### Post by nanotube on 2006-02-26
your script does not have to have a .sh extension, if you put this line as the first line in your script:
```
#!/bin/bash
```

---

### Post by harold4 on 2006-02-26
**This post was to show an example of the script updating with var1 and var2 being the same, but...

RM'd ip and the sh, created new files and has worked 10 times in a row.

---

### Post by cilynx on 2006-02-26
As said before, the '.sh' extension is unnecessary, just good form.  Having the ';' or not doesn't make much difference either.  It pretty much takes the place of hitting Enter.  The main change that I made was putting the $var's in quotes during the echos statements.  The problem with the initial script is that the whitespace of the variable was being truncated when you echoed it, but not when doing the comparison.  Thus, they were not the same.  Putting the vars in quotes preserves the whitespace.

---

### Post by harold4 on 2006-02-27
Makes sense

Have any suggestions for good books to read about bash?

---

### Post by cilynx on 2006-02-27
You may want to check out the Advanced Bash-Scripting Guide

[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

---

