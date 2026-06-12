---
title: "Tecplot 360 2008 Installation"
date: 2009-04-06
forum: General Help
---

### Post by dmitriyp13 on 2009-04-06
Here's a quick how-to for installing Tecplot 360 2008 in Ubuntu as the instructions in the official guide are somewhat incomplete or inaccurate.

**Step 1:**
[INDENT]    Run the install script
```
sudo ./setup
```
    Go through all of the prompts and answer the questions as they pertain to your particular setup, including the license file info.[/INDENT]


**Step 2 (optional):**
[INDENT]    If you entered the wrong license info, modify the tecplotlm.lic file.[/INDENT]


**Step 3: **
[INDENT]    Modify the .profile file to include the following two lines
```
## Tecplot 360 2008 environment variable
export TEC_360_2008=/opt/tecplot360-2008
PATH=$PATH:$TEC_360_2008/bin
```
    Where /opt/tecplot360-2008 is the directory where Tecplot was installed.[/INDENT]


**Step 4:**
[INDENT]    To get Tecplot working immediately, either restart the computer or enter the commands from Step 3 into the terminal.[/INDENT]


**Step 5:**
[INDENT]    Run Tecplot.
```
tec360
```
    If you get the following error message:
```
/opt/tecplot360-2008/bin/tecplot.shared: error while loading shared libraries: libstdc++.so.5: wrong ELF class: ELFCLASS32
```
install the libstdc++5 library via
```
sudo apt-get install libstdc++5
```[/INDENT]

Enjoy

---

### Post by kairho on 2009-04-15
I had the following error: 

```
/opt/tec360/bin/tecplot.shared: error while loading shared libraries:
 libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

Solution was to install the libc from gutsy:
[packages.ubuntu.com]("http://packages.ubuntu.com/gutsy/i386/libstdc++2.10-glibc2.2/download")

Also, about Step4: There is no need to restart the computer. Starting a new terminal session or sourcing the profile file ". ~/.bashrc" for bash (or "source ~/.profile" for bourne?) will be sufficient.

---

