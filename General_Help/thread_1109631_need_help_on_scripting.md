---
title: "need help on scripting"
date: 2009-03-28
forum: General Help
---

### Post by Walter Melon on 2009-03-28
I'm writing this program and it's supposed to be silent while the laptop is plugged in, but as soon as its unplugged it plays a song until I type in my password.

But all it does is play; regardless of if its plugged in or not. 

```

#! /bin/bash
#laptop alarm - ac_power detect

export power="state: on-line"
export state=$(cat /proc/acpi/ac_adapter/ADP1/state)
gnome-screensaver-command --lock

for ((i=100;i=115;i+=1)); do
export state=$(cat /proc/acpi/ac_adapter/ADP1/state)
if [ "$state" != "$power" ]
then
totem ~/Desktop/siren.mp3
fi
done
```

Any help is appreciated. Thank you

---

### Post by DGortze380 on 2009-03-29
> **Walter Melon said:**
> I'm writing this program and it's supposed to be silent while the laptop is plugged in, but as soon as its unplugged it plays a song until I type in my password.

But all it does is play; regardless of if its plugged in or not. 

```

#! /bin/bash
#laptop alarm - ac_power detect

export power="state: on-line"
export state=$(cat /proc/acpi/ac_adapter/ADP1/state)
gnome-screensaver-command --lock

for ((i=100;i=115;i+=1)); do
export state=$(cat /proc/acpi/ac_adapter/ADP1/state)
if [ "$state" != "$power" ]
then
totem ~/Desktop/siren.mp3
fi
done
```

Any help is appreciated. Thank you

I may be missing something, but it looks like you have a logical error in the conditions of your loop. Can you please explain what you would like the for loop to do??

---

### Post by Walter Melon on 2009-03-29
I run the program and if it gets unplugged, the siren goes off.  The for loop is supposed to run indefinitely until I kill the program.

---

### Post by DGortze380 on 2009-03-29
> **Walter Melon said:**
> I run the program and if it gets unplugged, the siren goes off.  The for loop is supposed to run indefinitely until I kill the program.

ok, I think it should be infinite, but may I suggest something a bit clearer...

```

while ((true)); do

done

```

# or

```

for ((x=1;x>0;x++)); do

done

```

Looking at the rest now, been a while since I've written in BASH, sorry.

---

### Post by DGortze380 on 2009-03-29
Ok, here's what I can tell you...

line 1:  export power="state: on-line"
Works Fine

EDIT!!
line 2: export state=$(cat /proc/acpi/ac_adapter/ADP1/state)
On my system, this should be /proc/acpi/ac_adapter/AC/state)

Check this outside your script with: cat /proc/acpi/ac_adapter/ADP1/state

You may have a formatting issue. The output on my machine from this command has two or three tabs after the colon. power would have to have the same for the if to work correct

```

state:            on-line

```

line 3: gnome-screensaver-command --lock
I can't check this, no GUI

line 5: for loop is infinite

line 7: if statement works correctly

line 9: totem ~/Desktop/siren.mp3
I can't check this, no GUI

---

### Post by fixitdude on 2009-03-29
awk '{print $2}'

Prints the second thing on the line.

I don't know why you are using "export", see below. (yea, it's thrown together, how much time do you want me to spend on this for free?)

power="state: on-line"
echo $power
state: on-line

whatever=`echo $power | awk '{print $2}'`
echo $whatever
on-line

Now try the "if" statement, but I would compare it with just the word, not another variable.

---

### Post by Walter Melon on 2009-03-29
> **DGortze380 said:**
> ok, I think it should be infinite, but may I suggest something a bit clearer...

```

while ((true)); do

done

```

# or

```

for ((x=1;x>0;x++)); do

done

```

Looking at the rest now, been a while since I've written in BASH, sorry.

I changed the for loop to while and I had the same problem.  I added three tabs to ```
state: on-line
``` and it works perfectly now. 
Thank you so much for your help.

---

