---
title: "Mathematica 5.2 trouble"
date: 2008-03-10
forum: Education &amp; Science
---

### Post by Stochastics on 2008-03-10
Hi everyone,

I just installed Mathematica 5.2 on Ubuntu 7,10. When i start Mathematica, i see the notebook but i see nothing when i type something...any suggestions ?

Stochastics

---

### Post by vegetali on 2008-03-12
I have been using mathematica 4 (in kde) and 5, 5.2, 6, 6.01 (in fluxbox and ubuntu gnome) with no problems at all.

Try this:
- open a terminal

- run the "math" command (i.e., type "math" on the command line and press "enter"). This command runs mathematica in the terminal, and does not lauch the graphical user interface.

-you should get a message like this

Mathematica 5.2 for Linux
Copyright 1988-2007 Wolfram Research, Inc.
In[1]:= 


-In[1]:= means the you can enter an input. Try any operation, let's say 2+2. Namely type in the terminal "2+2" and press "Enter". You should get something like this  
In[1]:= 2+2
Out[1]= 5
In[2]:= 

No, I am joking. I expect something like this:
In[1]:= 2+2
Out[1]= 4
In[2]:= 

If this works fine, the installation was ok and you only need to install the right fonts. I do not know which fonts mathematica 5.2 uses, but you may try to run "sudo fc-cache -f -v" to update the fonts, if mathematica installed some new ones itself.

in any case, you can use the non graphic version until you solve the problem.

---

### Post by Stochastics on 2008-04-06
I just found a workaround for this problem. To be able to see what i write on the Mathematica notebook, i need to set to normal the visual effects in System->Preferences->Appearence. 

Stochastics.

---

### Post by slimdog360 on 2008-04-08
can I ask if your name choice was just something random?

---

