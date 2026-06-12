---
title: "Launch 2 SSH sessions in same shell script"
date: 2009-06-03
forum: General Help
---

### Post by topgun_tapan on 2009-06-03
Basically this is what I want to do :
Write a shell script that will first ssh to one computer then open a new tab in that gnome-terminal and ssh to another computer.

Can anyone help me out with this ? It will of great help. Currently i'm using two different shell scripts for each ssh. I'm using Ubuntu 9.04 Jaunty. If this can be achieved in some other way too other than shell scripting please let me know.

---

### Post by cak3 on 2009-06-03
I dont think you can open a new tab in a remote terminal, since you aren't really using a terminal emulator such as gnome terminal there, you are on a terminal session (ie, like you would be locally if you logged in without X).

I have never tried it, but I assume that using the ssh command on the remote computer would allow you to ssh to another, (which would be routed through the first remote machine and then to yours). 

What you do mean writing scripts to ssh? you can just use the "ssh" command. You can make ssh-ing a lot easier by setting up a key-pair and/or setting up aliases in your ~/.ssh/config file (see [http://www.innovatingtomorrow.net/2008/01/21/type-less-ssh-aliases](http://www.innovatingtomorrow.net/2008/01/21/type-less-ssh-aliases) ).

---

### Post by topgun_tapan on 2009-06-03
Hey. I am sorry, I wasnt very clear in the first post. What i want to do is write a shell script which first will ssh to one computer. After that connection is made and is still active it will open another tab on the terminal of my computer and ssh to yet another computer so that I'll have two active ssh sessions from my computer to two other computers. I know this sounds like something which can be done manually without much hassle and it is silly to write a shell script for something like this. But I just wanted to know if it could be done.

---

### Post by Brandon Williams on 2009-06-03
In a single gnome-terminal command line, you can run multiple commands in multiple tabs. Here is an example: 'gnome-terminal -e "ssh host1" --tab -e "ssh host2"'.

---

### Post by HermanAB on 2009-06-03
Hmmm, tricky stuff.

Make a separate script to run on the remote machine, then copy it to the remote machine and run it through SSH like this:

scp script.sh user@server:~/.
ssh user@server "script.sh any parameters needed"

---

### Post by topgun_tapan on 2009-06-03
> **Brandon Williams said:**
> In a single gnome-terminal command line, you can run multiple commands in multiple tabs. Here is an example: 'gnome-terminal -e "ssh host1" --tab -e "ssh host2"'.
Thank you for the suggestion. When I tried this I got the following error :
"There was an error in creating the child process for this terminal"
I then ran the command as sudo 'gnome-terminal -e "ssh host1" --tab -e "ssh host2"'. I got the following error :
"Failed to contact the GConf daemon; exiting."
I searched for this on google but it seems it was some jaunty alpha bug which was to be fixed/got fixed. I have the jaunty final version with all updates installed. Any suggestions ?

@HermanAB : I need to ssh to both the remote computers from my own pc. Can i do that by running a script on one of the remote hosts ? Also it is important that the connections happen one after the other and not simultaneous.

---

### Post by Brandon Williams on 2009-06-04
I just tried it on Jaunty (my previous test was on Hardy), and I had to add an extra "--tab" argument for some reason: 'gnome-terminal --tab -e "ssh host1" --tab -e "ssh host2"' This worked from an xfce session, I can try from a gnome session this evening when I get home if no-one else has verified the functionality in a gnome desktop before then.

---

### Post by HermanAB on 2009-06-04
If you need to do exactly the same thing on multiple computers using SSH, then you can also use Cluster SSH or Parallel SSH.

---

### Post by topgun_tapan on 2009-06-05
> **Brandon Williams said:**
> I just tried it on Jaunty (my previous test was on Hardy), and I had to add an extra "--tab" argument for some reason: 'gnome-terminal --tab -e "ssh host1" --tab -e "ssh host2"' This worked from an xfce session, I can try from a gnome session this evening when I get home if no-one else has verified the functionality in a gnome desktop before then.

Thanks a lot. This worked in gnome as well.

---

