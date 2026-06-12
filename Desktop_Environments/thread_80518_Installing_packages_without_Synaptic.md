---
title: "Installing packages without Synaptic"
date: 2005-10-22
forum: Desktop Environments
---

### Post by irv on 2005-10-22
I am some what new to Linux, and I find installing packages confusing :confused:  There are .deb, gz, and .bin files and no real instructions on how it all work.
So far I did figuar out how to us sudo dpkg -i to install .deb files, but when I tried to install gxine all I get is lib files not found. (libxinel 1.0.1 and libsmjsl) I do have libxinel 1.0 installed but it neeeds 1.0.1. How do I install bin and gz files? and where are all this files going?

I posted this in the How to do forum but it is hard to get an answer.

---

### Post by somuchfortheafter on 2005-10-22
i think the how-to forum is for tuts anyway gz files are generally source code meaning they must be compiled from source. At your skill level there is one book you should really cosider ordering it is called Linux Power Tools, none of the information in thebook is ubuntu specific however it does cover *nix fundamentals really well as well as package management features of each distrobution (debian, redhat, and slackware.) also what is wrong with synaptic to intall packages with?

---

### Post by irv on 2005-10-22
Thanks for the advice on "Linux Power Tools".
I just tried an install for RealPlayer10 and it installed but in my user folder. It works, but I don't thinks it belong there. I used the sudo apt-get install to do this.
I am still looking for the libxinel and libsmjsl lib files?
I am not using Synaptic because the programs I am trying to install are not in the Repositories and I am not sure how to add them. I am not sure what to put in the "APT line"?

---

### Post by somuchfortheafter on 2005-10-22
ok well i just installed gxine via synaptic anyway. you need to do this

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bc
```
```
sudo gedit /etc/apt/sources.list
```

then select all of what you have and remove it, then replace it with this

```

#Comments removed

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe multiverse

# Might be useful, might not...

deb http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

then save the file, next.
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```
After all of this gxine should be in the repositories for synaptic.

---

### Post by irv on 2005-10-22
Just to let you know I found a copy of Linux Power Tools on ebay for **$1.37 + $3.99** for shipping. Thanks again for the tip.

---

### Post by irv on 2005-10-22
I followed the instruction to the letter, and everything worked!!! I now have gxine installed. Thanks again for the help.

---

### Post by somuchfortheafter on 2005-10-22
glad to be of help

---

