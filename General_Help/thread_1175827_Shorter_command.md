---
title: "Shorter command?"
date: 2009-06-01
forum: General Help
---

### Post by Psycho.mario on 2009-06-01
I have a script that has this command in it:
```
diff=`diff <(echo "$target") <(echo "$current") | sed s/.*\>// | sed s/0a.*// | sed s/2a.*// | sed s/\ // | sed '/^$/d' | sed s/5d.*// | sed s/.*\<// | sed s/4d.*// | sed s/4a.*// | sed s/3a.*//`
```
It's removing some output from the diff command. Basically, the diff command outputs something like:
```
4d5
192.168.1.1
192.168.1.2
```
Is there a general command for removing the number-letter-number without touching the IP's?

---

### Post by ibuclaw on 2009-06-01
First question, why so many pipes? Sed can handle it in one or with multiple -e's.

```
diff=`diff <(echo "$target") <(echo "$current") | sed 's/.*\>//; s/0a.*//; s/2a.*//; s/\ //; /^$/d; s/5d.*//; s/.*\<//; s/4d.*//; s/4a.*//; s/3a.*//'`
```

or
```
diff=`diff <(echo "$target") <(echo "$current") | sed -e 's/.*\>//' -e 's/0a.*//' -e 's/2a.*//' -e 's/\ //' -e '/^$/d' -e 's/5d.*//' -e 's/.*\<//' -e 's/4d.*//' -e 's/4a.*//' -e 's/3a.*//'`
```

But surely there must be an easier way ...
What is the original values/content in $target and $current ?

Is it just IP addresses that you want to fish out of the diff, or something more generic?

Regards
Iain

---

### Post by sisco311 on 2009-06-01
how about:
```
awk '!/[a-z]/{ print }'
```
or
```
grep -v [a-z]
```

---

### Post by ibuclaw on 2009-06-01
Well... this should fork out all IP addresses:
```
diff=`diff <(echo "$target") <(echo "$current") | perl -nle 'print $1 if($_ =~ /.*?(\d{1,3}(\.\d{1,3}){3}).*/)'`
```

Regards
Iain

---

### Post by Psycho.mario on 2009-06-02
That command almost works: it removes the unwanted bits, but its not doing the diff properly. Heres the script im using it in:
```
#!/bin/bash
#######################################################
#--------------------Start Editing--------------------#
#Please set these variables:
#Hosts that are always online (e.g. servers, printers...) one ip per line
target="192.168.1.1
192.168.1.4
192.168.1.10
192.168.1.199"
#Timeout for notification
timeout=5
#Title for notification
title="Hosts online:"
#ip system (e.g. 192.168.1.1 or 10.0.1.1) First ip in range. Must be *.*.*.1
ipsys=192.168.1.1
#Time to wait between each run (sec)
sleep=10
#--------------------Stop Editing---------------------#
#######################################################
while [ 1 = 1 ]
do
if [ -s /tmp/online ]; then
    target=`cat /var/tmp/online`
    rm /tmp/online
else
    target=`echo "$target"`
fi
current=`nmap -sP $ipsys-255 | sed s/.*T// | sed s/N.*// | sed s/.*t\ // | sed s/\ app.*// | sed '/^$/d'`
if [ "$current" == "$target" ]; then
    echo "" > /dev/null
else    
    diff=`diff <(echo "$target") <(echo "$current") | sed s/.*\>// | sed s/0a.*// | sed s/2a.*// | sed s/\ // | sed '/^$/d' | sed s/5d.*// | sed s/.*\<// | sed s/4d.*// | sed s/4a.*// | sed s/3a.*//`    
        if [ -s /usr/bin/gxmessage ]; then    
            gxmessage -center -nofocus -title "$title" -timeout $timeout "$diff"
        else
            xmessage -timeout $timeout "$diff"
        fi
fi
echo "$current" > /tmp/online
sleep $sleep
done
```



It's very messy, but it is my First ever bash script and i haven't got the hang of it yet.
It's line 32 that the command is on that wants changing. 
If you can reccommend any other bits to clean up then please do, but i don't want to completely change the code, i stilll want it to be my script, not a list of botched together commands.

Thanks

---

### Post by sisco311 on 2009-06-02
[list=i]
[*]if you want to compare $current and $target line by line, then you have to add the newlines (\n) manually:
```
target="192.168.1.1\n\
192.168.1.4\n\
192.168.1.10\n\
192.168.1.199"
```

and
```
current=$(nmap -sP 192.168.2.* | awk '{ if ($1=="Host") print $2;}')
current=$(echo $current | sed 's/ /\\n/g')

```

now you can use diff to compare $target and $current line by line:
```
diff <(echo -e $current) <(echo -e $target)
```


[*]```
if [ -s /tmp/online ]; then
    target=`cat /var/tmp/online`
    rm /tmp/online
else
    target=`echo "$target"` #this else statement is redundant 
fi
```

```
if [ -s /tmp/online ]; then
    target=`cat /var/tmp/online`
    rm /tmp/online
fi
```


[*]```
if [ "$current" == "$target" ]; then
    echo "" > /dev/null # redundant
else    
...
fi
```

```
if [ "$current" != "$target" ]; then
...
fi
```


[*]I still don't understand what's your goal with the *diff* command.
[/list]

---

### Post by Psycho.mario on 2009-06-02
i: Doesn't work, Output is all wrong

ii: I know

iii: I know

ii & iii: I know is shouldn't be there but it helps me when im reading it (remember, its my first script)

iv: basically, it finds the difference between online hosts and the hosts in the list and tells me which hosts are online. The hosts in the list are things like myself and the router.

---

