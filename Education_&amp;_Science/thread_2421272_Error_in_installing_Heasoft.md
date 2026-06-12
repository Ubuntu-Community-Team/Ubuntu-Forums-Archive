---
title: "Error in installing Heasoft"
date: 2019-06-19
forum: Education &amp; Science
---

### Post by astroriya on 2019-06-19
I'm trying to install a package called heasoft  in order to do some nuclear physics research. I can't seem to get the  commands to work, even though I'm following the instructions as  far as I can tell. Here is the instruction page: [http://heasarc.gsfc.nasa.gov/docs/so...t/install.html]("http://heasarc.gsfc.nasa.gov/docs/software/lheasoft/install.html")

Here is how I've tried to type the commands. It's a  standard pre-built binary, as I'm not advanced enough to mess with the  source code.

rxs103@nucpc30:~/heasoft-6.26/x86_64-pc-linux-gnu-libc2.27/BUILD_DIR$ export HEADAS=/home/rxs103/heasoft-6.26/x86_64-pc-linux-gnu-libc2.27/BUILD_DIR
rxs103@nucpc30:~/heasoft-6.26/x86_64-pc-linux-gnu-libc2.27/BUILD_DIR$ . $HEADAS/headas-init.sh
headas-init.sh: ERROR -- cannot execute /home/rxs103/heasoft-6.26/x86_64-pc-linux-gnu-libc2.27/BUILD_DIR/BUILD_DIR/headas-setup

---

### Post by sehouma on 2020-02-23
Hello,
You should use those commands in your terminal (home)
export HEADAS=/home/rxs103/heasoft-6.26/x86_64-pc-linux-gnu-libc2.27   # you need to be sure thattthe x86_..... is a folder in your heasoft folder
. $HEADAS/headas-init.sh
alias heainit=". $HEADAS/headas-init.sh"
heainit

you need also to add the alias to   ~/.bash_aliases

Here is an interesting video explaining the installation

---

