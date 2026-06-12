---
title: "Telnet in a bash script"
date: 2009-04-22
forum: General Help
---

### Post by smileboot on 2009-04-22
Hi im trying to write a bash script and since im completly new to it i need a little help.

I am trying to convert this windows batch script

```

rem echo off
:start
rem ------------------------------------------------
ping 192.168.20.81 -n 1 -w 1 >NUL
IF ERRORLEVEL 1 goto start

rem putty
rem ------------------------------------------------
break
putty.exe [telnet://192.168.20.81:9000](telnet://192.168.20.81:9000) -m redboot.txt
exit

```I managed to make this which works fine

```

#!/bin/bash
echo
echo ""
echo "Enter hostname or ip address: " 
read host
while true
do
    if eval "ping -c 1 -s 1 $host" > /dev/null; then       
    echo "Router Awake"
    putty telnet://$host 9000 -m redboot.txt
        break
    else
        echo "Waiting for Redboot to boot. Press CTRL + C to quit"
     sleep 1
    fi
done

```But i dont like that it uses putty. im trying to make it use telnet command which is as easy as using telnet $host 9000. but the -m redboot.txt makes putty send a ^C when it connects. which im having difficulty doing with the plain telnet command. Any help appreciated.

---

### Post by Anthon on 2009-04-22
I would start with trying to do:
  telnet $host 9000 < redboot.txt
and make sure the ^C is explicit in the file. 

I don't think many people can read the  Waiting.... prompt and react with in the 1 second sleep time. Do you really want to have that so short?

---

### Post by Yashiro on 2009-04-22
ssh is usually used for this, not telnet.

---

### Post by smileboot on 2009-04-22
it has to be telnet and yes the short time is necessary. Literally have to connect to the device before it launches a script after being on for 1 second.

Just so you know the script pings the ip untill it gets a respone then it connects via telnet and send that command.

---

### Post by smileboot on 2009-04-22
Bump

---

### Post by KyleBrandt on 2009-04-22
More information, such as what is in redboot.txt might help (also, I don't know what -m does exactly for putty).  However, maybe you want something like:
```

# -e sets the escape character, for < <() read about process substitution.
telnet $host 8000 -e . < <(echo .)

```

-Kyle

---

### Post by smileboot on 2009-04-22
as i said all -m redboot.txt does is when connected send ^C.

All that is contained in the txt file is ^C. So i assume all -m does is read txt files and executes/sends to remote host.

-e i believe only sets the escape key it does not send it to the remote host. typing "send escape" (i think) once connected to a host in telnet sends ^C or specifically an escape.

---

### Post by KyleBrandt on 2009-04-22
Oh ... I think I might see what you are saying. Maybe you want:

```
 echo -e "\c" | telnet $host 8000
```

?

---

### Post by defaria on 2009-04-22
> **smileboot said:**
> it has to be telnet and yes the short time is necessary. Literally have to connect to the device before it launches a script after being on for 1 second.

Just so you know the script pings the ip untill it gets a respone then it connects via telnet and send that command.

In a word - see expect(1).

---

### Post by Slim Odds on 2009-04-22
> **defaria said:**
> In a word - see expect(1).

That's **exactly** what I was going to say......

---

