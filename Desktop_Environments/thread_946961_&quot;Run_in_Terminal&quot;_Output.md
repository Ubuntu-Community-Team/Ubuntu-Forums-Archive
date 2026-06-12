---
title: "&quot;Run in Terminal&quot; Output"
date: 2008-10-13
forum: Desktop Environments
---

### Post by Craig73 on 2008-10-13
Hi,

I have a simple shell script (foobar.sh) that just touches a bunch of file names.  If I open a terminal and run the script, I see the output from the script.  If I double click on the script in Nautilus and select "run in terminal" I see no output.  (At first I assumed it was going by too quick and changed the terminal defaults to keep the terminal window open, but still no output)

Should I be expecting to see output here?

[I'm running Nautilus 2.24.0 in Intrepid, but I posted here because I remember it also not working in Hardy]

---

### Post by caljohnsmith on 2008-10-13
I've never been able to get the "run in terminal" feature to work the way I want it, so if I want to run my shell scripts in a terminal from the launcher, I do it with:
```
gnome-terminal -x bash -c "script.sh;read -n1"
```
Note the "read -n1" will make it so the terminal will stay open until you press any key. Try experimenting with it with something simple like:
```
gnome-terminal -x bash -c "free;read -n1"
```
And you'll see what I mean. Would something like that work for you?

---

### Post by Craig73 on 2008-10-14
> **caljohnsmith said:**
> 
And you'll see what I mean. Would something like that work for you?

I tried that, it seems to give me what I want with the Free command. Although trying it with my script there is still no output.

I'll play around with this and see how far I can get.

Thanks.

---

### Post by elmu.edana on 2008-11-09
> If I double click on the script in Nautilus and select "run in terminal" I see no output.

I had this problem randomly. So far it didn't occur anymore after I put ```
sleep 1
``` or ```
read
``` at the end of my scripts. Seems the output isn't captured when the script terminates too early.

[SIZE="1"](intrepid, gnome)[/SIZE]

---

