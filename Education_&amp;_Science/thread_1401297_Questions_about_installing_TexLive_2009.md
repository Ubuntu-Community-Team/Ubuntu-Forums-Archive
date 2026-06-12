---
title: "Questions about installing TexLive 2009"
date: 2010-02-07
forum: Education &amp; Science
---

### Post by AmadeusOK on 2010-02-07
Hey everyone,

I'm trying to install TexLive 2009 following the instructions at [http://tug.org/texlive/quickinstall.html](http://tug.org/texlive/quickinstall.html). I unpacked it in /usr/local/src. When I run "./install-tl" I got the following message:

```


Detected platform: x86_64 with GNU/Linux
 
 <B> binary systems: 1 out of 15

 <S> Installation scheme (scheme-full)
     83 collections out of 84, disk space required: 2002 MB

 Customizing installation scheme:
   <C> standard collections
   <L> language collections

 <D> directories:
   TEXDIR (the main TeX directory):
     !! default location: /usr/local/texlive/2009
     !! is not writable, please select a different one!
   TEXMFLOCAL (directory for site-wide local files):
     /usr/local/texlive/texmf-local
   TEXMFSYSVAR (directory for variable and automatically generated data):
     /usr/local/texlive/2009/texmf-var
   TEXMFSYSCONFIG (directory for local config):
     /usr/local/texlive/2009/texmf-config
   TEXMFHOME (directory for user-specific files):
     ~/texmf

 <O> options:
   [ ] use letter size instead of A4 by default
   [X] create all format files
   [X] install macro/font doc tree
   [X] install macro/font source tree
   [ ] create symlinks to standard directories

 <V> set up for running from DVD

Other actions:
 <I> start installation to hard disk
 <H> help
 <Q> quit

Enter command: i
Installing to: /usr/local/texlive/2009
./install-tl: mkdir(/usr/local/texlive/) failed, goodbye: Permission denied


```

Where should I unpack the tarball? Do I need to create a subdirectory /texlive? What can I do? Thanks in advance for any kind of help.

---

### Post by myle on 2010-02-08
[https://help.ubuntu.com/community/LaTeX](https://help.ubuntu.com/community/LaTeX)

```
sudo apt-get install texlive
```

works fine.

---

### Post by Abdus on 2010-02-08
> **myle said:**
> [https://help.ubuntu.com/community/LaTeX](https://help.ubuntu.com/community/LaTeX)

```
sudo apt-get install texlive
```

works fine.

No, it doesn't work fine, as the TeXLive version available in Ubuntu repositories is very outdated. This is why some decide to install fresh TeX environment manually.


Back to the thread - seems you don't have enough privileges to install in this path. I didn't install TL manually (I used Ailurus installer instead), so I'm not sure, but I would try using sudo (if it's not strongly discouraged somewhere in the readmes :) ).

---

### Post by Claus7 on 2010-02-08
Hello,

its absolutely normal the error you get. Because if you do e.g.: cd /usr/local and then type mkdir test, you will get the same error and the directory won't be created. That means, as it was mentioned, that you have not the privileges to install something on this directory.

It is irrelevant in most applications where you will download the tarball. What it matters is, which path you will give during configuration (part of the installation procedure) in order for the necessary files of the package to be installed. 

If you keep the default, then I would suggest you to download the package to your home folder or your Desktop. Untar the file and enter the directory. Become root (sudo su, and give your password) and then type i)./configure  ii)make and iii)make install and probably, if you have all the dependencies, you are done.

edit:sometimes instead of the configure command you just type ./executable and the installation proceeds as in this situation, where you are required to type:"./install-tl"

Regards!

---

### Post by AmadeusOK on 2010-02-09
Hey everyone,

Thank you very much for all your help. I did exactly the same as before but this time I used "sudo". It worked like magic, although it took more than 12 hours to install all the packages.

Now, at the end I got the following message:

```
 
 Add /usr/local/texlive/2009/texmf/doc/man to MANPATH.
 Add /usr/local/texlive/2009/texmf/doc/info to INFOPATH.

 Most importantly, add /usr/local/texlive/2009/bin/x86_64-linux
 to your PATH for current and future sessions.

 Welcome to TeX Live!
Logfile: /usr/local/texlive/2009/install-tl.log

```

