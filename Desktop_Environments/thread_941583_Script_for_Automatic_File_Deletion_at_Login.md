---
title: "Script for Automatic File Deletion at Login"
date: 2008-10-08
forum: Desktop Environments
---

### Post by robk315 on 2008-10-08
First off I am very new to Ubuntu/Gnome so bear with me... I am running Ubuntu 8.0.4 with the Gnome desktop as a LTSP server(K12 School Environment). LTSP clients are logging in automatically to unique local accounts. I need help creating a login script that will delete files and directories in the users Documents folder (this is so students cannot look or use another students work). From a terminal I can use #rm -r -f /$HOME/Documents/* to accomplish this, but I have no idea how to make this run at login. Any help would be greatly appreciated...

---

### Post by caleb12 on 2008-10-08
Basically, you want to create a script with those commands in it. Then edit the users .profile or .bashrc files and reference that script - I forgot which one you want to actually edit, I believe you can use either... but google may have a better answer. In either case, the idea is that the .bashrc and .profile scripts are run at login which would then execute the script you want. 

Although if I understand your question well enough, you should be able to set the proper UMASK for the user files which would make them unreadable by another user account. The particular umask is set in .profile as well. I think a umask of 066 would produce files readable by only the user that created them, this is adjustable of course. 

For your scripting pleasure:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

---

### Post by robk315 on 2008-10-08
I am typically used to writing Windows batch files in a 2000/XP environment so this is very new to me. So I put the command into a text editor, do I have to save it to a specific location or with any type of extension? I was thinking about using the session preferences to add this startup script, that way I can copy the users home directory to /etc/skel so the autologin accounts all have this script.

---

### Post by caleb12 on 2008-10-08
Setting up a bash script is as easy as opening a text editor, make sure this is on the first line

#!/bin/bash
#

that tell the script what enviroment to execute commands under, this is for a bash script specifically so we call the bash environment. You could write a perl or ruby script the same way... 

All lines (after the first) that have a # at the beginning are considered comments and are not executed. So, in you case... your script may look something like this:

#!/bin/bash
#
# Deletes contents of user directory
#

rm -r -f /$HOME/Documents/*  ## I'm a comment

# more comments. 

I always make it a habit of being descriptive in my comments, because while that line of code may make complete sense in this moment... next year you may have no idea what you were thinking... 

Ok, once that's done... save the file as any name... Another rule of thumb is that I give scripts an extension I recognize... so I would save it, user.sh - but this doesn't actually matter. Now you have to make the file executable, I usually do this at a command prompt - so from a terminal type, chmod +x user.sh Now it's executable... 

Put the file someplace you will remember. Edit .profile and reference the file. I don't know your whole setup here but a couple of potential issues I see are... 1) file permissions, the script will be executed as the current owner of the script so make that an administrative account that has permission to delete files 2) the $HOME in your command is a variable, and depending on your environment may or may not be recognized by the script. It is possible to define variables in your script as well... 

In either case... test it and you'll know soon enough.

---

### Post by robk315 on 2008-10-08
I made the file an executable then moved it to /bin . I added /bin/rmdocs.sh to the session startup program manager and it seems to be working. Thanks again for the help!

---

