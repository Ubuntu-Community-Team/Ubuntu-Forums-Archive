---
title: "I need help in something that is simple, I think"
date: 2009-03-10
forum: General Help
---

### Post by stargazerfpx on 2009-03-10
Hello, I'm a newbie in the use of ubuntu/linux and I'm trying to install on my system ns-2 (a program that simulates gmpls webs) and I'm having some issues. When I try to install the program itself, with all due components already installed and checked, it gives me this message after I run ./install :

Please put /home/rafael/Desktop/ns-allinone-2.33/bin:/home/rafael/Desktop/ns-allinone-2.33/tcl8.4.18/unix:/home/rafael/Desktop/ns-allinone-2.33/tk8.4.18/unix
into your PATH environment; so that you'll be able to run itm/tclsh/wish/xgraph.

IMPORTANT NOTICES:

(1) You MUST put /home/rafael/Desktop/ns-allinone-2.33/otcl-1.13, /home/rafael/Desktop/ns-allinone-2.33/lib, 
    into your LD_LIBRARY_PATH environment variable.
    If it complains about X libraries, add path to your X libraries 
    into LD_LIBRARY_PATH.
    If you are using csh, you can set it like:
                setenv LD_LIBRARY_PATH <paths>
    If you are using sh, you can set it like:
                export LD_LIBRARY_PATH=<paths>

(2) You MUST put /home/rafael/Desktop/ns-allinone-2.33/tcl8.4.18/library into your TCL_LIBRARY environmental
    variable. Otherwise ns/nam will complain during startup.


After these steps, you can now run the ns validation suite with
cd ns-2.33; ./validate

As I'm a beginner I have no idea on how to do that, if anyone can isntruct me on how to proceed I would higly apreciate it.


Thanks already.

---

### Post by prince_niceguy on 2009-03-10
open .bashrc in your home folder using gedit.

find if there is a PATH (please ensure proper case), if not add a line like below.
```

PATH=$PATH:~/Desktop/ns-allinone-2.33/otcl-1.13:~/Desktop/ns-allinone-2.33/otcl-1.13:
export PATH

```

find if there is a LD_LIBRARY_PATH in .bashrc if not then create one or append to it.

```

LD_LIBRARY_PATH=$LD_LIBRARY_PATH:~/Desktop/ns-allinone-2.33/tcl8.4.18/library:
export LD_LIBRARY_PATH

```

now logout and relogin.

and run the steps of cd ns-2.33; ./validate in a terminal to see if it works.

Let me know if you want to understand what has been done here.

---

### Post by stargazerfpx on 2009-03-10
I would really like to understand what was done, but I think I can do it here. Thanks! And I'll be waiting for the explanation

---

### Post by prince_niceguy on 2009-03-10
Hope that work.

.bashrc is a file which gets executed when you login or open a terminal (assuming bash is your default shell. there are lot of sites with info on shell, as it would be elaborate for this small post :-)).

so what we did was tried to set the PATH and LD_LIBRARY_PATH. PATH is something which is used by shell to find the location of your programs, e.g. when you type firefox in terminal, it will search for all the directories given in the path to locate a match for firefox command and run it if it finds one.

LDA_LIBRARY_PATH is similar to path but only for loading library (dll in MS terms) for running a program.

I have not used your home folder in the PATH as mentioned by your command, I have replaced it with ~ which is equivalent of home.

Hope that gives some insight, though it is not elaborate you can relate something :-)

---

