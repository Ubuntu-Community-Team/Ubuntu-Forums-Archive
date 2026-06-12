---
title: "Changing directory in shell script (Problem)"
date: 2009-06-01
forum: General Help
---

### Post by lockhid on 2009-06-01
Hi,
I'm currently using Ubuntu 9.04 (Jaunty). I've no modem driver,
so I download vlc player and its related pkgs from 'packages.ubuntu.com'. I wanted to create a shell script 
which would install all pkgs serially (pkgs depends followed). 
my pkgs directory structure is given below

/root/ubuntu-pkgs
   -> pkgs
      -> hardy
      -> jaunty
   -> vlc-plugin
      -> hardy
   -> vlc
      -> hardy

So, I created the following script. Script name is 'vlc-install_i386.sh' and it is in the 
"/root/ubuntu-pkgs/vlc/hardy" directory.

script:

cd ../../pkgs/hardy
dpkg --install <package-name.deb>
dpkg --install <package-name.deb>
.........
dpkg --install <package-name.deb>

cd ../../vlc/hardy
dpkg --install vlc-nox_*.deb

cd ../../vlc-plugin/hardy
dpkg --install <package-name.deb>
....
dpkg --install <package-name.deb>

cd ../../vlc/hardy
dpkg --install vlc_*.deb

-------------
but, it's not working. Console shows ' No such Archive' and
pkgs are not installed. I think 'cd' is not changing the dir.

How this will work? Please help me.

Sincerely,
Lockhid

---

### Post by lensman3 on 2009-06-01
Try running your shell script as:

sh -xv <script>

The -xv will show what the scripts are executing as it happens.  Also you might add the command "pwd" print-working-directory to see where the script actually is at that moment.

Hope this helps.  (yes the cd command is a special built-in command to the shell.  A cd in a script is different from the command line.  But it should work in your case.  The old saying "You can't teach an old dog (the shell), new tricks (the script)", is true, because the script is being spawned and not running in the current shell).  

Take a look at the "source" and the . (dot) command.  These two commands actually allow you to run a command(s) in an executing shell without a spawn.

---

### Post by lockhid on 2009-06-04
This post have some mistake mainly the tree structure of the directory mentioned above. This post is moved to the following post.

[http://ubuntuforums.org/showthread.php?t=1176282&highlight=lockhid]("http://ubuntuforums.org/showthread.php?t=1176282&highlight=lockhid")

please goto that post.

---

### Post by lockhid on 2009-06-10
**===================================================**
**SOLVED!!!!!!!!!!!!!!!!!SOLVED!!!!!!!!!!!!!!!!SOLVED**
**===================================================**
The problem is solved. Actually it's caused because I edited some parts
of this script in Windows and Windows use line terminator 'CRLF' pair and
Unix family os use only 'LF'. The problem caused by 'CR' - carrige return code.

You can see the solution thread from the following link-

[http://ubuntuforums.org/showthread.php?t=1183334]("http://ubuntuforums.org/showthread.php?t=1183334")

thanks, **asmoore82** for giving an excellent solution with a demonstration.

---

