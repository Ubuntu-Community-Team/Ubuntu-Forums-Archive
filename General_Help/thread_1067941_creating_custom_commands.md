---
title: "creating custom commands"
date: 2009-02-12
forum: General Help
---

### Post by madhavhmk on 2009-02-12
I have written a program in C language named 'TOV.c'
Its inputs are text documents. Each time i have to run the program i have to copy the file into current directory......

I was just wondering if i can set a custom command 'tov' in the command prompt, so that i can run it from the command line from any location......

eg:
now i am doing like this:

>> gcc tov.c -lm
>>./ a.out -f eos.out

where eos.out is a file in current dir

I want to have it like this:

>>tov -f eos.out

:confused:
like we do >>acroread file.pdf 

pls help me where i  can set a custom command.......

---

### Post by Dr Small on 2009-02-12
The file that you want to execute needs to be somewhere in your $PATH. Try:
```
echo $PATH
```

---

### Post by Tibuda on 2009-02-12
If you want it to be available to all users copy it (as root) to /usr/local/bin or /usr/bin, and if you want it only for your user, copy it to ~/.local/bin (create that directory if it does not exists)

---

### Post by madhavhmk on 2009-02-12
Hey thankyou....!!!

now its working.....but there is another problem nw....

I created an a.out file by complilinf tov.c, renamed it as TOV and put it in above location.......so it is running fine as below:

>>TOV -f input.txt

but for the program, I also have an output file to be specified, which is usually created in the current directory.....but now the program is running, but the output file is not seen.....

eg:

earlier----
>>./a.out -f input.txt -o output.txt
will create a file output.txt in current dir

now----
>>tov -f input.txt -o output.txt

the file is being created in the dir /proc/7684/cwd 

how to overcome this? any ideas?

---

### Post by niteshifter on 2009-02-12
> **danielrmt said:**
> ,... copy it to ~/.local/bin (create that directory if it does not exists)

I think that should be ~/bin. Depends upon what is in a user's .profile, mine has this:

```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

---

### Post by |{urse on 2009-02-12
nvm =p

---

### Post by madhavhmk on 2009-02-12
yes....I have tried giving full path before the output file name....
its not working....

.
here contents after the tag -o is stored into a variable called output1. Then a file is created in that name.....
usually what happens is that the file is created in current directory......

but since the a.out code is now in bin, there seems to be a problem.....can't understand how it is going into proc

---

### Post by madhavhmk on 2009-02-12
ok guys....
problem solved....

my mistake to scan proc.....
file is being created in normal directory

---

