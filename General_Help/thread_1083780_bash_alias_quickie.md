---
title: "bash alias quickie"
date: 2009-03-01
forum: General Help
---

### Post by mcai8sh4 on 2009-03-01
Alrighty, I'm trying to sort out a couple of quick alias' (maybe I'd be better with a little script, but...)

I'm tending to work on things for a few days until I  get them right, therefore everytime I log in I'm changing to a certain dir often, then once I'm finished with that project, I'm changing to a diff dir. (Hope this makes sense)

SO... what I'm trying to do is this :
1) setup a command to save the current working directory to a text file.
2) set up another command to then go to the directory stored in the file.

I've done the above like so..

1)```
alias cd+='pwd > ~/bin/current_work.txt'
```

therefore, I navigate to my current working dir and type "cd+"
This works.

2)```
alias cd..='cd "$(cat ~/bin/current_work.txt)"'
```
then whenever I type "cd.." (not to be confused with "cd ..") I change to the dir where my current work is stored.
This works too.

BUT, if the current dir contains spaces (ie ~/Code/temp sensor/) then it just replies "No such file or directory"

I've tried changing the space to \ . (there is a space after the \) but this doesn't work. To do this I've used sed, because I like it...
```
alias cd+='pwd | sed -es"/ /\\\ /g" > ~/bin/current_work.txt'
```

But that doesn't work either.

I realise this is like pushd/popd but slightly less temporary.

Any help appreciated, thanks for your time!

-s

---

### Post by heindsight on 2009-03-01
> **mcai8sh4 said:**
> 
1) setup a command to save the current working directory to a text file.
2) set up another command to then go to the directory stored in the file.

I've done the above like so..

1)```
alias cd+='pwd > ~/bin/current_work.txt'
```

therefore, I navigate to my current working dir and type "cd+"
This works.

2)```
alias cd..='cd "$(cat ~/bin/current_work.txt)"'
```
then whenever I type "cd.." (not to be confused with "cd ..") I change to the dir where my current work is stored.
This works too.

BUT, if the current dir contains spaces (ie ~/Code/temp sensor/) then it just replies "No such file or directory"


I just did exactly what you described, ie (EDIT: I used a different file to store the directory, but that shouldn't make a difference):
```
alias cd+='pwd > ~/cw.txt'
alias cd..='cd "$(cat ~/cw.txt)"'
```

I then did:
```
mkdir ~/foo\ bar
cd ~/foo\ bar
cd+

```

After this, doing
```
cd..
```
from anywhere in my filesystem, takes me to ~/foo\ bar.

In other words, it works, even with a space in the directory name. Perhaps you should check the quoting in your alias definition of cd.. again.

---

### Post by mcai8sh4 on 2009-03-01
ok, for what it's worth (it may be useful to someone else!?)

I've played around and it now works, I changed it a few times, so probably just confused myself initially. these now work :

```
alias cd+='pwd  > ~/bin/current_work.txt'
alias cd..='cd "$(cat ~/bin/current_work.txt)"'
```

---

### Post by heindsight on 2009-03-01
> **mcai8sh4 said:**
> ok, for what it's worth (it may be useful to someone else!?)

I've played around and it now works, I changed it a few times, so probably just confused myself initially. these now work :

```
alias cd+='pwd  > ~/bin/current_work.txt'
alias cd..='cd "$(cat ~/bin/current_work.txt)"'
```

Congratulations ;)

It occurs to me that your problem may have been with the existence of the file where your cd.. alias was looking for the dir to cd to. If that file doesn't exist, you'll get an error. Did you perhaps change the name of the file you use?

---

