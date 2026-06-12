---
title: "Double Clicking for apps to start"
date: 2009-04-26
forum: General Help
---

### Post by Dondo on 2009-04-26
Hello everyone.  I'm a noob when it comes to Ubuntu.  I've been using 8.04 for several months and have begun to figure a few things out.  (On a side note, I enjoy Ubuntu so far, little learning curve from a Windows user, but not horrible)  Last night I updated to Ubuntu 8.10, then this morning updated to 9.04.  I suppose everything worked with the exception of my "X-Plane" simulator.  I created a "shortcut" to the executable (like I did in 8.04), but when I dbl click it, nothing happens.  This might be more of an X-Plane question (I posted this same issue on a Linux flight simulation board), but I downloaded and unzipped the Linux X-Plane installer thinking that it would "refresh" my current X-Plane installation.  Well, when I dbl click that application, nothing happens either.  I know that these are not really .exe files (I do have Wine installed, but it is not needed with X-Plane Linux).  All of the applications/programs in my App/Programs list work fine.

Any idea's? I thought I read something about Linux keeping a list of double clickable programs that are installed, but I don't remember when/where I read that.

Thanks for any help.

Dondo

---

### Post by emshains on 2009-04-26
Emmm, so you didn't install it with synaptic or apt-get ?

Try running it in console, display the output.

Since you mentioned that you are a "noob", I'll give you some tips on using it.

First of all, you can open the terminal from Programs->Accessories->Terminal. 
Then, you should see a window, with this on it ```
[user]@[computer-name]:~$
``` 

Then, you should go to the directory where the executable is located. You can to this by using "cd". Example: ```
cd /path/to/the/directory
Note, that you now are at /home/[user]/ and you don't have to write that, you can just replace it with ~
Basically ~ is /home/user/
```

Then, to execute it, just write ./[executable]

---

### Post by Dondo on 2009-04-26
How frustrating....I thought that I could do this...what am I missing here?  I've tried everything I can think of.  I also found a link telling me that I might need some new LIB files to place in the USR/LIB32 folder, but when I try to unzip them, they tell me I need root permission.  Found another post to tell me to type "SUDO" before the command....what command?  I'm using the unzipper program.  Here is what I've done with the terminal window:

[I]dondo@Ubuntu:~$ cd /X-Plane 9/X-Plane 9 Demo
bash: cd: /X-Plane: No such file or directory
dondo@Ubuntu:~$ cd/X-Plane 9
bash: cd/X-Plane: No such file or directory
dondo@Ubuntu:~$ cd /X-Plane 9
bash: cd: /X-Plane: No such file or directory
dondo@Ubuntu:~$ X-Plane 9
bash: X-Plane: command not found
dondo@Ubuntu:~$ cd~
bash: cd~: command not found
dondo@Ubuntu:~$ cd ~
dondo@Ubuntu:~$ cd/X-Plane 9
bash: cd/X-Plane: No such file or directory
dondo@Ubuntu:~$ cd ~/X-Plane 9/X-Plane 9 Demo
bash: cd: /home/dondo/X-Plane: No such file or directory
dondo@Ubuntu:~$ /home/dondo/X-Plane 9/X-Plane 9 Demo
bash: /home/dondo/X-Plane: No such file or directory
dondo@Ubuntu:~$ cd/home/dondo/X-Plane 9/X-Plane 9 Demo
bash: cd/home/dondo/X-Plane: No such file or directory
dondo@Ubuntu:~$ X-Plane-i686
bash: X-Plane-i686: command not found
dondo@Ubuntu:~$ [/I]

Here is the link to the extra libraries I guess I need:

[http://forums.x-plane.org/index.php?showtopic=37947](http://forums.x-plane.org/index.php?showtopic=37947)

I downloaded the .tar file and try to unzip it, but it tells me I need my root password.

---

### Post by Dondo on 2009-04-26
okay, so I got to the X-Plane dir (had to call upon my old DOS commands, but I remembered a few), here is what I got:


[I]dondo@Ubuntu:~/X-Plane 9/X-Plane 9 Demo$ ./X-Plane-i686
./X-Plane-i686: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory
dondo@Ubuntu:~/X-Plane 9/X-Plane 9 Demo$ [/I]

Dondo

---

### Post by Dondo on 2009-04-27
Finally figured out how to get root privileges so that I can add libraries to the usr/lib32, but now I get this error when trying to give myself access:


dondo@Ubuntu:~$ sudo nautilus
[sudo] password for dondo: 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:13578): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root
--> file:///root/Desktop
--> file:///

(nautilus:13578): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 3 elements at quit time (keys above)

(nautilus:13578): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 3 elements at quit time
dondo@Ubuntu:~$ 

I'm quite frustrated at this point.  I am simply trying to copy 5 files into a directory and it has taken me 5 posts on two different forums....and I still have not got it to work.  Anyone have any suggestions?

Thanks

Dondo

---

