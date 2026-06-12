---
title: "Why doesn't mprime start when typing 'mprime' from the terminal?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Mikael on 2006-06-03
I want to do some stability testing on my newly assembled Linux box. I was going to use mprime, but I can't start it from the terminal. I can start it with an app launcher from the desktop, but then I don't get any printout on the progress of the torture test. When I try to launch it from the terminal, standing in the mprime directory and issuing the command *mprime*, I get the following message:

bash: mprime: command not found

I'm more or less a complete newbie on Linux, so it's quite likely that I'm missing something here.

---

### Post by Jussi Kukkonen on 2006-06-03
working directory is not normally included in the path on Unix (for security reasons). Try with:
```
./mprime
```
if that is the name of the executable.

---

### Post by Mikael on 2006-06-04
Thank you! Worked like a charm. :D

---

### Post by Ted_Smith on 2006-10-06
That doesn't work for me? I get :

bash: ./mprime: No such file or directory

I've also run chmod x-a mprime to make it executable. Still no luck?

Can anyone help? It's listed as a green file when I run ls which meaqns that it's executable? 

Ted

---

### Post by kwalo on 2006-10-06
You must type```
chmod u+x mprime
```Make sure, that mprime file is in directory you're in.

---

### Post by Ted_Smith on 2006-10-06
Apologies. I had already done that. The problem was I'd downloaded the FreeBSD version by mistake which is why it didn't work. I went back and downloaqded the proper version and it worked like a charm! 

Cheers

Ted

---

### Post by Huzudra on 2008-01-26
how would one run 2 instances?  one per core?  in windows i just rename the exe slightly and 2 instances are allowed to run.  same for ubuntu?

---

