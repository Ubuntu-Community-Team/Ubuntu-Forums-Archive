---
title: "Changing icons for specific file type"
date: 2007-08-04
forum: Desktop Environments
---

### Post by Nevon on 2007-08-04
I'm using Ubuntu Feisty Fawn with GNOME, and I'm having some trouble associating an icon to a specific file type. I know how to change the icon on one specific file, but I would like that to apply to all files of the same type.

For example, I'm trying to set all .nds files to have a certain icon, but it won't work.

---

### Post by oomingmak on 2007-08-04
I tried to do this manually by editing various XML files, but I could never get it to work.

In the end I just used [**Assogiate**]("http://www.kdau.com/projects/assogiate/") and did it in a few seconds with no problems.

---

### Post by Nevon on 2007-08-05
Maybe I'm just a moron, but could you tell me how to install this?

---

### Post by oomingmak on 2007-08-05
Don't worry, I found the install process utterly bewildering as well (I'm a noob). Fortunately the author of the program saw a plea of mine in another thread, and gave me some instructions on how to solve the dependency issues.


[COLOR=Red]_**Installing Assogiate**_[/COLOR]

**1.** Open a terminal window and paste the following command:

```
 sudo aptitude install g++ libgtkmm-2.4-dev libgnome-vfsmm-2.6-dev libxml++2.6-dev gettext gnome-doc-utils
```This will install / update all the required libraries to make Assogiate work.


** 2.** Then [**download**]("http://www.kdau.com/projects/assogiate/download.html") the Assogiate archive file, unpack it and follow the 'Basic Install' instructions that are in the file called INSTALL.
The installation puts an Assogiate icon in your Applications menu, so you just run it from there and make whatever file type changes you want. 

Using the program is easy (and is a hell of a lot simpler than installing it).

Apparently Assogiate is going to be included by default in the next version of Ubuntu (so by October you won't need to do all this messing around trying to install it).

Hope that helps.

---

### Post by Nevon on 2007-08-05
I get stuck on the second step of the installation. After installing all the dependencies, downloading the package and navigating to it, I'm supposed to write 'make'. However, I only get this when I try > make: *** No targets specified and no makefile found.  Stop.

---

### Post by oomingmak on 2007-08-05
Did you configure first? (and are you doing it from within the extracted folder location?)

---

### Post by oomingmak on 2007-08-05
I also assume that you already have build essential installed.

If not then use:

```
sudo apt-get install build-essential
```

---

### Post by happysmileman on 2007-08-05
Yes if you have those installed the first step after navigating to the correct folder is "./configure", then "make"

---

### Post by oomingmak on 2007-08-05
> **happysmileman said:**
> Yes if you have those installed the first step after navigating to the correct folder is "./configure", then "make"
Thanks for the confirmation :) 

I'm a bit out of my depth trying to give advice here (because I am a complete and utter Linux noob). It was a miracle that I managed to get it working myself.

Just one final point, do you need to use sudo for any of those 3 commands? I can't remember whether I did or not (and I'm on Windows at the moment, so I can't check).

---

### Post by happysmileman on 2007-08-05
> **oomingmak said:**
> Thanks for the confirmation :) 

I'm a bit out of my depth trying to give advice here (because I am a complete and utter Linux noob). It was a miracle that I managed to get it working myself.

Just one final point, do you need to use sudo for any of those 3 commands? I can't remember whether I did or not (and I'm on Windows at the moment, so I can't check).

Well I'm assuming it's the same as most packages to be compiled. In which case it's

```
./configure
make
sudo make install
```

So you need sudo to install it, but not to prepare it (configure) or compile it (make)

---

### Post by oomingmak on 2007-08-05
> **happysmileman said:**
> So you need sudo to install it, but not to prepare it (configure) or compile it (make)
That makes sense (seeing as compile and make won't affect the system, whereas installation will).

The Assogiate instructions don't make any mention at all of using sudo during make install, so that's why I remembered something about figuring out that I had to add the sudo command myself.

I suppose it's obvious when you think about it, because all other types of software installation (synaptic etc.) require elevated privileges, so why would this one be any different?

---

### Post by Nevon on 2007-08-06
I don't know what the problem was, but it worked now when I first did ./configure and then make, and finally make install. It's strange though, because that's exactly what I did the first time.

Anyway, is it okay if I make a HOWTO out of this?

---

### Post by oomingmak on 2007-08-06
> **Nevon said:**
> I don't know what the problem was, but it worked now when I first did ./configure and then make, and finally make install.
Cool. I'm glad you managed to get it working.

---

