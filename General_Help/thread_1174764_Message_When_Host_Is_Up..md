---
title: "Message When Host Is Up."
date: 2009-05-31
forum: General Help
---

### Post by Psycho.mario on 2009-05-31
Is it possible to have ubuntu message me (xmessage?) when another host comes online?
I am on a wireless network and i want to know when other people log into my network. Is there a script that will tell me who is logged in at that moment?
 I know i can find out using 
```
nmap -sP 192.168.0.1-255
```How can i script this so that it will tell me when another computer comes online?
P.S. I'm using DHCP

Thanks

---

### Post by blueridgedog on 2009-05-31
```
nmap -sP 192.168.0.1-255 | tail -1 | sed s/.*\(// | sed s/\).*//

```

Will get you "x hosts up".  You could use the sed trick to drop the " hosts up" part as well.  From here you need to write a script that runs this and compares the value to a given variable.  If the two variables don't match, then it needs to send you a message.  I would be glad to look at what you come up with or suggest the next step if you need a bump.

---

### Post by Psycho.mario on 2009-05-31
Ok, So im trying to make a script:
The output of the command (**nmap -sP 192.168.1.1-255**)
Gives me this:
```
Starting Nmap 4.76 ( http://nmap.org ) at 2009-05-31 19:24 BST
Host 192.168.1.1 appears to be up.
Host 192.168.1.4 appears to be up.
Host 192.168.1.10 appears to be up.
Host 192.168.1.199 appears to be up.
Nmap done: 255 IP addresses (4 hosts up) scanned in 1.16 seconds
```If i make this as a variable, how can i 'chop' down the variable to it is just:
```
192.168.1.1
192.168.1.4
192.168.1.10
192.168.1.199
```
Thanks for all help so far


(Im sure this has something to do with your 'sed' command, but i sadly don't have a clue)

---

### Post by Psycho.mario on 2009-05-31
I did it;
```
var="Starting Nmap 4.76 ( http://nmap.org ) at 2009-05-31 19:44 BST
Host 192.168.1.1 appears to be up.
Host 192.168.1.4 appears to be up.
Host 192.168.1.10 appears to be up.
Host 192.168.1.199 appears to be up.
Nmap done: 255 IP addresses (4 hosts up) scanned in 1.36 seconds"
var2=`echo "$var" | sed s/.*T// | sed s/N.*//`
var3=`echo "$var2" | sed s/.*t\ // | sed s/\ app.*//`
echo "$var3"
```Wants tidying up, but it works. Slight problem though. That script gives me:
```
me@Ubuntu:~/Desktop$ ./Online.sh 

192.168.1.1
192.168.1.4
192.168.1.10
192.168.1.199
me@Ubuntu:~/Desktop$ 

```
How can i remove the blank line??
Thanks

---

### Post by Psycho.mario on 2009-05-31
The script so far:
```
var="192.168.1.1
192.168.1.4
192.168.1.10
192.168.1.199"
if [ "`nmap -sP 192.168.1.1-255 | sed s/.*T// | sed s/N.*// | sed s/.*t\ // | sed s/\ app.*//`" == "$var" ]; then
    echo "No one has come online"
else
    echo "Someone else has come online"
fi
```Thanks for the help so far :)

P.S. Still the blank line though :(

---

### Post by blueridgedog on 2009-05-31
Why not just add the blank line to var?

---

### Post by Psycho.mario on 2009-06-01
Bash doesn't like that. How can i find the difference between two variables?

e.g
```
var="192.168.1.1
192.168.1.2
192.168.1.3"

var2="192.168.1.1
192.168.1.2
192.168.1.3
192.168.1.4"

Difference=192.168.1.4
```Thanks

P.S. I'd rather NOT use temp files (write each var to file, use diff)

---

### Post by Psycho.mario on 2009-06-01
Ok, I found out how
```
diff <(echo "$a") <(echo "$b")
```That works, now i just need to sed it down to the bare minimum

---

### Post by Psycho.mario on 2009-06-01
Here's the script so far:
```
target="192.168.1.1
192.168.1.4
192.168.1.10
192.168.1.199"
current=`nmap -sP 192.168.1.1-255 | sed s/.*T// | sed s/N.*// | sed s/.*t\ // | sed s/\ app.*// | sed '/^$/d'`
if [ "$current" == "$target" ]; then
    echo "No one has come online"
else
    diff=`diff <(echo "$target") <(echo "$current") | sed s/.*\>// | sed s/0a.*// | sed s/2a.*// | sed s/\ // | sed '/^$/d'`
    xmessage $diff Has come online
fi
```
Works if only one host comes online at one.

TODO:
-Make the message more aesthetically pleasing
-Make it popup only once for each host (need help with this one)


How can i make it pop up once for each host rather than popping up everytime the script is run for the same host?

---

### Post by Psycho.mario on 2009-06-01
I finished the script(well not entirely). Thanks for all your help, Here it is:
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
sleep=60
#--------------------Stop Editing---------------------#
#######################################################
while [ 1 = 1 ]
do
if [ -s /var/tmp/online ]; then
    target=`cat /var/tmp/online`
else
    target=`echo "$target"`
fi
current=`nmap -sP $ipsys-255 | sed s/.*T// | sed s/N.*// | sed s/.*t\ // | sed s/\ app.*// | sed '/^$/d'`
if [ "$current" == "$target" ]; then
    echo "" > /dev/null
else    
    diff=`diff <(echo "$target") <(echo "$current") | sed s/.*\>// | sed s/0a.*// | sed s/2a.*// | sed s/\ // | sed '/^$/d'`    
        if [ -s /usr/bin/gxmessage ]; then    
            gxmessage -center -nofocus -title "$title" -timeout $timeout "$diff"
        else
            xmessage -timeout $timeout "$diff"
        fi
fi
echo "$current" > /var/tmp/online
sleep $sleep
done
```






TODO:
-Make it run without the terminal. Suggestions?

---

### Post by prem1er on 2009-06-01
Instead of running this in an infinite loop, why not use a cron job to make this run periodically.  It would be cleaner and more efficient.

---

### Post by blueridgedog on 2009-06-01
> **Psycho.mario said:**
> TODO:
-Make it run without the terminal. Suggestions?

You have done an excellent job, and have the makings of a great bash script writer.  I want to look at it in more detail, but I have little time in the work week.  One suggestion (as another poster stated) is to run this via cron, rather than a loop.  Then you can drop the terminal as well.  I would tell the cron process to run your script once every five minutes, with something like:

Edit your crontab with:
```

crontab -e
```

Then put a line in to run your script.  The format for crontab is minute/hour/day of month/day of week then your command.

So
```

10,20,30,40,50,60 * * * /path/to/my/script
```

Will run your script every ten minutes.

---

