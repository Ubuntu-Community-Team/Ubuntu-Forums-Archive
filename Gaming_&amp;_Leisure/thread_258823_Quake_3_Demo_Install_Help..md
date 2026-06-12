---
title: "Quake 3 Demo Install Help."
date: 2006-09-16
forum: Gaming &amp; Leisure
---

### Post by BOBSONATOR on 2006-09-16
hey guys, I just downloaded linuxq3ademo-1.11-6.x86.gz.sh, (quake 3 demo) and im trying to install it. 

So right off the bat, i ```
sh linuxq3ademo-1.11-6.x86.gz.sh
``` and get some error.

So then i ```
chmod +x linuxq3ademo-1.11-6.x86.gz.sh
``` and then some text goes flying by my screen in less than one second then it closes.

Can someone please help me? i have searched high and low but still cant find the answer.

Edit: Screen Added [http://img87.imageshack.us/img87/5903/screenshotcy3.png](http://img87.imageshack.us/img87/5903/screenshotcy3.png)

Thanks.

---

### Post by BOBSONATOR on 2006-09-17
please... 

bump.

---

### Post by BOBSONATOR on 2006-09-17
*Tears running down face*

please?

---

### Post by mr_niceguy on 2006-10-11
[http://www.ubuntuforums.org/showpost.php?p=322717&postcount=3](http://www.ubuntuforums.org/showpost.php?p=322717&postcount=3)

---

### Post by aidanr on 2006-11-09
i got it up and running
```
wget ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3ademo-1.11-6.x86.gz.sh
./linuxq3ademo-1.11-6.x86.gz.sh -target ~/q3
chmod -R 755 q3/
cp q3/bin/x86/glibc-2.0/q3demo q3/
cp q3/bin/x86/glibc-2.0/libMesaVoodooGL.so.3.2 q3/libMesaVoodooGL.so
ln -s /usr/lib/libGL.so.1 q3/libGL.so
rm -R q3/setup.data
rm -R q3/bin
rm q3/setup.sh
cd q3/
./q3demo
```
:D happy fragging

---

### Post by theosib on 2006-11-28
I'm reopening this thread, because running the quake demo installer is broken again.

When I follow those instructions, the window that pops up complains about there being no file named "-r". Apparently, the script is calling some program called "print" indirectly via a variable $echo, and that print doesn't accept -r as an option.

Help?

---

### Post by fearpi on 2007-02-26
I also have this problem. Anyone solve it yet?

---

### Post by fyo on 2007-03-13
I just successfully installed the latest q3a demo (same version quoted in the other post, although I downloaded it today).

I had some problems, but adding the target worked for me. Running the installer as my ordinary user caused it to fail (gracefully) at some later point since it wanted to install stuff in /usr/local/.... I tried to rerun as root, but then the installer failed completely. Turns out that when the q3 target directory is there, the installer won't run, so this needs to be deleted first. All the files are no-write, so chmod first:

chmod -R +w q3
rm -fr q3/

After that, running the installer worked fine:

./linuxq3ademo-1.11-6.x86.gz.sh -target ~/q3

The installer wants permission to write to the following directories:

/usr/local/games/q3demo
/usr/local/bin

NOTE: THE FIRST INSTALLER SCREEN STILL SHOWS ERRORS!!!! All that file -r not found stuff is still there. Ignore it. It doesn't appear to affect anything.

Now we'll see if the demo will actually run...

-fyo

---

### Post by fyo on 2007-03-13
And, yes, it worked flawlessly.

---

### Post by fyo on 2007-03-23
Of course, after upgrading (clean install) to Edgy Eft, I've been COMPLETELY unable to get q3demo to install. The installer returns:

./setup.sh: 9: function: not found
x86

---

### Post by rajeev1204 on 2007-03-23
hi 

i followed this  and got it to install'

But i have tried hopelessly to get sound configured.

Getting display working was tough too . i had to create a few symlinks etc.

but sound no idea.

the config files need some driver for sound and if i could give it a path , then it may run . Thats how i selcted nvidia drivers to be used for display:) 

But it looks for sound in dev/dsp which i cant figure out which other location to give

any help will be greatly appreciated

regards

rajeev

---

### Post by fyo on 2007-03-23
It took a bit of messing around, but I finally got q3ademo to install and run on Edgy.

Running linuxq3ademo-1.11-6.x86.gz.sh results in the aforementioned error in setup.sh.

Even though the installer fails, the target directory, q3 in my case, has been created and all the files unpacked.

Running setup.sh with bash instead of sh (as it's set to) makes it run, although it doesn't quite complete. It does manage to install the files (default location being /usr/local/games/q3demo/ ), however. Sadly, the game won't run at this point, so we look at the error returned from the setup.sh script. 

This error points to another script, postinstall.sh, which exhibits an error similar to the one in setup.sh. The solution is the same, run it with bash instead of sh. However, postinstall.sh takes an argument - the target directy - so we need to supply that as well.

So far so good, but (at least on my system) postinstall.sh doesn't finish completely, failing before making some vital symlinks. Creating these manually is the final step needed to installing the game completely on Edgy.

Here are the commands: (make sure you run them with the appropriate permissions, typically "sudo" if you want to install in the default location)

[COLOR="Red"]
$ /bin/bash linuxq3ademo-1.11-6.x86.gz.sh -target ~/q3

---> ./setup.sh: 9: function: not found

$ /bin/bash q3/setup.sh

---> similar error in postinstall.sh

$ /bin/bash postinstall.sh /usr/local/games/q3demo

---> Voodo drivers not installed error

$ ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so

(or execute q3ademo with "+set r_gldriver libGL.so.1")

DONE!
[/COLOR]

---

