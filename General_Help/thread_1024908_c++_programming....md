---
title: "c++ programming..."
date: 2008-12-29
forum: General Help
---

### Post by hezy00 on 2008-12-29
Hello,
I finally deared (if i spell it right) to start, step by step,  turning from windows to linux and I'm very glad and setisfied about it. Anyway, I've installed a copy of 8.10 on vmware and find is on the spot. I realy like to know what are the developing tools for c\c++, if there are and how to install it. I've asked that before and I have recived an answer about 3 system-built-in programms but I forgot about it. I realy like to get some help again. thx,
hezy.

---

### Post by Amazona aestiva on 2008-12-29
My favourite is [Code::Blocks]("http://www.codeblocks.org/").:)

It has many features, and available in debian binary.

---

### Post by mali2297 on 2008-12-29
First you need to install the package **build-essential**. It includes the compilers gcc and g++ together with other tools that can be run from the command line.

Next, if you want an IDE, try out **code::blocks**, **anjuta** or **geany**.

---

### Post by jus71n742 on 2008-12-29
if you wanted to go with VIM from command line you could do 
```

sudo apt-get vim-full

```

---

### Post by DGortze380 on 2008-12-29
sudo apt-get install build-essential

you'll have gcc which includes g++. That's all you need for C/C++ programing in Linux. I like geany for writing source, or VIM if you're old school.

sudo apt-get install geany

vim is a command line tool installed by default.

---

### Post by hezy00 on 2008-12-29
How do you install the package build-essential? How you open the command line? thx again,
hezy.
p.s How can I verify the ver. of the os and be sure weather it's 32 or 64 bit?

---

### Post by mali2297 on 2008-12-29
> **hezy00 said:**
> How do you install the package build-essential?
Open the package manager via System -> Administration -> Synaptic Package Manager. Then search for the package and mark it for installation. For more info, see [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto).

>  How you open the command line?
Via Applications menu -> Accessories -> Terminal. See [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal).

> 
p.s How can I verify the ver. of the os and be sure weather it's 32 or 64 bit?
In the terminal, type
```

uname -m

```
If the output is i686, then it means that you have a 32-bit OS. If it says x86_64, then you have 64-bit.

---

### Post by hezy00 on 2008-12-30
hey guys,
I realy apriciate alot the way you answer my quastions, what makes the experiance with the os enjoiyable and fruitable. Thanks alot,
Hezy.

---

### Post by DGortze380 on 2008-12-30
> **hezy00 said:**
> How do you install the package build-essential? How you open the command line? thx again,
hezy.
p.s How can I verify the ver. of the os and be sure weather it's 32 or 64 bit?

Second and more precise option.

Open a terminal
Accessories -> Terminal

type the following and press enter:
```

sudo apt-get install build-essential

```

sudo - gives you root (administrator) access
apt-get - the package manager in Ubuntu (can replace with aptitude)
install - argument to apt-get/aptitude specifying you wish to install the specified package
build-essential - the package you wish to install

---

