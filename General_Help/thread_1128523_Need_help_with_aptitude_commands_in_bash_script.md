---
title: "Need help with aptitude commands in bash script"
date: 2009-04-17
forum: General Help
---

### Post by ALIENDUDE5300 on 2009-04-17
Hi, I'm experienced with Ubuntu, but I'm trying to create a bash script to automate some common tasks that I do in Linux, but I'm having a bit of trouble figuring out how to make the script interact with aptitude. Here's what I need it to do: Ask for the root password without the user having to type sudo before the command to run the script (I was thinking of having it check the username and if it isn't root yet, prompting for the password -- similar to what happens when you type 'sudo bash'), Check if specific packages that are needed for the rest of the script to work right are installed using aptitude, then if they are installed, reload the package lists and check for updates using 'apt-get update' and 'apt-get upgrade' -- otherwise, prompt the user to either install the packages or exit -- this should be completely automatic). After that, I should once again have it check if the packages were correctly installed and continue running the script. Anyone have any ideas on how to do this?

---

### Post by jowilkin on 2009-04-17
I was interested if there was an option in aptitude to allow you to not use "sudo aptitude ...", but only be prompted for password if needed, so I looked through the man page and could not find anything.

This is the behavior of the package manager yaourt on Arch Linux and I like it, but I don't know how to replicate it with aptitude.

I think the closest you could (easily) get to what you want is to just have a line in the script with "sudo aptitude install package1 package2 ...".  I believe that if the packages are not installed, they will be installed, and if the packages are installed but updates are available, they will be updated.

Another option is to use "aptitude search packagename" and then use grep or sed or awk or something like that to parse the output and determine if the package is installed.  "aptitude search" does not require sudo to work.  If you know your script requires a certain version of a program to work, you could use "aptitude show packagename" and then grep/sed/awk to determine the version of the installed package, the "show" option also does not require sudo.

---

### Post by ALIENDUDE5300 on 2009-04-17
Thanks for the help. Although it's kinda lame how I can't easily check if a package is installed without being root, that solution accomplishes everything I need. :)

---

