---
title: "how install tvtime"
date: 2005-04-04
forum: Desktop Environments
---

### Post by kristi on 2005-04-04
I did 
sudo apt-get install tvtime

and got  "Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package tvtime"

edit:ditto with firefox
edit2:It's been a while - something about need to add appropriate libraries to debian archiving set so it will know where to look?
edit3: present state of /etc/apt/sources.list   ```

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330)]/ hoary main restricted


deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

```

edit4:  I'm guessing that of the last 6 extant lines, 4 are commented and need to be uncommented.
HELP!!! 
What repositories are usually added?  and is there a mechanism for adding them?

tia
Kristi

---

### Post by lao_V on 2005-04-04
Uncomment the lines with universe in the end. Then, sudo apt-get update and try to install tvtime. You can do all this via synaptic package manager as well.

---

### Post by digby on 2005-04-04
You can get more info on extra repositories [here]("http://ubuntuguide.org/temp/#extrarepositories").  The instructions for that say to use gedit, but I remember you saying that you didn't have that, so you can use vi again (or my favorite: the easy to use nano).

---

### Post by kristi on 2005-04-04
digby, thanks so much for your time and effort.  I took kubuntu down this morning.  I'll try it again if there's a good major release with documentation specific to kubuntu that's up to date (re repositories), and good partition mount support.
Thanks again.  You tried!
Kristi

---

