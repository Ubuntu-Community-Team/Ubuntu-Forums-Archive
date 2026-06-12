---
title: "I need help QUICK!!"
date: 2006-09-02
forum: Desktop Environments
---

### Post by DougieFresh4U on 2006-09-02
I was playing around in terminal and took out some # symbals and now I cannot get into package manager. When I try to get sinap. I get this error:E:Typte "N.B>" is not known on line 13 in source list /etc/apt/ source.list    E: The list of sources could not be read. E: Go to the repository dialog to correct the problem. I have not got a clue as to what I should do. Please someone assist me in simple terms as I am VERY new. I cannot access synapt. until this problem is fixed](*,) . Thanks

---

### Post by meng on 2006-09-02
Please post your sources.list here. Do this by typing
cat /etc/apt/sources.list
P.S. Everyone needs help, and everyone needs it quick, please be more informative with your thread title.

---

### Post by DougieFresh4U on 2006-09-02
I type that into th e term and got -No such file or directory. I am not sure how to post what ever comes up. Please forgive my ignorance

---

### Post by meng on 2006-09-02
1. Check that you typed the last command correctly.
2. If you're definitely certain that this file is missing, which would be strange because that error suggests that the file still exists, then you can do the following:
gksudo gedit /etc/apt/sources.list

then cut and paste the sources.list text found here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Regarding posting the output of a command here in these forums, you can copy and paste to and from the terminal if you run it within GNOME.

---

### Post by crane on 2006-09-02
> **DougieFresh4U said:**
> I was playing around in terminal and took out some # symbals and now I cannot get into package manager. When I try to get sinap. I get this error:E:Typte "N.B>" is not known on line 13 in source list /etc/apt/ source.list    E: The list of sources could not be read. E: Go to the repository dialog to correct the problem. I have not got a clue as to what I should do. Please someone assist me in simple terms as I am VERY new. I cannot access synapt. until this problem is fixed](*,) . Thanks

Firdt thing would be to go back to your sources list and check line 13 see what it says and edit accordingly. If it is just a link to a repo and your not sure the just comment it out with #
Are you trying to start synaptic from the menu? If so try just typing 
sudo synaptic
in a terminal.
 If you still have a problem starting it try running 
apt-get update
after you correct line 13.

 Just a couple thoughts.

---

### Post by Crooksey on 2006-09-02
```
sudo gedit /etc/apt/sorces.list
```

Delete everyhting in there, and copy in the below section.

```


deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted


deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted


deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe


deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main

deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted


deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse


deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse


deb http://archive.canonical.com/ubuntu dapper-commercial main


deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

deb http://download.skype.com/linux/repos/debian/ stable non-free

```

then
```
sudo apt-get update
```

---

