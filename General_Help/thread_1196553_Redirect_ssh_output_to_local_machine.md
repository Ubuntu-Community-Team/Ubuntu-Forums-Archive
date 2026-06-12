---
title: "Redirect ssh output to local machine"
date: 2009-06-25
forum: General Help
---

### Post by WitchCraft on 2009-06-25
Hi, question:

I'm doing ipkg list on a remote machine via ssh.

Now this command lists all available packages in the ipkg repository. Fortunately, this list is rather large, unfortunately, the ssh console history cache is not, so I can only see the bottom of the list.

At the moment I pipe it to less or more, but what I want is to redirect the stdout of the "ipkg list" command to the local host machine.

I want to do something like this: 
"ipkg list @localhost> /home/username/Desktop/packages.txt" 

Is something like that possible ?

---

### Post by prshah on 2009-06-25
> **WitchCraft said:**
> 
I want to do something like this: 
"ipkg list @localhost> /home/username/Desktop/packages.txt" 


No, but you can output to a file, and then transfer the file using scp. Eg:
```
somecommand > /home/somebody/output
#now, on your machine (local), open another terminal and give the command
scp -P 22 remotemachine:/home/somebody/output ~
```

and the file will be saved in your home directory.

---

### Post by WitchCraft on 2009-06-25
> **prshah said:**
> No, but you can output to a file, and then transfer the file using scp. Eg:
```
somecommand > /home/somebody/output
#now, on your machine (local), open another terminal and give the command
scp -P 22 remotemachine:/home/somebody/output ~
```

and the file will be saved in your home directory.

Very excellent, thank you!

Note for my noobieness:
To get scp to work:
```

On Error: ash: scp: not found
ipkg install openssh 
On Error: ash: scp: not found
ln -s /opt/bin/scp /usr/bin/scp

```

---

### Post by ChrisKentfield on 2011-10-21
Using scp works, but it is possible to redirect output between remote ssh and your local machine.

[FONT="Courier New"]ssh remote.machine "ipkg list" > localfile.txt[/FONT] should work.

This can be very useful in scripts. See [http://www.nsc.liu.se/systems/ssh-tutorial.pdf](http://www.nsc.liu.se/systems/ssh-tutorial.pdf) the Executing commands remotely section for more info.

---

