---
title: "[SOLVED] nvidia - glx"
date: 2008-03-19
forum: Desktop Effects &amp; Customization
---

### Post by Living2007 on 2008-03-19
What and where can I find a solution to the "nvidia - glx"

I enabled the standard desktop effects anf it pops up with the "nvidia - glx"

---

### Post by erginemr on 2008-03-19
What is your system specs? Laptop or desktop computer? Its brand name? What is the brand and model of your graphics card?

What is the outcome of the following command from the terminal?
```
lspci | grep -i vga
```

What happens when you run "restricted drivers manager" from the Gnome main menu -> System -> Administration?

---

### Post by Living2007 on 2008-03-19
The computer's custom built.

4 Partitions; 2 NTFS, 1 swap, 1 Linux drive
Intel Inside Celeron D
Windows XP and ubuntu 7.10
80 GB HDD and 512 RAM
nVidia gForce4 MX 4000 @ 128MB of GPU RAM

---

### Post by PmDematagoda on 2008-03-19
You can install the nvidia-glx package with:-
```
sudo apt-get install nvidia-glx
```

You can enable the Nvidia driver with:-
```
sudo nvidia-glx-config enable
```

---

### Post by Living2007 on 2008-03-19
Do I need the internet activated? 

Because I am having so much trouble setting up DCSI Dial-Up internet connection

---

### Post by PmDematagoda on 2008-03-19
> **Living2007 said:**
> Do I need the internet activated? 

Because I am having so much trouble setting up DCSI Dial-Up internet connection

You could go to [Ubuntu Packages]("http://packages.ubuntu.com/") and download it and then run it from Ubuntu.

---

### Post by Living2007 on 2008-03-19
OK, Internet needs to be fixed

---

### Post by Living2007 on 2008-03-30
> You could go to Ubuntu Packages and download it and then run it from Ubuntu

I cant locate the package

---

### Post by PmDematagoda on 2008-03-30
It must be there.

In any case, here is the direct link:-
[http://packages.ubuntu.com/search?keywords=nvidia-glx-new&searchon=names&suite=gutsy&section=all](http://packages.ubuntu.com/search?keywords=nvidia-glx-new&searchon=names&suite=gutsy&section=all)

---

