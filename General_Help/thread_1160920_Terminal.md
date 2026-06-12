---
title: "Terminal"
date: 2009-05-16
forum: General Help
---

### Post by DeMus on 2009-05-16
I just opened a terminal window and type an instruction. After entering it said I made a typo, so I used the up-arrow to return to the previous instruction.
I pushed the up-arrow again and saw an instruction I had used in a previous terminal window, which has been closed for some hours.
So I kept pushing the arrow button and it looks like I can go back in history till the day I installed Jaunty.
Questions: Is this normal? Isn't every terminal window a stand alone process? How about if I have used sudo and type my password? Will it stay open all the time?
Who can help me with this?

---

### Post by lloyd_b on 2009-05-16
> **DeMus said:**
> I just opened a terminal window and type an instruction. After entering it said I made a typo, so I used the up-arrow to return to the previous instruction.
I pushed the up-arrow again and saw an instruction I had used in a previous terminal window, which has been closed for some hours.
So I kept pushing the arrow button and it looks like I can go back in history till the day I installed Jaunty.
Questions: Is this normal? Isn't every terminal window a stand alone process? How about if I have used sudo and type my password? Will it stay open all the time?
Who can help me with this?

Yes, this is normal.  History is stored for the *user*, not the specific terminal window session.

I'm not sure what you're worried about with regard to sudo.  The *password* is input to the sudo program, so it is NOT stored in your shell history.  And sudo times out after 15 minutes without a sudo command, forcing you to enter your password again if you execute another sudo...

Lloyd B.

---

### Post by DeMus on 2009-05-16
> **lloyd_b said:**
> Yes, this is normal.  History is stored for the *user*, not the specific terminal window session.

I'm not sure what you're worried about with regard to sudo.  The *password* is input to the sudo program, so it is NOT stored in your shell history.  And sudo times out after 15 minutes without a sudo command, forcing you to enter your password again if you execute another sudo...

Lloyd B.

Thanks for your answer. Yes, I should have known that about the password. I was just wondering since I never seen before that the history is kept alive.
Why is that? Why not store it per session and once the terminal window is closed the history is emptied again? Does it make sense to know what you type a month ago?

---

### Post by WatchingThePain on 2009-05-16
I think there is probably a way customise all of that.
Variables are used to control how bash uses history files.

When the shell is started HISTFILE defaults to ~/.bash_history.
HISTFILESIZE is the amount of lines used for the history stack.
500 is the default usually.

---

### Post by mali2297 on 2009-05-16
The history is by default saved in the file ~/.bash_history when you quit a terminal session. If you don't want to save the history, put this line in the file ~/.bashrc or ~/.bash_profile:
```

export HISTFILE=""

```

---

### Post by sahabcse on 2009-05-16
history -c

---

### Post by lloyd_b on 2009-05-16
> **DeMus said:**
> Thanks for your answer. Yes, I should have known that about the password. I was just wondering since I never seen before that the history is kept alive.
Why is that? Why not store it per session and once the terminal window is closed the history is emptied again? Does it make sense to know what you type a month ago?

The "one history file per user" is a default, which can be modified quite easily.

For instance, add the following line into your "~/.bashrc" file:```
export HISTFILE="~/.bash_history."`date +%m%d%H%M%S`
``` and it will create a new history file each time bash is run, with the history file being ".bash_history.MMDDHHMMSS" (Month, Day, Hours, Minutes, Seconds).  This will allow for a separate history file for each terminal window (unless by some chance you start two of them on the same second - it would probably be better to do this via PID rather than date/time...).

The only problem with this is that you'll wind up with many ".bash_history..." files, so if you do something like this, add the line ```
rm $HISTFILE
``` at the end of the file "~/.bash_logout" to delete these files when the terminal window exits.

As to whether it makes sense to have history going back a month (or more), it depends on the user.  If a person uses the terminal only rarely, and then to always run the same small set of commands, then it would make sense.  But for other users, who use a much larger set of commands, then maybe not.

Lloyd B.

Edit: I should have read the other posts more thoroughly - mali2297's suggesting of just setting "HISTFILE" to null achieves the same effect, with a lot less convolutions.

---

