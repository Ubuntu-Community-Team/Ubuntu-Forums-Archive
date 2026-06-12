---
title: "bash syntax error"
date: 2009-02-13
forum: General Help
---

### Post by thunderduck3141 on 2009-02-13
Hey all,

I'm writing a bash script and I cant seem to get the syntax correct, any help would be appreciated.

Here's the script:

#!/bin/sh

COUNT=1

POTATO=0

while [ $COUNT -gt 0 ]; do

	firefox	
	let COUNT=COUNT+1

	let POTATO=POTATO+1

		if [ $POTATO -eq 50]; then

		kill -9 pid firefox

	
	fi
done


Thanks in advance,
The Duck

---

### Post by Slim Odds on 2009-02-13
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by geirha on 2009-02-13
Please put code and terminal output inside code-tags. You do that marking the part of the post that is code, and clicking on the button marked with a # symbol. Makes it much easier to read. 

I do see one syntax error, namely:
```
if [ $POTATO -eq 50]; then
```
It's picky on the spacing here, so you'll need to add a space between 50 and ].

---

### Post by thunderduck3141 on 2009-02-13
still gives me a fi found but then expected error

thanks,
the duck

---

### Post by Slim Odds on 2009-02-13
> **thunderduck3141 said:**
> still gives me a fi found but then expected error

thanks,
the duck

Did you look at the link to the Advanced Bash Scripting guide?

Also what do you think "pid" means?

Also, you probably want /bin/bash instead of /bin/sh

---

### Post by thunderduck3141 on 2009-02-13
Yes I did look at the guide, though I'm not sure what section Im looking for. I'm using pid as an arg for kill, i just firefox in as a standing for the program

---

### Post by Slim Odds on 2009-02-13
> **thunderduck3141 said:**
> Yes I did look at the guide, though I'm not sure what section Im looking for. I'm using pid as an arg for kill, i just firefox in as a standing for the program

pid is an placeholder, you need to give it the actual PID (which is a number)

---

### Post by thunderduck3141 on 2009-02-13
#!/bin/sh
COUNT=1
POTATO=0
while [ $COUNT -gt 0 ]; do
firefox
let COUNT=COUNT+1
let POTATO=POTATO+1
if [ $POTATO -eq 50 ]; then
kill -9 firefox
fi
done

this is what i have now, this is what i get now

11: Syntax error: "done" unexpected (expecting "do")

---

### Post by mcduck on 2009-02-13
Try this..
```
#!/bin/sh
COUNT=1
POTATO=0
while [ $COUNT -gt 0 ]
  do firefox
  $COUNT=`expr $COUNT+1`
  $POTATO=`expr $POTATO+1`
  if [ $POTATO -eq 50 ]
    then killall firefox
  fi
done
```
also, if you are trying to start 50 instances of Firefox you should add an ampersand after the "firefox" command. Without it, the script will stop to wait until the Firefox is stopped before continuing the next step:

```
#!/bin/sh
COUNT=1
POTATO=0
while [ $COUNT -gt 0 ]
  do firefox &
  $COUNT=`expr $COUNT+1`
  $POTATO=`expr $POTATO+1`
  if [ $POTATO -eq 50 ]
    then killall firefox
  fi
done
```
This will start Firefox in the background, allowing the script to continue without having to wait for Firefox to stop.

edit: I also used expr instead of let becasue let is only available in Bash, not Ubuntu's default shell Dash. If you want to use let instead you need to change the shebang to "#!/bin/bash" and then run the script with "./yourscript.sh" instead of "sh yourscript.sh". (Bash is used as login shell, but /bin/sh points to Dash instead..)

edit2: changed the "kill" command to "killall".

---

### Post by thunderduck3141 on 2009-02-13
that u very much mcduck

i think i might have done something wrong, i was trying to get the loop to open firefox let it sit open for 50 seconds, and the close it, and repeat until enduser send kill signal

any help would be great

the duck

---

### Post by mcduck on 2009-02-13
In that case you'll want to do something like this:

