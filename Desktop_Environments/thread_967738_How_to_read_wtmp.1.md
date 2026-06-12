---
title: "How to read wtmp.1?"
date: 2008-11-02
forum: Desktop Environments
---

### Post by dgermann on 2008-11-02
Hi--

How do I open and read a wtmp.1 file?

Thanks!

---

### Post by cantormath on 2008-11-02
It is login and logout info if I recall.  Look at it with vi or more the file in terminal.  
Its gonna look like a  bunch of hex data so it wont make sense.

---

### Post by dgermann on 2008-11-02
cantormath--

Thanks for helping me so quickly!

Yes, that is the question, isn't it--how to make it humanly readable! Any thoughts on that?

---

### Post by dgermann on 2008-11-02
Hi--

Just answered my own question:
```
:/var/log$ last -f wtmp.1
```

---

### Post by paco_moreno on 2009-03-27
/usr/sbin/dump-utmp /var/log/wtmp.1

---

### Post by dgermann on 2009-03-28
paco_moreno--

Thanks! Guess there is always another way to do something under linux, huh?

I would have to install dump for that to work....

Thanks!

---

### Post by jasonkirk2006 on 2010-03-23
Hi,

I'm trying to do the same thing but your snippets give nothing!

Could you please explain how did you use them to read these binary logs?

```
$ /usr/sbin/dump-utmp /var/log/wtmp.1
bash: /usr/sbin/dump-utmp: No such file or directory
```

```
$ :/var/log$ last -f wtmp.1
bash: :/var/log$: No such file or directory
```

---

### Post by VernonA on 2010-03-23
I would suspect that if the thread doesn't help you at all, you will struggle with understanding a hex dump even if we explain how to get one.
Hopefully you noted that Doug mentioned he would have to install the dump command. Did you do the same? If you didn't, then that would be a simple explanation for why it didn't work.
Also, most shell users set their terminals up so that their prompt includes information on their current directory. Eg when I first start a terminal, my prompt shows:
```
/home/vernona>
```
(I prefer to use a > to a $ as my end-of-prompt marker.) When someone says type:
```
:/var/log$ dump abc
```
they mean "cd to directory /var/log/ and use the dump command on the file abc". This is standard Unix-speak. Another convention is that if you need to run a command as root, change the $ to a #, as the root user commonly uses a # at the end of his prompt to distinguish him from a regular user.

---

### Post by jasonkirk2006 on 2010-03-23
> **VernonA said:**
> I would suspect that if the thread doesn't help you at all, you will struggle with understanding a hex dump even if we explain how to get one.
Hopefully you noted that Doug mentioned he would have to install the dump command. Did you do the same? If you didn't, then that would be a simple explanation for why it didn't work.
Also, most shell users set their terminals up so that their prompt includes information on their current directory. Eg when I first start a terminal, my prompt shows:
```
/home/vernona>
```
(I prefer to use a > to a $ as my end-of-prompt marker.) When someone says type:
```
:/var/log$ dump abc
```
they mean "cd to directory /var/log/ and use the dump command on the file abc". This is standard Unix-speak. Another convention is that if you need to run a command as root, change the $ to a #, as the root user commonly uses a # at the end of his prompt to distinguish him from a regular user.

Hi VernonA. Thanks for great explanation. I thought i knew linux. I think i'm used to out-of-the-box settings for shell ($ and # notation). It just looked like a command rather than a prompt.

Anyway... no ending for learning.

---

### Post by Cfossy2 on 2012-03-09
I did the commands, and added a re-direction to create a text file, which I could then read in my favoiurite text editor.I used the following code:
/var/log/wtmp.1 >>wtmp.txt


Then I could openit up with a text editor.Hope this helps.

---

