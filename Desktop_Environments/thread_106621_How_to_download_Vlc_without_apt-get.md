---
title: "How to download Vlc without apt-get?"
date: 2005-12-21
forum: Desktop Environments
---

### Post by index_0@ya.com on 2005-12-21
Hi thr,
        I am a newbie to use Ubuntu . I dont have internet conn at home, so i download at browsing centers and bring it home and install . So , i looked for VLC player  .. thru link apt-get link 
[http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) 
and went to i386 folder , and i found bunch of files with libraries (for dependency issues?? ) and build files,,!! 
and i dont know , the correct files to get VLC up and running..

can somebody help (not  only for VLC but generally for Debian istallations)

---

### Post by anil_robo on 2005-12-21
I'm not a command-line guy myself, but I'd try to help.

1. First, download the binary source for VLC [here.]("http://downloads.videolan.org/pub/videolan/vlc/0.8.4a/vlc-0.8.4a.tar.gz")
2. Then extract it by right clicking the file and selecting "extract here".
3. Now you have to open a terminal window, and navigate to the directory where you have extracted the source files. You can use the dir command to see what's in a folder, and use cd command to enter directories by their names.
4. When you have reached inside the extracted binary folder, type ./configure
5. Check for error messages. If there are no error messages, continue to step 6.
6. Type make and press enter
7. Type make install and press enter.
If all goes well, you should have installed VLC. If there are any dependent packages, the program will tell you their names in the error message. Find and install them too (follow the similar procedure - download binary, extract, ./configure, make and make install) one by one.

And do let me know what happened! I'm still learning you know! :)

---

