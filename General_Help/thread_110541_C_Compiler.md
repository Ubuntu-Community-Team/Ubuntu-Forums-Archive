---
title: "C Compiler"
date: 2005-12-31
forum: General Help
---

### Post by s_spiff on 2005-12-31
I finally sorted out some of my problems, but now when I'm installing the rp-ppoe, the error i get in the terminal window is = Could not convert to executeble files, C compile not found or something like that. Doesn't Ubuntu come default with a C compiler? If not, where can I get one so that I can get done with this. Otherwise I'll have to boot up in windows only to ask a query! I'm already going insane!

---

### Post by PaganHippie on 2005-12-31
No, it doesn't come with a C compiler.  Fire up Synaptic, search for 'gcc' & 'g++' and install everything recommended.

---

### Post by darth_vector on 2005-12-31
gcc and g++ wont be enough. you will have to install the C library files, make and a few other things as well. the package you want it build-essential

sudo apt-get install build-essential

---

### Post by s_spiff on 2005-12-31
hey thanks, but I read the error I got more carefully, it says, the compiler couldn't generate executable files. Any clue why the error?

---

### Post by darth_vector on 2005-12-31
can you post the whole error

---

### Post by s_spiff on 2005-12-31
Umm, I don't exactly remember, cuz its in the linux OS and I'm in Windows, to access the net, I have to install a rp-pppoe-3.7 package [.tar  or something]. I extracted it into the /usr/local/src and then as a root executed the file Go. When I do that, it says, look to some gcc, which then goes to gcc compiler and then finally it gives an error, that the compiler couldn't generate execuables. for more information check out config.log, which I have no clue wher it resides. :(

---

### Post by darth_vector on 2005-12-31
did you have the compiler installed at the time? its not installed by default, so try installing again after getting build-essential. you may also have to download and install other things that program needs (called dependencies). the README file should tell you all about these.

try the above and let us know if it works. if not, try to post the whole error message. its a lot easier with one.

by the way, to find config.log try using the locate command.

good luck mate :)

---

### Post by s_spiff on 2005-12-31
umm.. will try the above, thanks . I'll write down the whole error when i again boot into linux. God, all this seems to be a big head ache! will give you guys an update in another 15/20 mins.

---

### Post by s_spiff on 2005-12-31
Ohh yeah, I had everything that was associated with C and C++ installed that time. Dunno why it didnt work. Will give it a shot agian soon.

---

### Post by s_spiff on 2005-12-31
Is there any way to install a new compiler or library for C in Ubuntu? I'm trying to install the pppoe script, and the C compiler is not able to produce executables. Someone mentioned that it may be due the library missing or someting like that. I downloaded a .tar C compiler, burned it on a cd. Now I want to know how to install it on nix, every time I try through synaptic, it says, ' couldn;t find any packages, perhaps this is not a debian cd' . Anyway to put in a new compiler? I want to set this net connection up. That done, I wont have to boot up everytime into xp to post my queries!

---

### Post by cylon359 on 2005-12-31
I thought the pppoe stuff was already included?  Does "sudo pppconfig" not work?

---

