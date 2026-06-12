---
title: "[SOLVED] Create Terminal Command for Matlab"
date: 2008-09-04
forum: Education &amp; Science
---

### Post by pasQualle on 2008-09-04
Hey guys,

I don't know exactly if this is really a MatLab related question, or if you can solve it with a little linux experise (I'm learning every day I'm sitting in front of this machine, but with that I need your help.).

I've installed Matlab in /opt and created a starter with executes opt/matlabr2007a/bin/matlab but unfortunately I don't have a terminal command to start Matlab (something like matlab ;)). If I want to start Matlab from the terminal I have to cd into the Matlab bin folder and ./matlab to start it.

Since I want to install the SBMLToolbox right know, I think I need such a command.
How can I create a command that starts Matlab from the terminal? Something with writing a starter script, or pasting the path in some file with an alias? I have no idea.

Please help!
Thanks

P.S. I'm on Hardy here.

---

### Post by stumbleUpon on 2008-09-04
> **pasQualle said:**
> Hey guys,

I don't know exactly if this is really a MatLab related question, or if you can solve it with a little linux experise (I'm learning every day I'm sitting in front of this machine, but with that I need your help.).

I've installed Matlab in /opt and created a starter with executes opt/matlabr2007a/bin/matlab but unfortunately I don't have a terminal command to start Matlab (something like matlab ;)). If I want to start Matlab from the terminal I have to cd into the Matlab bin folder and ./matlab to start it.

Since I want to install the SBMLToolbox right know, I think I need such a command.
How can I create a command that starts Matlab from the terminal? Something with writing a starter script, or pasting the path in some file with an alias? I have no idea.

Please help!
Thanks

P.S. I'm on Hardy here.
You have to set the path to the matlab installation directory.

Open .bashrc file in your home directory in any editor and add this line

export PATH=$PATH:/opt/matlabr2007a/bin/

---

### Post by prshah on 2008-09-04
> **pasQualle said:**
> 
I've installed Matlab in /opt and created a starter with executes opt/matlabr2007a/bin/matlab but unfortunately If I want to start Matlab from the terminal I have to cd into the Matlab bin folder and ./matlab to start it.

How can I create a command that starts Matlab from the terminal?

instead of cd'ing to the folder and using "./matlab" you can just do ```
/opt/matlabr2007a/bin/matlab
```

Is this what you're looking for? Post back if this is not it.

---

### Post by pasQualle on 2008-09-04
> **stumbleUpon said:**
> You have to set the path to the matlab installation directory.

Open .bashrc file in your home directory in any editor and add this line

export PATH=$PATH:/opt/matlabr2007a/bin/

No effect. Do I have to restart?

---

### Post by pasQualle on 2008-09-04
> **prshah said:**
> instead of cd'ing to the folder and using "./matlab" you can just do ```
/opt/matlabr2007a/bin/matlab
```

Is this what you're looking for? Post back if this is not it.

No, sry, it's not. I only want to type in ```
matlab
``` to start Matlab.

---

### Post by stumbleUpon on 2008-09-04
> **pasQualle said:**
> No effect. Do I have to restart?
If you are using the same terminal then do

source ~/.bashrc

else opening a new terminal will set the path.

---

### Post by pasQualle on 2008-09-04
> **stumbleUpon said:**
> If you are using the same terminal then do

source ~/.bashrc

else opening a new terminal will set the path.

Great! It's working. Thanks very much!

---

### Post by prshah on 2008-09-04
> **pasQualle said:**
> No, sry, it's not. I only want to type in ```
matlab
``` to start Matlab.
```

export PATH=$PATH:/opt/matlabr2007a/bin

```

will add the matlab bin directory to your path; then you can start it with just "matlab".

---

### Post by Tonie168 on 2008-11-06
Thanks a lot. Wasn't exactly looking for this, but saves a lot of time for me in the future.

EDIT: Where can I find the .bashrc file? I've searched for it, but couldn't find it. I'm new to Ubuntu.

---

### Post by ad_267 on 2008-11-06
> **Tonie168 said:**
> Thanks a lot. Wasn't exactly looking for this, but saves a lot of time for me in the future.

EDIT: Where can I find the .bashrc file? I've searched for it, but couldn't find it. I'm new to Ubuntu.

It should be in your home directory. Files with a "." in front are hidden so you can turn on "Show hidden files" under the view menu or press Ctrl+H. Or just press Alt+F2 and run "gedit .bashrc"

---

