---
title: "loading realplayer"
date: 2005-10-20
forum: Desktop Environments
---

### Post by fourtwenty on 2005-10-20
just loaded ubuntu went to load realplayer10 went to the site and it says to make sure the .bin file i downloaded was executalble. I have never used linux before so bear with me. I open terminal and type chmod a+x realplayer10gold.bin and hit enter and it always comes back with file not found. I tried /home/xxx/desktop etc. not found. I have rightclicked on the file but see no options for running it. I managed to download alien as well as a libstsomething 5 file. I just need a few pointers. Thanks in advance orik

---

### Post by fourtwenty on 2005-10-22
got it working but it won't play streaming video from national geographic magazine ngm.com they have a widlcam there. It just says this version can't play it. Is there another version capable. thank you

---

### Post by Riverside on 2005-10-22
[QUOTE=fourtwenty]just loaded ubuntu went to load realplayer10 went to the site and it says to make sure the .bin file i downloaded was executalble. I have never used linux before so bear with me. I open terminal and type chmod a+x realplayer10gold.bin and hit enter and it always comes back with file not found. I tried /home/xxx/desktop etc. not found. I have rightclicked on the file but see no options for running it. I managed to download alien as well as a libstsomething 5 file. I just need a few pointers. Thanks in advance orik[/QUOTE]Linux (and Unix) commands are case sensitive, so typing "chmod a+x realplayer10gold.bin" won't work.

You need to type:

user@localhost:~$ chmod a+x RealPlayer10GOLD.bin

Which will work.  Or, you could make use of your Bash shell's file completion functionality by typing "chmod a+x Rea<Tab>" - providing there is no other file in the directory commencing "Rea", Bash will automagically complete the file name for you.  You also need to be in the directory, or to point your command at the directory, where the RealPlayer10GOLD.bin file is situated of course.

---

