---
title: "Need help installing a dosbox cvs build"
date: 2009-02-08
forum: General Help
---

### Post by hempa on 2009-02-08
Hi i have allready posted this question before in the games forum but with no answer so im hoping for better luck here.
My qustion is this:Does anybody know how to install a cvs build of dosbox in ubuntu? the cvs build i have is from daum cafe. [http://ykhwong.x-y.net/cvs/frame.html](http://ykhwong.x-y.net/cvs/frame.html)
Im just hoping that someone who has installed this build can give me a fairly detailed tutorial on how to install it in ubuntu (hardy)
all help tips/tricks are welcome thanks

---

### Post by gfulton on 2009-02-08
1. Download the cvs snapshot of your choice (ex. 32bit: [http://www.msu.edu/%7Eyootaewo/linux/32bit/20061016.7z](http://www.msu.edu/%7Eyootaewo/linux/32bit/20061016.7z))

2. Extract the archive: ~/dosbox_cvs for example. This will contain the code that needs to be compiled.

3. Read the INSTALL or README file - but usually works like this:

cd to root of source tree
./configure
make
make install

I wasn't able to try this just yet as the linux snapshot is in a 7z archive for some reason, and I don't know the cvs location.

Hope this helps,
-gf

---

### Post by hempa on 2009-02-08
Hi thanks for the answer to my question, your the first one to answer and i have tried alot of forums not only ubuntu.i tried the command you gave me in your response earlier but i only get this message in terminal 
./configure: command not found

and the only files in that folder are twoo executables(not windows .exes but linux ones) one called dosbox and one called dosbox_debug and there is one shared library file called libSDL-1.2.so.0.11.1
and then there is a dosbox.conf file and a readme txt

the readmetxt says: Copy these two files into /usr/local/lib 

1. cp ./libSDL-1.2.so.0.11.1 /usr/local/lib 


Please link them to use OpenglHQ

2.  ln -s /usr/local/lib/libSDL-1.2.so.0.11.1 /usr/local/lib/libSDL.so
3.  ln -s /usr/local/lib/libSDL-1.2.so.0.11.1 /usr/local/lib/libSDL-1.2.so.0

my usr/local/lib is completely empty but my usr/lib folder is packed with stuff could the readme maybe mean that i should copy those files to there instead?
and what happens after that what shall i do with the linux exe called dosbox does it go int to some dir to AArgh! i dont get it at all.
this is what they say about cvs builds at the vogons: First, install the latest official release of DOSBox. Then, unpack the CVS build over the top of it, replacing the release versions of the files with the CVS versions.

---

