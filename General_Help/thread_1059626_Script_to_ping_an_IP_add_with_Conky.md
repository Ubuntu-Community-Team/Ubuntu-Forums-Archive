---
title: "Script to ping an IP add with Conky"
date: 2009-02-03
forum: General Help
---

### Post by NuttyMonk on 2009-02-03
Hi all,

i'm trying to write a script which can be called from Conky and will ping an IP address.  If the ping is (un)successful the script should return some value to Conky which will allow me to change part of the Conky layout (just the colour of a text item basically).

I know that the script should have an "if" statement and that i'll probably have to use a "grep" to get to the part of the ping output which says how many of the pings were successfull (i'll only send 1 ping each time the script is called).  So if the ping output says 1 packet returned, it sends a true value (or something similar) and if it says 0 packets are returned it sends a false value.

Conky can then display one or other of the output text i want it to show based on the returned true or false values.

Can anyone give me some advice on this or point me in the direction of some examples/documentation/tutes which will allow me to figure this out?

Cheers

NM

---

### Post by NuttyMonk on 2009-02-03
I need to find out what the number is before the word "received" in the following text which is output from the "ping" command...

PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=64 time=0.050 ms

--- 192.168.1.100 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.050/0.050/0.050/0.000 ms

...which is why i think i need to use grep but i can't fathom it out.  is there another way to do it?

NM

---

### Post by lloyd_b on 2009-02-04
The "ping" command already returns an error code, which an "if" statement can trap to determine if the ping was successful or not.  Here's a very short script to demonstrate this:
```
#!/bin/bash

if ping -c 1 $1; then
    echo "Success"
else
    echo "Fail"
fi
```
(Note the "$1" - this refers to the first command line argument.  So if you name it "pingtest", and pass it the command line "pingtest 192.168.0.1", it will execute "ping -c 1 192.168.0.1", and print "Success" if it got a response, and "Fail" if it did not).

Lloyd B.

---

### Post by NuttyMonk on 2009-02-04
excellent, thanks for that Lloyd.  Works a treat.

Cheers

NM

---

### Post by NuttyMonk on 2009-02-04
Hi,

still got problems with this actually.

the script i'm using for conky now looks like this (the ip address is asterisked out)...

```
#!/bin/bash
if [ping -c1 ***.***.***.***]; then
    echo '${color black}${hr 2}${color}'
else
    echo '${color white}${hr 2}${color}'
fi
```

...I'm using the ${execp} command in conky to carry out the script but it only ever seems to carry out the second part of the if...else statement whether the ping to the ip address is successful or not.

If i change the color tags around, then the line which it draws is black not white.

I'm assuming that the error code which Lloyd mentioned isn't getting trapped correctly by the if...else statement.

Anyone know why this would happen and can offer me a solution?

If i remove the square brackets around the ping command i get the output of that command showing up in conky so i can see whether the packets are being received or not and the ping command itself is definitely working ok.

Cheers

NM

---

### Post by lloyd_b on 2009-02-06
First off, the "[" and "]" you are wrapping around the ping command are invoking a "test" command - that's probably why it's always evaluating to false.

If you want to suppress the output of the ping command, then redirect it to "/dev/null":

```
#!/bin/bash

if ping -c 1 $1 > /dev/null; then
    echo "Success"
else
    echo "Fail"
fi
```

Lloyd B.

---

### Post by Jose Catre-Vandis on 2009-02-08
> **lloyd_b said:**
> The "ping" command already returns an error code, which an "if" statement can trap to determine if the ping was successful or not.  Here's a very short script to demonstrate this:
```
#!/bin/bash

if ping -c 1 $1; then
    echo "Success"
else
    echo "Fail"
fi
```
(Note the "$1" - this refers to the first command line argument.  So if you name it "pingtest", and pass it the command line "pingtest 192.168.0.1", it will execute "ping -c 1 192.168.0.1", and print "Success" if it got a response, and "Fail" if it did not).

Lloyd B.

Thanks, this was also what I needed for another project :)

---

### Post by NuttyMonk on 2009-02-08
Thanks Lloyd.  Works great.

I'm gonna need to start learning a bit more about python.  It's annoying having to ask other people to solve my problems all of the time ;-)

NM

---

### Post by NuttyMonk on 2009-02-15
Is it possible to add a timeout to a ping command?

I have a ping script which is used in Conky.  If the IP is available conky updates regularly every second.  If the IP isn't available then Conky takes 4 or 5 seconds to update because the ping script is still trying to find the IP address.

If i could add a timeout of 0.5-1 second to the ping command, then Conky would continue to update regularly and the ping command would be carried out to my satisfaction as the IP i am pinging is on my local network.

Cheers

NM

---

### Post by lloyd_b on 2009-02-16
> **NuttyMonk said:**
> Is it possible to add a timeout to a ping command?

I have a ping script which is used in Conky.  If the IP is available conky updates regularly every second.  If the IP isn't available then Conky takes 4 or 5 seconds to update because the ping script is still trying to find the IP address.

If i could add a timeout of 0.5-1 second to the ping command, then Conky would continue to update regularly and the ping command would be carried out to my satisfaction as the IP i am pinging is on my local network.

Cheers

NM

"man ping" in a terminal window to see all of ping's options.  I think you want the "-W" option here - it's a timeout value.  It only works in increments of 1 second, but that should be short enough for your purpose.

So change the command to "ping -c 1 -W 1" and you should be good to go.

Lloyd B.

---

### Post by NuttyMonk on 2009-02-16
Cheers Lloyd.  You've come to my rescue again!!!  :-)

I tried "ping -help".  I didn't realise you could get more detailed definitions by doing "man ping".

Thanks again Lloyd

NM

---

