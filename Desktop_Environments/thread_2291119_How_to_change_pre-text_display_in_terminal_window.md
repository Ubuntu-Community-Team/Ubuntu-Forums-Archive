---
title: "How to change pre-text display in terminal window?"
date: 2015-08-18
forum: Desktop Environments
---

### Post by ruwan2 on 2015-08-18
Hi,

Due to different applications, I have several Ubuntu, such as one 14.04 64-bit, another is 12.02 64-bit. When I installed the 12.02 Ubuntu, I thought it was a 32-bit. I named it U12-32Bit at the OS installation process. Now, I find that it is 64-Bit Ubuntu. That is fine for my app, but the pre-text(I don't know what formal name of it) in a terminal window shown as U12-32Bit, which is not 64-Bit.

Could you tell me how to correct it?


Thanks,

---

### Post by dino99 on 2015-08-18
is not that partition label ?; you can rename it with gparted

---

### Post by steeldriver on 2015-08-18
... I think the OP is referring to the hostname portion of the PS1 prompt

---

### Post by tgalati4 on 2015-08-18
You can change it.  Edit the *.profile* and set it to what you want.

What is your current PS1?

```
echo $PS1
```

What is your hostname?

```
cat /etc/hostname
```

Where does your terminal prompt get set?

```
cat /etc/bash.bashrc
```

What should I set it to:  /h is substituted for your hostname, otherwise change it to My_Machine

```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@My_Machine\[\033[01;34m\] \w \$\[\033[00m\]'
```

Where My_Machine is a useful name for you.  If you are happy with it, then make it permanent.

```
cd
nano .profile
```

Use the arrow keys to go to the bottom of the file and add the line.  Control-O (enter) to save, Control-X to exit.

An alternative is to change your *hostname*, but that may affect your network connectivity.

```
man hostname
```

---

### Post by ruwan2 on 2015-08-18
The terminal has pre-text:
[COLOR=#0000ff]u12_rj@u12-_32_Bit-MS-7696:~$[/COLOR]

I want it to be:
[COLOR=#0000ff]u12_rj@u12-[/COLOR][COLOR=#006400]_64_[/COLOR][COLOR=#0000ff]Bit-MS-7696:~$[/COLOR]


Some poster wants the action of the computer of echo "$PS1". Here is it:

u12_rj@u12-32Bit-MS-7696:~$ echo $PS1
[COLOR=#800000]\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$[/COLOR]
u12_rj@u12-32Bit-MS-7696:~$ 



How can I get the desired string:
[COLOR=#0000ff]u12_rj@u12-[/COLOR][COLOR=#006400]_64_[/COLOR][COLOR=#0000ff]Bit-MS-7696:~$


Thanks,
[/COLOR]

---

### Post by tgalati4 on 2015-08-19
What is the output of:

```
hostname
```

---

