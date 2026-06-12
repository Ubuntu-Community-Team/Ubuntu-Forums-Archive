---
title: "Installing only security updates"
date: 2006-06-19
forum: Desktop Environments
---

### Post by flyingrhino on 2006-06-19
How do you install only security updates to ubuntu / kubuntu ?

I already know how to do apt-get update , apt-get upgrade and get
all the new packages, but sometimes I only want to get fixes for
security issues.

Any ideas ?

---

### Post by Jucato on 2006-06-19
You could probably just disable all other repositories except for dapper-security, and enable them only when you need to install things.

It's a bit tedious, though. But it's the only workaround I know. Using Synaptic to do this would probably make it a lot easier than manually editing sources.list everytime.

---

### Post by master_b on 2006-06-19
ditto for adept

/view/repositories
right-click and disable

bill

---

### Post by flyingrhino on 2006-06-21
thanks for that. i think commenting out the other repos will be an easy solution, i can create a second sources.list file and use that copy , then revert back to the original.

thanks.

---

### Post by lindyslack on 2006-06-21
How i rotate sources.list:

I have three sources.list files.

My sources.list = the one being used
My sources.list.security = everything but security commented out
My sources.list.all = all repos uncommented

made two shell scripts
from a comand prompt
cd ~
mkdir repos
cd repos
nano security.updates

the file looks like this

#!/bin/sh
echo 'Entering Security Update Only Mode'
sudo cp /etc/apt/sources.list.security /etc/apt/sources.list
sleep 30
sudo apt-get update


and a second file called all.updates
nano all.updates

the file looks like this

#!/bin/sh
echo 'Entering All Repository Mode'
sudo cp /etc/apt/sources.list.all /etc/apt/sources.list
sleep 30
sudo apt-get update

then just issue
chmod a+x *.updates 
to make them both executable
then to switch the repos from one to the other simply enter the repos directory and issue ./all.updates or ./security.updates

---

### Post by flyingrhino on 2006-06-21
More elaborate than manually changing the files, but looks good.
I

---

