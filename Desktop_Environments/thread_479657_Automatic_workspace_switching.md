---
title: "Automatic workspace switching?"
date: 2007-06-20
forum: Desktop Environments
---

### Post by rhythminmind on 2007-06-20
Anyone know of a app or way to have the workspace switch automatically at a set interval?
I want the workspace to switch every 10 sec's.

---

### Post by tgm4883 on 2007-06-20
Why?

---

### Post by diatribe on 2007-06-20
this does seem like a very odd request, what is your goal?

---

### Post by rhythminmind on 2007-06-20
I have setup a system to monitor a few servers & has a vnc client .  I want to have a different vnc session on each workspace & have the workspaces cycle. It would be a good visual que for the non admin types that i work with that a server is down.

---

### Post by rhythminmind on 2007-06-21
I'm surprised something like this hasn't been done. With all the cool desktop effects available i would of thought this would of been done years ago.

---

### Post by thelinuxguy on 2007-06-21
```

sudo apt-get install wmctrl

```

SwitchWorkspace.sh
```

numberOfDesktops=4

for (( ; ; ))
do
        for (( i = 0; i < $numberOfDesktops; i++ ))
        do
                wmctrl -s $i
                sleep 10s
        done
done

```

Regards,
thelinuxguy

---

### Post by rhythminmind on 2007-06-21
Thank you.. i'll give it a shot..

---

### Post by rhythminmind on 2007-06-21
How should i run this script? Do i keep it in my home directory?

---

### Post by thelinuxguy on 2007-06-21
Home directory is fine.
Make the script executable and run it using the following commands
```

chmod u+x SwitchWorkspace.sh
./SwitchWorkspace.sh

```

---

### Post by rhythminmind on 2007-06-21
Nice.. Works great.. Thanks again.. Really helps

---

### Post by thelinuxguy on 2007-06-22
> **rhythminmind said:**
> Nice.. Works great.. Thanks again.. Really helps

You are welcome. Consider marking this thread as resolved. Helps others with similar questins.

---

### Post by mtn on 2007-06-24
This looks like what I'm looking for, but when I run the script I get...

```
ggh@ggh-desktop:~/Desktop$ sudo ./switchdesktop.sh
./switchdesktop.sh: 3: Syntax error: Bad for loop variable
```

Any ideas? Thanks

---

### Post by thelinuxguy on 2007-06-24
Umm.... The script is running at my end as expected.
Did you modify anything in the script?

---

### Post by mtn on 2007-12-06
I have just come back to this (after ages) and it works fine now (I have reinstalled and upgraded since). What I would really like is a script, or something, that spins the desktop cube when Compiz-Fusion is on. This script worksto change desktops when Compiz is of, but won't spin the cube - I guess that is something to do with wmctrl and the windows managers it supports!

Any ideas?

---

