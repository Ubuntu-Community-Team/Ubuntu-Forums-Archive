---
title: "Python 2.6.5 Installation"
date: 2010-06-10
forum: Desktop Environments
---

### Post by hamzah01 on 2010-06-10
Hi, 
I need help installing Python 2.6.5 on my computer. I tried to downloaded and installed from the Internet directly but it gives me error message. Also I tried to downloaded it from Ubuntu but when I go to the software package and click on python it show me hundreds of python types. I'm a beginner and I need to use Python for my class this summer, I only need to use python GUI. So please any one can tell me how to install python on Ubuntu and also how to find it  after installation. 
Thank you.

---

### Post by ThesaurusRex on 2010-06-10
Did you try simply going to the terminal and typing...

```
sudo aptitude install python
```

? If that doesn't work, try 'python-2.6.5' instead of just 'python'

---

### Post by hamzah01 on 2010-06-10
I typed the command and I think it work. I have attached screen shot to the result. 
please take look at it and tell me if python been installed  or not. if yes please tell me then how to find the program in Ubuntu (python GUI) because I'm also new to Ubuntu. 

Thank you for your help.

---

### Post by stoneage on 2010-06-11
You want to install python2.6 not python.

Also by gui do you mean an ide? If so idle-python2.6 should be what you are looking for

---

### Post by hamzah01 on 2010-06-11
yes the exactly what I wanted. And it work, now i can see the Python Idle. 

Thank you very much for you help.

---

### Post by BigFlatBrook on 2010-06-25
I have the same problem -- not being able to install python 2.6.5

 sudo aptitude install python

does nothing because it seems to think that python 2.5.2 is the latest.

  sudo aptitude install python-2.6.5
  sudo aptitude install python2.6
  sudo aptitude install python2.6.5
  sudo aptitude install python-2.6

all return with the error message that the package couldn't be found.

I'm on 8.04.  What am I missing?

---

### Post by stoneage on 2010-06-25
Python2.6.5 isn't in the repository for Hardy.

---

