---
title: "bash: event not found(please help)"
date: 2005-10-02
forum: Desktop Environments
---

### Post by fsshl on 2005-10-02
root@etutor:~# mv !serial.txt      math/.
bash: !serial.txt      math/.: event not found
----------------------------------------------------------------please help--fsshl

---

### Post by darkmatter on 2005-10-04
[QUOTE=fsshl]root@etutor:~# mv !serial.txt      math/.
bash: !serial.txt      math/.: event not found
----------------------------------------------------------------please help--fsshl[/QUOTE]

You are not utilizing bash correctly. Don't feel bad, we've all been down that road before.

I can help you with that, but first I need to know what directory serial.txt is in and which directory math is in.

Then i can use your problem to show you the correct manner in which to use bash to move a file.

---

### Post by darkmatter on 2005-10-04
Use the 'Places' menu and click on 'Search for files...' to find the location of the file/directory. Type 'serial.txt' in the search field, then tell me where it is located. Then do the same for 'math'.

This will give me the information I require to help you.

---

### Post by fsshl on 2005-10-06
first, thanks your reply and way to help
---------------------------------------------------------------------------------------------------
root@etutor:~# ls
c_ccprogram  [COLOR="Blue"]math[/COLOR]  [COLOR="PaleGreen"]mp95.zip[/COLOR]  [COLOR="Blue"]ms9387E[/COLOR]  !serial.txt  [COLOR="Blue"]src[/COLOR]
---------------------------------------------------------------------------------------------------
hope to see your (or any advancers') experienced advice again
fsshl

---

### Post by darkmatter on 2005-10-06
[QUOTE=fsshl]first, thanks your reply and way to help
---------------------------------------------------------------------------------------------------
root@etutor:~# ls
c_ccprogram  [COLOR="Blue"]math[/COLOR]  [COLOR="PaleGreen"]mp95.zip[/COLOR]  [COLOR="Blue"]ms9387E[/COLOR]  !serial.txt  [COLOR="Blue"]src[/COLOR]
---------------------------------------------------------------------------------------------------
hope to see your (or any advancers') experienced advice again
fsshl[/QUOTE]
Ok. From the information given, both the file and  math directory are in your  root's home directory (/root). First, I'll give you the command to move !serial.txt to math, then I'll explain a little about bash usage in regards to the command, and give you some links to bash resources to better help you learn the proper usage/syntax.
To move !serial.txt to math (as root - since the output you listed was from your root account), type the following in a terminal 
```
mv ~/!serial.txt ~/math
```
the '~' is a 'shorthand' representation for the 'home' folder of the account you are running from. For example, if the above files were on my system under my user account, I could move the .txt by the following
```
mv /home/darkmatter/!serial.txt /home/darkmatter/math
```
or, if i was running as root, and the above files were in my root directory, I would move the .txt with
```
mv /root/!serial.txt /root/math
```
but, to save on typing, I can substitute '~' in place of the home directory. So for either of the above situations, the command would look the same:
```
mv ~/!serial.txt ~/math
```
The same files, if in the root account, could also be moved with the sudo command from my user account, but i would need to give the full path to the file, as well as the math directory
```
sudo mv /root/!serial.txt /root/math
```
As you can see from the above examples, bash commands follow a very simple structure. Individual commands are always seperated by a space, and the same holds true for a source directory (as in your case, the location of !serial.txt) and the destination directory (in your case, the location of /math)
Directory paths are also given a specific structure (just think of how you would list a directory under Windows in the command prompt or in the 'address bar of Windows Explorer. Although Linux/UNIX uses '/' to define a change in directory, as opposed to Windows, which uses '\')

Therefore, the path must be represented in the above manner, with a '/' preceeding any file or folder in the directory structure.

I hope this information was of help (and not confusing)

For more information on beginning to use bash, see the following links:

Beginners tutorials:
[http://cs.gettysburg.edu/~tneller/dept/bash-tutorial.html](http://cs.gettysburg.edu/~tneller/dept/bash-tutorial.html)
[http://www.hypexr.org/bash_tutorial.php](http://www.hypexr.org/bash_tutorial.php)
[http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal) (It's a little old, but still useful)
[http://subsignal.org/doc/AliensBashTutorial.html](http://subsignal.org/doc/AliensBashTutorial.html) (I personally like this one)

References:
One of the most overlooked. In a terminal, type
```
man bash
```
Online:
[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html) (the GNU bash reference manual)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/) (the a-z listing of bash commands)
[http://en.wikipedia.org/wiki/Bash](http://en.wikipedia.org/wiki/Bash) (wikipedia - has some very useful links)
[http://infocenter.guardiandigital.com/manuals/SecureProfessional/node260.html](http://infocenter.guardiandigital.com/manuals/SecureProfessional/node260.html) (basic  bash commands)
Good Luck, and welcome to Ubuntu Forums.:)

---

