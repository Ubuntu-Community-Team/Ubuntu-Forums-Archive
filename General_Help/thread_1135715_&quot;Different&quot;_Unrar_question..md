---
title: "&quot;Different&quot; Unrar question."
date: 2009-04-24
forum: General Help
---

### Post by Loogworld on 2009-04-24
I have a total of five unique passwords, all of them are alpha numeric. My rar is password protected with multiple uses of these passwords, moreover I used more than one password  however I do not know which ones or what order I used. I have a 5 page list of every permutation of my passwords, this means every combination from one password in length, to five passwords in length. I am sure the password I need is in this list.

My question is, how can I implement the automation of a rar crack command, with the specific list of passwords I have. My first attempt left me with;

```
sudo su
(unrar x -p'line1' MYRAR.rar &) ; (unrar x -p'linen' MYRAR.rar &) 
```

However, typing every command would be as useful as testing all of the passwords manually.

Also, there is no way I can use a brute force attempt, though I know the characters, my password is likely 30+ characters long.

I would love ANY ideas.
Thank you in advance for your time and help.

--Zachary Fisher

---

### Post by mali2297 on 2009-04-24
Write the candidate passwords on separate lines in a file called foo.txt (say). Then, to try every two-word permutation, use the command
```

for i in $(cat foo.txt); do for j in $(cat foo.txt); do unrar x -p"$i$j" MYRAR.rar; done; done;

```
To try three-word permutations, add another loop...
```

for i in $(cat foo.txt); do for j in $(cat foo.txt); do for k in $(cat foo.txt); do unrar x -p"$i$j$k" MYRAR.rar; done; done; done;

```
and so on.

---

### Post by Loogworld on 2009-04-24
I may not understand, if so I'm sorry.

I already have all of the permutations, so that's not a problem. What I wanted to do was find a way to try 5 pages of passwords in succession. For example if my password document was psswd.xml,

```
 unrar x psswd.xml MYRAR.rar
```I understand the previous command is incorrect, but I was just looking for something similar. I expect that the solution, if any, will require the intervention of a third party application.

Sorry for the inconvenience and thank you for the help!

--Zac Fisher

---

### Post by mali2297 on 2009-04-24
Well, if you have the permutations alone on separate lines in foo.txt, then you should be able to use one loop:
```

for i in $(cat foo.txt); do unrar x -p"$i" MYRAR.rar; done;

```

If the permutations are scattered among xml tags, then you will have to extract them first somehow.

---

### Post by Loogworld on 2009-04-24
Perfect!

I misunderstood you initially, sorry about that. It worked flawlessly.

Thank you very much for your time.

-Zac Fisher

---

