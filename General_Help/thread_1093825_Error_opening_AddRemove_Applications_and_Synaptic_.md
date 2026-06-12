---
title: "Error opening Add/Remove Applications and Synaptic Package Manager"
date: 2009-03-11
forum: General Help
---

### Post by Mrbill86 on 2009-03-11
Hey guys, I recently got ubuntu after windows got corrupted, and I've slowly been learning my way around it and having fun.  But, all of a sudden, whenever I try to open either Add/Remove Applications or Synaptic Package Manager: it starts, the window is greyed out and everything freezes, it closes without an error message, and the computer resumes as if nothing happened.  I'm wondering if there is just some error in the program and if there is any way to fix it... anything helps.  I have Intrepid Ibex if that changes what I need to do in any way.

---

### Post by MaxIBoy on 2009-03-11
That's odd. It shouldn't do that. 

Pull up a terminal (applications > accessories > terminal.) Type in "gksudo synaptic" and hit enter. Does it still crash? If it does, could you copy and paste whatever appears in the terminal?

---

### Post by Mrbill86 on 2009-03-12
Okay, I entered it into the terminal, it opened after about a minute of everything being frozen, froze again, then closed...

nothing but the "gksudo synaptic" was in the terminal

I'm starting to wonder if it could mean my hard drive is physically going bad because it makes this weird sound whenever it freezes, then goes away as soon as it starts working again

---

### Post by MaxIBoy on 2009-03-12
Okay, try this command:
```
gksudo synaptic; dmesg -more > ~/some_text_file.txt
```
Dmesg is a command that outputs diagnostic information. Look through the text file that has been created, and see if you can find anything that mentions synaptic or a crash/error.

---

### Post by Mrbill86 on 2009-03-12
I entered that and this is what the terminal said:

```
******@Laptop:~$ gksudo synaptic; dmesg -more > ~/some_text_file.txt
dmesg: invalid option -- 'm'
Usage: dmesg [-c] [-n level] [-s bufsize]

```

---

### Post by hep-basak on 2009-07-06
Hi guys, please help me. That command doesnot work.After writing this command "gksudo synaptic; dmesg -more > ~/some_text_file.txt" I got these lines five minutes later. 

dmesg: invalid option -- m
Usage: dmesg [-c] [-n level] [-s bufsize]
hep-basak@basak:~$ 

I am about to lose my mind :((. &#304;s there anyone who can solve these problem. I waiting your replys...

Thank you in advance

---

### Post by michy99 on 2009-07-06
You are more likely to get help if you start a new thread instead of replying to one that is almost four months old.

Start a new thread with a descriptive title and a good description of what is going wrong and you will probably get help.

---

