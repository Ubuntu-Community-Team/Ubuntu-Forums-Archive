---
title: "No such file or directory"
date: 2010-12-21
forum: Desktop Environments
---

### Post by smss on 2010-12-21
Hi
How to fix this erorr:
```

smss@smss-me:~/temp$ ./start.sh
bash: ./start.sh: /bin/tcsh: bad interpreter: No such file or directory

```And im sure ```
 start.sh
``` is available in the directory ```
 /home/me/temp/ 
```

---

### Post by karthick87 on 2010-12-21
Are you sure that you are inside the directory???

---

### Post by ajgreeny on 2010-12-21
cd to the directory first with ```
cd temp
``` if temp is a folder in home, no need for the** /temp,** just **temp** will do it.  Then just ```
./start.sh
```should run the file.

You only need the  / if the folder path is in the root file system, not when it's in home.

---

### Post by smss on 2010-12-21
Yes , Im confident.

---

### Post by smss on 2010-12-21
Yes , Im just using only this ```
cd temp
```But I'm faced with this error:
```
smss@smss-me:~/temp$ ./start.sh
bash: ./start.sh: /bin/tcsh: bad interpreter: No such file or directory
```

---

### Post by Possum Films on 2010-12-21
Are you sure that start.sh is set to be executable? 

Try this:```
chmod +x ./start.sh
```

---

### Post by qamelian on 2010-12-21
From the error you're getting, it appears that the script wants to run under the tcsh shell. Do you have tcsh installed? It isn't installed on a default Ubuntu system.

---

### Post by smss on 2010-12-21
How I install the tcsh??

---

### Post by smss on 2010-12-21
This no result:```
chmod +x start.sh && chmod +x ./start.sh && sudo chmod +x start.sh && sudo +x ./start.sh
```

---

### Post by qamelian on 2010-12-21
> **smss said:**
> How I install the tcsh??

Go to Applications > Accessories > Terminal.

At the prompt in the terminal, type:
```
sudo apt-get install tcsh
``` and press enter.
You will be prompted to enter you password. Type it in and press enter. Note that the password will not actually show up as you are typing it.

Then just wait for a few moments as the package manager downloads and installs tcsh. :)

---

### Post by smss on 2010-12-21
Yes.
 Was correct.
 I thank from all and especially [qamelian.]("http://ubuntuforums.org/member.php?u=8229")

---

