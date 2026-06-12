---
title: "terminal color problem"
date: 2009-10-25
forum: Desktop Environments
---

### Post by tnvkrishna on 2009-10-25
hi all
i have recently installed ubuntu 9.10 on my laptop.
i should appreciate the ubuntu team for their constant
improvement over the previous ubuntu releases.

I have been facing this problem from the time i have started using linux.
If i type a command that gives more than a screenful of output .. trying to locate the position in terminal where the output actually started is pretty 
agonizing, because everything appears in black including my 

"username@computer-name "
and the 
"output of command" 
so i could not easily find out exactly where i have typed the command.
Is there any way to change the color of username@computer-name ..?
(linux mint does have it by default)
any help is appreciated

regards

---

### Post by sisco311 on 2009-10-25
edit the ~/.bashrc file and uncomment(remove the #) the *#force_color_prompt=yes* line.

you can also pipe the output of the command to less or more:
```
command | less
command | more

```

or clear the terminal screen before you run the command:
```
clear
```

---

### Post by tnvkrishna on 2009-10-26
thanks that solved the problem.

---

