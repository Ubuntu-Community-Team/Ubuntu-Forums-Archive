---
title: "Script help: checking IP"
date: 2009-06-01
forum: General Help
---

### Post by Psycho.mario on 2009-06-01
I wrote myself a script which tells me what hosts on my network come online:
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
#--------------------Stop Editing---------------------#
#######################################################
while [ 1 = 1 ]
do
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
done
```I have two questions:

-Because of the way i wrote it, the next time it is run it shows up the same IP's it did on the last run (if the hosts are still up). How can i make it so that it only pops up when a NEW host comes online, with out completely changing the code?

-How can i turn this into an executable (the equivilent of the windows  bat2exe) and run it as a daemon. Meaning it is always looping in the background and notifies me whenever a new host comes online.

Thanks in Advance

---

### Post by iponeverything on 2009-06-01
I would write out the last known state to a file in /var/tmp or somewhere and then just output a positive if does not appear in the file -- before rewriting the file with the new state.

---

### Post by Psycho.mario on 2009-06-01
How could I include that?

---

### Post by Psycho.mario on 2009-06-01
I did it:
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

---

