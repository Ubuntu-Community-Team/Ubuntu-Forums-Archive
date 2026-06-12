---
title: "Code::Blocks problem , please help"
date: 2009-05-24
forum: General Help
---

### Post by sudoomar on 2009-05-24
hello

i am new to ubuntu and linux systems

i e installed C::B and the GCC compiler pakage

now when i try to Run the prom code i get the following error

sh : /filepath permission denied

I tried to chown and chmod a+x ,it gives me another problem 

file_path :5 : Syntax error :"(" unexpected

please help

C is essential for me

---

### Post by sudoomar on 2009-05-24
Note that i use also Kdevelop and it gives me the same problem

---

### Post by colau on 2009-05-24
```

aptitude install g+++
aptitude install gcc

```
Can you post the snapshot and the code?

---

### Post by sudoomar on 2009-05-24
> **colau said:**
> ```

aptitude install g+++
aptitude install gcc

```
Can you post the snapshot and the code?

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

i think i have permission problems

how can i fix that

i have already installed gcc package

---

### Post by colau on 2009-05-24
> **sudoomar said:**
> E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

i think i have permission problems

how can i fix that

i have already installed gcc package
You need to be root or 
```

sudo aptitude install g++
sudo aptitude install gcc

```

---

### Post by sudoomar on 2009-05-24
> **colau said:**
> You need to be root or 
```

sudo aptitude install g++
sudo aptitude install gcc

```

i have installed g++ also

the problem persists

permission denied :(

---

### Post by sudoomar on 2009-05-24
i used the command chmod +x filename
and then bash filename

it gives me the following :

omar@omar-laptop:/storage$ bash omar
omar: line 2: syntax error near unexpected token `('
omar: line 2: `int main (void)'

---

### Post by colau on 2009-05-24
> **sudoomar said:**
> i used the command chmod +x filename
and then bash filename

it gives me the following :

omar@omar-laptop:/storage$ bash omar
omar: line 2: syntax error near unexpected token `('
omar: line 2: `int main (void)'
Can you post the code?
And going to that directory where your file is, can you post the output of
```

ls -l

```

---

### Post by sudoomar on 2009-05-24
> **colau said:**
> Can you post the code?
And going to that directory where your file is, can you post the output of
```

ls -l

```
```

-rwxr-xr-x 1 omar omar 121 2009-05-24 19:28 prova

```

---

### Post by welshboy on 2009-05-24
Forgive a dumb question, but did you install the build-essentials?

As that will install gcc, g++ and all the stuff that's linked to it.

---

### Post by sudoomar on 2009-05-24
> **welshboy said:**
> Forgive a dumb question, but did you install the build-essentials?

As that will install gcc, g++ and all the stuff that's linked to it.

i've already installed gcc and g++

do i need to install somethig else?

---

### Post by colau on 2009-05-24
```
sudo aptitude install build-essential
```
Can you post the content of the source file?

---

### Post by sudoomar on 2009-05-24
> **colau said:**
> ```
sudo aptitude install build-essential
```
Can you post the content of the source file?

```
omar@omar-laptop:~$ sudo aptitude install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "build-essentials"
Couldn't find any package whose name or description matched "build-essentials"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

omar@omar-laptop:~$ 

```

---

### Post by colau on 2009-05-24
> **sudoomar said:**
> ```
omar@omar-laptop:~$ sudo aptitude install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "build-essentials"
Couldn't find any package whose name or description matched "build-essentials"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

omar@omar-laptop:~$ 

```
It's
```

sudo aptitude install build-essential

```

---

### Post by sudoomar on 2009-05-24
> **colau said:**
> It's
```

sudo aptitude install build-essential

```

```
omar@omar-laptop:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done


```

the same

---

### Post by sudoomar on 2009-05-24
i executed the following code 

```
apt-cache depends build-essential

```

the result was ```
build-essential
 |Depends: libc6-dev
  Depends: <libc-dev>
    libc6-dev
  Depends: g++
  Depends: make
  Depends: dpkg-dev

```

gcc is missing here!!!

---

### Post by sudoomar on 2009-05-24
ie tried to write my hellow world program is a text file and then use the gcc from terminal 
but it says  no such directory

i am feeling pain :(

---

### Post by x33a on 2009-05-24
hey omar, i found this thread with a similar problem as yours:

[http://ubuntuforums.org/showthread.php?t=840445](http://ubuntuforums.org/showthread.php?t=840445)

see, if the solution posted works for you.

---

