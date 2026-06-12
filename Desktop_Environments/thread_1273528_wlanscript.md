---
title: "wlanscript"
date: 2009-09-23
forum: Desktop Environments
---

### Post by newbie44 on 2009-09-23
Hi all

I have latest conky installed. all works ok, but the script below gives me this error

wlanscript.sh: line 4: [: -lt: unary operator expected
wlanscript.sh: line 7: [: -lt: unary operator expected
wlanscript.sh: line 10: [: -lt: unary operator expected
wlanscript.sh: line 13: [: -lt: unary operator expected
wlanscript.sh: line 26: [: -lt: unary operator expected

here is the script
```

#! /bin/bash
function dload()
{
    if [ $lq -lt 100 ] && [ $lq -gt 65 ]; then
    echo '${image ./pix/wlan100.png -s 94x79 -p 10,25}'
    fi
    if [ $lq -lt 66 ] && [ $lq -gt 55 ]; then
    echo '${image ./pix/wlan50.png -s 94x79 -p 10,25}'
    fi
    if [ $lq -lt 56 ] && [ $lq -gt 49 ]; then
    echo '${image ./pix/wlan40.png -s 94x79 -p 10,25}'
    fi
    if [ $lq -lt 50 ] && [ $lq -gt 5 ]; then
    echo '${image ./pix/wlan5.png -s 94x79 -p 10,25}'
    fi


}
function usage()
{
echo '${image ./pix/wlan0.png -s 94x79 -p 10,25}'
}

lq=$(iwconfig wlan0|grep 'Link Quality:'|grep : | grep --max-count=1 -o '\:\([0-9]\+\)'|grep --max-count=1 -o '\([0-9]\+\)')

if [ $lq -lt 5 ]
then
    usage
else
    dload
fi

```Re edit above. please can any one help. is anyone using this script?

---

### Post by Brandon Williams on 2009-09-23
The message is an indication that your variable is empty. With arithmetic operators, putting quotes around it probably won't help, since the variable will still be empty, and the arithmetic operator probably wants a number.

Focus on figuring out why the variable is empty. It's hard for me to tell what the problem might be due to the emoticon stuck in the middle.

FWIW, I don't use iwconfig to figure out signal quality for wireless, because it doesn't give me all the details unless I run it with sudo. If you use network manager, consider using nm-tool to get the connection information.

---

### Post by newbie44 on 2009-09-27
please can someone help. i have been trying to figure out looking at some bash scripts but cant seem to get it working

---

### Post by Brandon Williams on 2009-09-29
I suspect that your iwconfig output doesn't match what your script is expecting. Mine doesn't, and the output differs based on whether or not I run iwconfig  with sudo. Post the output from 'iwconfig wlan0' when run on the command line.

---

### Post by newbie44 on 2009-09-29
thanks [Brandon Williams]("http://ubuntuforums.org/member.php?u=744208")

I didn't use sudo

wlan0     IEEE 802.11abgn  ESSID:"**hidden**"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: **hidden**
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr off   Fragment thr=2352 B   
          Power Management off
          Link Quality=90/100  Signal level:-46 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"**hidden**"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: **hidden**
          Bit Rate=36 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr off   Fragment thr=2352 B   
          Encryption key: **hidden** [3]   Security mode open
          Power Management off
          Link Quality=100/100  Signal level:-44 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

hidden some details above

---

### Post by Brandon Williams on 2009-09-29
Try this:
```
lq=$(iwconfig wlan0 | awk -F/ '/^Link Quality=/ { gsub("Link Quality=",""); print $1; }')
```

That should work with the output produced by iwconfig on your machine.

---

### Post by newbie44 on 2009-09-29
Hi [Brandon]("http://ubuntuforums.org/member.php?u=744208")

Tried the above script, doesn't give any errors. The only image i have is from

function usage()
{
echo '${image ./pix/wlan0.png -s 94x79 -p 100,25}'
}

but other imagesdont change.. any ideas?

---

### Post by Brandon Williams on 2009-09-29
Run the script from the command line like this:
```
$ bash -x wlanscript.sh
```
That will show you the flow through the code, and should give you an idea of what's going wrong.

Also, this
```
$lq -lt 100
```
should be
```
$lq -le 100
```
to allow for the possibility of signal strength of 100%.

---

### Post by newbie44 on 2009-09-30
Hi

I get this output

bash -x wlanscript.sh
++ iwconfig wlan0
++ awk -F/ '/^Link Quality=/ { gsub("Link Quality=",""); print $1; }'
+ lq=
+ '[' ' -le 5' ']'
+ usage
+ echo '${image ./pix/wlan0.png -s 94x79 -p 100,25}'
${image ./pix/wlan0.png -s 94x79 -p 100,25}

changed -lt to -le

only get the one image

this is the script now

#! /bin/bash
function dload()
{
    if [ $lq -le 100 ] && [ $lq -gt 65 ]; then
    echo '${image ./pix/wlan100.png -s 94x79 -p 100,25}'
    fi
    if [ $lq -le 66 ] && [ $lq -gt 55 ]; then
    echo '${image ./pix/wlan50.png -s 94x79 -p 100,25}'
    fi
    if [ $lq -le 56 ] && [ $lq -gt 49 ]; then
    echo '${image ./pix/wlan40.png -s 94x79 -p 100,25}'
    fi
    if [ $lq -le 50 ] && [ $lq -gt 5 ]; then
    echo '${image ./pix/wlan5.png -s 94x79 -p 100,25}'
    fi


}
function usage()
{
echo '${image ./pix/wlan0.png -s 94x79 -p 100,25}'
}

#lq=$(iwconfig wlan0|grep 'Link Quality:'|grep |grep --max-count=1 -o '\:\([0-9]\+\)'|grep --max-count=1 -o '\([0-9]\+\)')
lq=$(iwconfig wlan0 | awk -F/ '/^Link Quality=/ { gsub("Link Quality=",""); print $1; }')

**[COLOR=Red]if [ "$lq -le 5" ][/COLOR]**
then
    usage
else
    dload
fi

as you can see I put "" round the above..

---

### Post by Brandon Williams on 2009-09-30
Run this command on the command line:
```
iwconfig wlan0 | awk -F/ '/^Link Quality=/ { gsub("Link Quality=",""); print $1; }'
```

Your debug output indicates that this is giving no output, but the awk command itself correctly parses the 'iwconfig wlan0' sample output that you previous posted.

Also, I only meant to indicate that you should modify the one use of -lt, not all of them. The rest were OK ... you were just ruling out the possibility of displaying anything if the value is 100. With the new code, you have several cases where you could print multiple lines.

---

### Post by newbie44 on 2009-09-30
Thanks brandon for all your help! this is the script below. still don't work as intended. i think i will concentrate on something else.

thanks again

#! /bin/bash
function dload()
{
    if [ $lq -le 100 ] && [ $lq -gt 65 ]; then
    echo '${image ./pix/wlan100.png -s 94x79 -p 100,25}'
    fi
    if [ $lq -lt 66 ] && [ $lq -gt 55 ]; then
    echo '${image ./pix/wlan50.png -s 94x79 -p 100,25}'
    fi
    if [ $lq -lt 56 ] && [ $lq -gt 49 ]; then
    echo '${image ./pix/wlan40.png -s 94x79 -p 100,25}'
    fi
    if [ $lq -lt 50 ] && [ $lq -gt 5 ]; then
    echo '${image ./pix/wlan5.png -s 94x79 -p 100,25}'
    fi


}
function usage()
{
echo '${image ./pix/wlan0.png -s 94x79 -p 100,25}'
}

#lq=$(iwconfig wlan0|grep 'Link Quality:'|grep |grep --max-count=1 -o '\:\([0-9]\+\)'|grep --max-count=1 -o '\([0-9]\+\)')
lq=$(iwconfig wlan0 | awk -F/ '/^Link Quality=/ { gsub("Link Quality=",""); print $1; }')


if [ '$lq -lt 5' ]
then
    usage
else
    dload
fi

---

### Post by Brandon Williams on 2009-10-01
This line:
> **newbie44 said:**
> if [ '$lq -lt 5' ]
isn't correct. You have to remove the quotes. It should be:
```
if [ $lq -lt 5 ]
```

With the quotes, it will always be true and run the usage function.

---

### Post by newbie44 on 2009-10-01
Hi

I have tried with and without quotes.

Really dont understand this. Not done any script before!

---

