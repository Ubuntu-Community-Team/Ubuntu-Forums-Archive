---
title: "Need to run network security script built for windows and OS X"
date: 2009-01-19
forum: General Help
---

### Post by danda1man on 2009-01-19
Ok, to gain internet access on my school network, I need to run the Bradford_Dissolvable_Agent.sh script.  The extension is for a shell script but the download says it is a BIN file (not sure if that makes a difference).  All attempts to run the file have been met with failure.  I am assuming my school was not planning on Linux based OS's on the network, but is there any way I can run this script?  Here is the output from my attempts to run the program:

administrator@server1:~$ chmod +x /home/administrator/Desktop/Bradford_Dissolvable_Agent.sh
administrator@server1:~$ sh /home/administrator/Desktop/Bradford_Dissolvable_Agent.sh
mkdir: cannot create directory `.CSA.TEMP': File exists
awk: cannot open /home/administrator//home/administrator/Desktop/Bradford_Dissolvable_Agent.sh (No such file or directory)
tail: +: invalid number of lines

gzip: stdin: unexpected end of file
tar: This does not look like a tar archive
tar: Error exit delayed from previous errors
chmod: cannot access `./engine': No such file or directory
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 11: ./engine: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 12: function: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 19: function: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 25: netscape: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 25: netscape: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 26: function: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 30: function: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 33: epiphany: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 34: function: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 37: konqueror: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 38: function: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 47: function: not found
/home/administrator/Desktop/Bradford_Dissolvable_Agent.sh: 50: opera: not found
Error running CSA.sh.  Please call the helpdesk.
rm: cannot remove `engine': No such file or directory
rm: cannot remove `agent.config': No such file or directory
rm: cannot remove `tmp.csa': No such file or directory

Note:
Because I have to run this to gain internet access, anything I need to install needs to be ported over by USB flash drive.

---

### Post by cybergalvez on 2009-01-19
have you tried to read the file? whats in it? try gedit Desktop/Bradford_Dissolvable_Agent.sh or simply cat Desktop/Bradford_Dissolvable_Agent.sh to see what the file is attempting to do

---

### Post by cariboo on 2009-01-19
If the script is going to make any changes in any thing other then /home, you should run the script using sudo.

Also check with the IT deptartment, it's up to them to keep the network running properly,  and you will be part of the network once you can connect.

Jim

---

