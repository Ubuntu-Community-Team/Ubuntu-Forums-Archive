---
title: "Intel Fortran compiler"
date: 2008-09-08
forum: Education &amp; Science
---

### Post by Kito1980 on 2008-09-08
Hi everyone. I'm really newbie in ubuntu and I have a problem installing Intel Fortran compiler.

I followed all instructions of this page

[http://registrationcenter-download.intel.com/irc_nas/1208/l_fc_p_10.1.018_INSTALL.htm]("http://registrationcenter-download.intel.com/irc_nas/1208/l_fc_p_10.1.018_INSTALL.htm")

however, I have the problem in the section "Setting Up the Compiler Environment", specifically when is written "It is strongly recommended that you add those script files into your login script (.login file)."

I don't know where is "my login script". Anyone could help me to find it and tell me what thing I should write inside of this file?

Thank you.



RESOLVED by kjohansen and jeremytaylor

> Thank you for help me, you were really nice.

As summary:

1.- I found my ".bashrc" file in "/home/<my-login-name>". Because it's a hidden file, I had to push "Ctrl+H" to see it.

2.- I added in the end of the file ".bashrc" the following lines:

```
source /opt/intel/fc/10.1.018/bin/ifortvars.sh
source /opt/intel/idb/10.1.018/bin/idbvars.sh
```

3.- Restart my laptop, and it's work.

---

### Post by kjohansen on 2008-09-08
Here is a guy with some soultions:
[http://www.tjansson.dk/?p=78](http://www.tjansson.dk/?p=78)

Are you specifically attached to the intel compiler?  I have always used gfortran from the people who make gcc for C and it works great and is available through the repositories for easy installation.

sudo apt-get install gfortran.

---

### Post by Kito1980 on 2008-09-08
> **kjohansen said:**
> Here is a guy with some soultions:
[http://www.tjansson.dk/?p=78](http://www.tjansson.dk/?p=78)

Are you specifically attached to the intel compiler?  I have always used gfortran from the people who make gcc for C and it works great and is available through the repositories for easy installation.

sudo apt-get install gfortran.


Yes, I really need install that compiler. 

I'll work with a fortran program of 70k of lines of other guy who compile with it. He told me he has had some problems with other compilers, so I might to install the intel one.

I know it is really easy to install gfortran, but I don't wanna have any problem. 

Thanks you for the answer, but I need know where are those files.

---

### Post by kjohansen on 2008-09-08
[http://ubuntuforums.org/showthread.php?t=565498](http://ubuntuforums.org/showthread.php?t=565498)


files that begin with "." are hidden files.  To show them in nautilus CTRL + H

---

### Post by jeremytaylor on 2008-09-09
I found that my Ubuntu install didn't come with a .login file but using the .bashrc file seemed to work. For example I added the lines 

```

source /opt/intel/fc/10.1.015/bin/ifortvars.sh
source /opt/intel/idb/10.1.015/bin/idbvars.sh

```

to mine, the location of the appropriate scripts will depend on where you installed the compiler.


Hope that works/helps
Jeremy

---

### Post by Kito1980 on 2008-09-09
Thank you for help me, you were really nice.

As summary:

1.- I found my ".bashrc" file in "/home/<my-login-name>". Because it's a hidden file, I had to push "Ctrl+H" to see it.

2.- I added in the end of the file ".bashrc" the following lines:

```
source /opt/intel/fc/10.1.018/bin/ifortvars.sh
source /opt/intel/idb/10.1.018/bin/idbvars.sh
```

3.- Restart my laptop, and it's work.

---

### Post by Xnst on 2008-09-12
Hi,

I think if you put the variable definitions: that is:

```

source /opt/intel/fc/10.1.015/bin/ifortvars.sh
source /opt/intel/idb/10.1.015/bin/idbvars.sh 

```

in your .bashrc it will only be visible for your shell sessions. If you on the other hand put it in the .profile other software can use the compiler as well. I know abaqus requires intel fortran so, if you use the compiler from other software I suggest you move it to .profile

---

