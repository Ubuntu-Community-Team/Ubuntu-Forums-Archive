---
title: "Two Pidgin on login"
date: 2008-02-27
forum: Desktop Environments
---

### Post by it.henrik on 2008-02-27
I have a strange problem I cant seem to get rid of,

When I login to my dear ubuntu box pidgin greets me with two pidgin windows.

Even if I go into system - pref.s - sessions and un/check pidgin in the list of processes that should run at startup I still have two pidgins running next time I login again.	:???:

I have had this problem since the first pidgin release and I would very much appreciate if someone could help me here.

---

### Post by it.henrik on 2008-02-28
bump

---

### Post by ifokkema on 2008-02-29
Hiya,

Did you check System -> Preferences -> Sessions?

P.S. Nice sig you got there ;)

---

### Post by it.henrik on 2008-03-02
> **it.henrik said:**
> 
Even if I go into system - pref.s - sessions and un/check pidgin in the list of processes that should run at startup I still have two pidgins running next time I login again.	:???:


Yes I have, no luck there.

I am totally clueless atm on where my pidgins comes from.:confused:


Bunny rules!

---

### Post by ifokkema on 2008-03-03
Unbelievable. I thought I'd never say this here, but ... I'm apparently to blind to read. Sorry about that :)

So does pidgin appear in that list twice everytime, or is out now, but still starts twice?
Do you have that "Automatically remember running applications when logging out" option set?
When you check the pocess list, do you see two pidgin processes running also? If so, do they have the same parent process id? Because I've been unable to get to a point where I have two pidgin windows ;) Running the application when it's already open, does not spawn a new process or a new window. If you have two separate processes, they must not know about each other somehow...

---

### Post by it.henrik on 2008-03-03
I always have two pidgins! :(

Automagically save running apps in this session on logout [check]
unmarked check box for pidgin [check]

If I mark the checkbox I will have three pidgins when I login next time :)
```

henrik@henrik-laptop:~$ ps -ef | grep pidgin
henrik    7013  6847  1 21:36 ?        00:00:01 /usr/bin/pidgin --session 117f000101000120432216400000056560003 --display :0.0
henrik    7037  6847  1 21:37 ?        00:00:01 /usr/bin/pidgin
henrik    7354  7174  0 21:38 pts/1    00:00:00 grep pidgin
henrik@henrik-laptop:~$ 

```

Where do all these pidgins come from?

---

### Post by michaelzap on 2008-03-03
> **it.henrik said:**
> 
Where do all these pidgins come from?

Pidgins are mutant rats. They are essentially the noxious rodent air force. That's why you never see baby pidgins (only full-grown ones).

When I remove Pidgin from Sessions it doesn't load at startup, so something is definitely odd. Do you have any extra plugins that might include this option? I skimmed my installed plugins and none of them do this, but that doesn't mean that none exist I suppose.

---

### Post by ifokkema on 2008-03-04
> **it.henrik said:**
> Automagically save running apps in this session on logout [check]
unmarked check box for pidgin [check]
Are you saying you HAVE selected the option that it will remember what you had running? In that case, are you logging of with Pidgin running, or do you first close Pidgin and then log off?

> **it.henrik said:**
> ```

henrik@henrik-laptop:~$ ps -ef | grep pidgin
henrik    7013  6847  1 21:36 ?        00:00:01 /usr/bin/pidgin --session 117f000101000120432216400000056560003 --display :0.0
henrik    7037  6847  1 21:37 ?        00:00:01 /usr/bin/pidgin
henrik    7354  7174  0 21:38 pts/1    00:00:00 grep pidgin
henrik@henrik-laptop:~$ 

```

Where do all these pidgins come from?
Note that the parent process ID's of the two Pidgin processes are identical (second column). They are both spawned by the same process. Do a grep on that one. So first grep pidgin, then grep on the value in the second column and see what kind of process spawned the pidgins ;)

Also, note that it's the --session 117f000101000120432216400000056560003 --display :0.0 part that allows to pidgin processes to run alongside each other...

---

### Post by it.henrik on 2008-03-05
No special plugins, and I have seen this strange behavior since I first installed pidgin.

the parent to all my pidgins is x-session-manager.

----------------------------------------------------------------

Does this mean that my pidgins used to be x-session-managers and then mutatet to rats and then to pidgins? :)

---

### Post by ifokkema on 2008-03-06
> **it.henrik said:**
> the parent to all my pidgins is x-session-manager.
This makes me believe it's really a session problem, not pidgin related... but that doesn't solve the problem, though.
If you do not tell it to remember what you had running when you log off, and you removed the pidgin processes from the startup list... what's left?
Maybe it's worth looking at your ~/.gconf/apps/gnome-session/ directory. Anything weird looking in there?

> **it.henrik said:**
> Does this mean that my pidgins used to be x-session-managers and then mutatet to rats and then to pidgins? :)
The managers probably started to experiment with drugs, turning them into vile low-life rats. Most likely, because of poisoning or nibbling on the wrong cable, they then mutated into pidgins. Probably.

---