```
#!/bin/sh
while true
  do firefox &
  sleep 50
  killall firefox
done
```

"while true" makes the while loop repeat until interrupted. "firefox &" starts Firefox in the background, "sleep 50" waits for 50 seconds and then "killall firefox" closes all running instances of Firefox.

(actually even the scripts I posted above should use "killall", not "kill -9" which would expect process ID, not process name..)

---

### Post by Slim Odds on 2009-02-13
I will repeat again, kill does not take names.

It takes Process ID's (PID)

---

### Post by Slim Odds on 2009-02-13
> **mcduck said:**
> In that case you'll want to do something like this:

```
#!/bin/sh
while true
  do firefox &
  sleep 50
  killall firefox
done
```"while true" makes the while loop repeat until interrupted. "firefox &" starts Firefox in the background, "sleep 50" waits for 50 seconds and then "killall firefox" closes all running instances of Firefox.


Yes, killall will kill all 1 instance of firefox that this script will run.

---

### Post by Slim Odds on 2009-02-13
I'm not sure what you are trying to accomplish, but your script is going to have to be a bit more complex.

You might want to write it in Ruby or Python.

---

### Post by mcduck on 2009-02-13
> **Slim Odds said:**
> Yes, killall will kill all 1 instance of firefox that this script will run.

It kills *all* instances of Firefox, no matter if they were started from the script or not.. Don't be confused by the "killall" name, it's not a tool for killing multiple processes, it' a tool for killing processes by name. :)

Anyway, the only important thing in this case is that it uses process name instead of PID, which saves us from the trouble of acquiring the PID to use with "kill".

By the way, I'd recommend not using "-9" even with the "kill" command unless you really need to. Just a simple "kill" (or "kill -15", if you want) will work in most cases just as fine, and allows the process to quit properly instead of forcing it to quit immediately.

---

### Post by mcduck on 2009-02-13
> **Slim Odds said:**
> I'm not sure what you are trying to accomplish, but your script is going to have to be a bit more complex.

You might want to write it in Ruby or Python.

What makes you think so?

The script I gave does exactly what he asked for: starts Firefox, runs it for 50 seconds, kills it and repeats until the script is killed.

Definitely not a task that would require anything more than a couple of shell commands. :D

---

### Post by Slim Odds on 2009-02-13
> **mcduck said:**
> It kills *all* instances of Firefox, no matter if they were started from the script or not.. Don't be confused by the "killall" name, it's not a tool for killing multiple processes, it' a tool for killing processes by name. :)

Anyway, the only important thing in this case is that it uses process name instead of PID, which saves us from the trouble of acquiring the PID to use with "kill".

By the way, I'd recommend not using "-9" even with the "kill" command unless you really need to. Just a simple "kill" (or "kill -15", if you want) will work in most cases just as fine, and allows the process to quit properly instead of forcing it to quit immediately.

I understand how killall works. I was just pointing out that your last script only starts one firefox.

With his original script, I believe that he as trying to start a whole bunch of firefoxes. That's why I'm asking exactly what he's trying to do.

---

### Post by mcduck on 2009-02-13
> **Slim Odds said:**
> I understand how killall works. I was just pointing out that your last script only starts one firefox.

With his original script, I believe that he as trying to start a whole bunch of firefoxes. That's why I'm asking exactly what he's trying to do.
You missed one of his posts where he explains what he is actually trying to do.. ;)

> i was trying to get the loop to open firefox let it sit open for 50 seconds, and the close it, and repeat until enduser send kill signal

..and my previous post where I posted a working script to start 50 instances of Firefox and then kill them all, which is what the original script was (almost) doing.

---

### Post by Slim Odds on 2009-02-13
> **mcduck said:**
> You missed one of his posts where he explains what he is actually trying to do.. ;)

My bad. I thought that he was trying to do a crazy system stress thing.

---

### Post by mcduck on 2009-02-13
> **Slim Odds said:**
> My bad. I thought that he was trying to do a crazy system stress thing.

no problem, these forums are so active it's easy to miss updates on threads. :)

---

