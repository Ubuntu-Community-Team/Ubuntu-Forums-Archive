---
title: "Origami install fails, not sure why."
date: 2010-10-06
forum: Education &amp; Science
---

### Post by krohn on 2010-10-06
I have a machine that is idle most of the time and wanted to install folding@home.  I followed all of the directions that are posted here:

[https://help.ubuntu.com/community/FoldingAtHome/origami](https://help.ubuntu.com/community/FoldingAtHome/origami)

the sudo apt-get install origami works fine but the install does not work.  I try this:

sudo origami install -u myUserName -t 45104 -k myPasscode

and it results in an:

ERROR: WGET RETRIEVAL FAILED!

I just used wget to download a different file so I am online and know wget works.  Anyone have any guesses as to what I am doing wrong?  Thanks.

---

### Post by yaaarrrgg on 2010-10-07
I just installed and am seeing the same message. My first thought is either:

1. their network is having a temporary issue (maybe the service is down).  This might fix itself. or 

2. my network is locked down too much to allow the communication (might need to open up port forwarding on my router?)

3. some kind of permission issue?

4. A bug needs to be reported?



I'll need to trouble shoot this more ...

---

### Post by yaaarrrgg on 2010-10-07
Hmm ... I'm not sure why origami is not starting up for me.

Although I just installed  manually from Standford's site and got it working.  I used version 6.02, rather than 6.29 though.  The latest release would not run for me.  It said it could not execute the binary file.  Maybe that could be affecting origami as well?

The instructions I used are at:

[http://folding.stanford.edu/English/LinUNIGuide](http://folding.stanford.edu/English/LinUNIGuide)

# what i did ... open a terminal and paste:
mkdir -p ~/folding
cd ~/folding
wget [http://www.stanford.edu/group/pandegroup/folding/release/FAH6.02-Linux.tgz](http://www.stanford.edu/group/pandegroup/folding/release/FAH6.02-Linux.tgz)
tar xzf FAH6.02-Linux.tgz
chmod +x fah6

# then configure the client (you can select all the defaults). 
# Ubuntu's Team number is 45104 , if you want to use it
./fah6 -configonly

# create a startup script (optional):
echo "./fah6 -verbosity 9 &" > fah
chmod +x fah

# then to start the client:
./fah

---
notes: There are more instructions for setting up as a serice that automatically starts up.
If you run "top" when the machine is not used, you should see the client around 100% cpu.

---

