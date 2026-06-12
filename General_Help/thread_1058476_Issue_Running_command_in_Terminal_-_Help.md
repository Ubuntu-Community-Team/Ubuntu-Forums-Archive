---
title: "Issue Running command in Terminal - Help"
date: 2009-02-02
forum: General Help
---

### Post by kmatousek on 2009-02-02
I've been trying to add some plugins to Compiz -  I understand why I have to use -sudo in the Terminal, but a lot of instructions I'm following ask to run:

cd ~/[folder]

After running the above, I recieve:

Could not open location 'file:///home/logan/cd%20~/[folder]'

The location or file could not be found.


What am I missing?

Thanks,

---

### Post by Crafty Kisses on 2009-02-02
The Terminal is case sensitive, remember that. So type it exactly as the file reads.

---

### Post by mmitt on 2009-02-02
Or you can just drag the file into the terminal prompt. After you type cd of course.

---

### Post by kmatousek on 2009-02-02
in most cases I am copying and pasting because of previous instructions.  In my most recent case I followed these commands:

mkdir -p  ~/compiz/

cd ~/compiz

Received the error mentioned above.

---

### Post by matthew.ball on 2009-02-02
The tilde (~) *is* your home directory.

So, ~/Documents is equivalent to /home/logan/Documents.

Judging from the error, it looks almost as if you are typing cd cd ~/[folder], where the %20 in the error is the space between cd and the tilde. (So it is thinking cd%20~ is a directory itself).

When you open a terminal, chances are you will be presented with your home directory straight off (logan@<comp_name>:~$), so you should just be able to go cd [folder].

I think.. I hope this makes sense.

---

### Post by kmatousek on 2009-02-02
Should I be able to run:

cd


without receiving that error?

Thanks

---

### Post by kmatousek on 2009-02-02
> **matthew.ball said:**
> The tilde (~) *is* your home directory.

So, ~/Documents is equivalent to /home/logan/Documents.

Judging from the error, it looks almost as if you are typing cd cd ~/[folder], where the %20 in the error is the space between cd and the tilde. (So it is thinking cd%20~ is a directory itself).

When you open a terminal, chances are you will be presented with your home directory straight off (logan@<comp_name>:~$), so you should just be able to go cd [folder].

I think.. I hope this makes sense.

Bingo.  Thank you.

---