How do I do this and what's all of this for? What are MANPATH, INFOPATH, and PATH?

---

### Post by Claus7 on 2010-02-09
Hello.

follow this: [http://www.everyjoe.com/newlinuxuser/howto-add-a-directory-to-my-path-statementvariable/](http://www.everyjoe.com/newlinuxuser/howto-add-a-directory-to-my-path-statementvariable/)

for each of PATH, INFOPATH and MANPATH.

This has to do on how your system will be able to identify and execute the program you want by finding where the executable is located. E.g. if you type cp command, the computer will try to find the cp command in all the directories that are included in the PATH variable. If it is there then the command will be executed. Now, if you install a program and its executable resides to a folder that is not comprised in the PATH variable you either have to navigate to that folder and find the executable and finally execute it or inform the PATH variable about the location of that executable. The same logic applies to the other variables you mention as well.

Regards!

---

### Post by AmadeusOK on 2010-02-10
> **Claus7 said:**
> Hello.

follow this: [http://www.everyjoe.com/newlinuxuser/howto-add-a-directory-to-my-path-statementvariable/](http://www.everyjoe.com/newlinuxuser/howto-add-a-directory-to-my-path-statementvariable/)

for each of PATH, INFOPATH and MANPATH.

This has to do on how your system will be able to identify and execute the program you want by finding where the executable is located. E.g. if you type cp command, the computer will try to find the cp command in all the directories that are included in the PATH variable. If it is there then the command will be executed. Now, if you install a program and its executable resides to a folder that is not comprised in the PATH variable you either have to navigate to that folder and find the executable and finally execute it or inform the PATH variable about the location of that executable. The same logic applies to the other variables you mention as well.

Regards!

Thanks for the explanation, it makes a lot of sense. However, I still have a few more questions. Sorry if I'm being annoying, but here I go:

1. Does adding here just mean inserting the text into the file? Is it something like

sudo [text editor name] /etc/profile

and/or

sudo [text editor name] /root/.bash_profile

and then  

PATH=$PATH:/usr/local/texlive/2009/bin/x86_64-linux
export PATH
? 

2. Do I have to do this for both the root and the user?

3. What's the correct syntax? Do I need to write anything before export PATH? How about a semicolon? Are quotation marks needed anywhere?

4. Are these two /etc/profile and /root/.bash_profile standard? I've seen somebody else using /etc/environment instead of /etc/profile.

Thanks again.

---

### Post by Claus7 on 2010-02-16
Hello,

what I would try to do if I were in your shoes would be:

```
cd /home/*your_user_name*
vim .bashrc 
```

and go in the end of that file and add:
> export PATH=/usr/local/texlive/2009/bin/x86_64-linux:$PATH
export MANPATH=/usr/local/texlive/2009/texmf/doc/man:$MANPATH
export INFOPATH=/usr/local/texlive/2009/texmf/doc/info:$INFOPATH

then type:
SHIFT+: and then
wq!

Then log out and log in again to see how the changes took effect. In case you face errors just remove the lines you added. This will affect only you as a user which I think is the best tactic to use.

Regards!

---

### Post by Abdus on 2010-02-16
> **AmadeusOK said:**
> 1. Does adding here just mean inserting the text into the file? Is it something like

sudo [text editor name] /etc/profile

and/or

sudo [text editor name] /root/.bash_profile

and then  

PATH=$PATH:/usr/local/texlive/2009/bin/x86_64-linux
export PATH
? 

2. Do I have to do this for both the root and the user?

3. What's the correct syntax? Do I need to write anything before export PATH? How about a semicolon? Are quotation marks needed anywhere?

4. Are these two /etc/profile and /root/.bash_profile standard? I've seen somebody else using /etc/environment instead of /etc/profile.

I suggest you use a simpler and less puzzling method that works as well as the one mentioned earlier. If you use it, you won't have to repeat the process for other users, as it will work for everyone. No exporting paths will be needed as well - it will kick in after next system boot.

I have Tex-Live 2009 installed and running smooth on my Ubuntu 9.10 Karmic. After it was installed, it modified my "/etc/environment" which now looks like that (with the part relating to TeX-Live marked with bluish colors):
```
PATH="[COLOR="Indigo"]/usr/local/texlive/2009/bin/x86_64-linux[/COLOR][COLOR="Red"]:[/COLOR]/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
MANPATH="[COLOR="Navy"]/usr/local/texlive/2009/texmf/doc/man[/COLOR]"
INFOPATH="[COLOR="Navy"]/usr/local/texlive/2009/texmf/doc/info[/COLOR]"
JAVA_HOME="/usr/lib/jvm/java-6-sun"
JAVA_BIN="/usr/lib/jvm/java-6-sun/bin"
CLASSPATH=".:/usr/lib/jvm/java-6-sun/lib/dt.jar:/usr/lib/jvm/java-6-sun/lib/tools.jar"
```

To modify your /etc/environment, open it with any text editor you want. My personal choice would be 'vim', but it may be puzzling for a newbie, so you can as well use something simpler, like 'gedit'. To open the file in chosen editor you type in the console:
```
sudo [text editor name] /etc/environmet
```
For vim:
```
sudo vim /etc/environmet
```
For gedit:
```
sudo gedit /etc/environmet
```
Then you just modify your file by adding new values to variables. You file originally looks probably like that:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME="/usr/lib/jvm/java-6-sun"
JAVA_BIN="/usr/lib/jvm/java-6-sun/bin"
CLASSPATH=".:/usr/lib/jvm/java-6-sun/lib/dt.jar:/usr/lib/jvm/java-6-sun/lib/tools.jar"
```
So first you must paste the path for TeX executables: 
```
/usr/local/texlive/2009/bin/x86_64-linux
```
to the line starting with "PATH". Your new line should look like:
```
PATH="/usr/local/texlive/2009/bin/x86_64-linux[COLOR="Red"]:[/COLOR]/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```
Note that the new valuse is added [i]after] the quotation mark, and that it is separated from next value in the line by a colon mark (in red).

Now you still need to add 2 completely new lines, so just go ahead, add them anywhere:
```
MANPATH="/usr/local/texlive/2009/texmf/doc/man"
INFOPATH="/usr/local/texlive/2009/texmf/doc/info"
```



> **Claus7 said:**
> [...]
then type:
SHIFT+: and then
wq!
[...]
You just suggested to use vim for editing files of vital importance to the system *to a newbie*, who does not feel comfortable neither with the files, neither with the editor (I suppose). In my opinion this was highly irresponsible from you, as vim is a really tricky and "unpredictable" editor if one doesn't know how to use it. There is no need to use vim here, any other editor can do the job without all the risks and frustration related to vim.

I do love vim, I do suggest people to learn and use it, as it is a marvelous tool. No doubt here. But there are situations, like here, when it's more responsible not to 'push' towards it. :)

PS. There was a joke around: how to produce a string of random ASCII symbols? Open vim and tell a newbie to close it.

---

### Post by Claus7 on 2010-02-17
Hello,

> **Abdus said:**
> 
....

You just suggested to use vim for editing files of vital importance to the system *to a newbie*, who does not feel comfortable neither with the files, neither with the editor (I suppose). In my opinion this was highly irresponsible from you, as vim is a really tricky and "unpredictable" editor if one doesn't know how to use it. There is no need to use vim here, any other editor can do the job without all the risks and frustration related to vim.

I do love vim, I do suggest people to learn and use it, as it is a marvelous tool. No doubt here. But there are situations, like here, when it's more responsible not to 'push' towards it. :)

PS. There was a joke around: how to produce a string of random ASCII symbols? Open vim and tell a newbie to close it.

Glad you added all this info. That way someone can choose which way fits better to one's needs. Really, as you can understand, vim is second nature to me, that's why I suggest that way, which in the end I think that is the fastest way to make changes to the contents of the file, while using command line. 

Yet, in the end, is a matter of personal taste I think. Hope the thread creator has more than the info the creator needs.

Regards!

---

### Post by AmadeusOK on 2010-02-17
Thank you guys for your help. After I added the directory to the path everything worked out perfectly. My /etc/environment now looks like this

```

PATH="/usr/local/texlive/2009/bin/x86_64-linux:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
MANPATH="/usr/local/texlive/2009/texmf/doc/man" 
INFOPATH="usr/local/texlive/2009/texmf/doc/info" 

```

---

