---
title: "Education - programming difficulty"
date: 2010-03-30
forum: Education &amp; Science
---

### Post by tx_tycoon on 2010-03-30
Hi all -

I have a programming assignment for a class and I'm pretty new to the linux scene and new to this forum, so I'm pleading for some serious help. The assignment is the following:

 [FONT=&quot]Write a program to reassemble a network packet dump. Your program input will be a file given by the instructor and your program will output all of the reassembled packets.  You must output human readable **Data Link, Network and Transport layer **information in the **snort** format.  Application layer information must be output as a **hex dump with 16 bytes per line and ASCII text in the right margin **for each line of application layer data.  You should also **include statistics** at the end of your output indicating number of packets received and number of packets that constitute each type of traffic [I](TCP, UDP, Telnet, FTP, etc).
[/I]
 * The input is a network trace.
 * The Ethernet, IP, and TCP output should follow the snort model. 
 * You may need to consult the relevant RFCs for the tcp/telnet/ftp protocols.
 * You can use libpcap library in your program. You can refer to existing open source projects (e.g.,   
     tcpdump, snort) and modify them according to your purpose.[/FONT]


Any help, even a shove in the right direction, would be greatly appreciated. 

Thanks in advance.

---

### Post by GregBrannon on 2010-03-30
Go to class?  Open the book?

Sorry, couldn't help it.

Welcome to the forums and the community.  You won't get specific help with homework.  Actually, you're not even supposed to ask.  But you may get some gentle nudges in the right direction.  Or not.

Good luck.

---

### Post by n0dix on 2010-03-30
It seems complex your assignment, but is your task not our. However, look information about the topics you are taking. A good book is Tanenbaum Computer Networks: [http://authors.phptr.com/tanenbaumcn4/](http://authors.phptr.com/tanenbaumcn4/)

Good luck!!

---

### Post by gunksta on 2010-03-31
When I graduated, I thought I was done with homework. Turns out -- I was wrong. Computers make it waaaay to easy to take work home, especially interesting work.

And this, is interesting. But I won't do it for you. But I can be persuaded into tossing out a few cookies.

Rule #1 - BREAK COMPLEX PROBLEMS DOWN INTO LITTLE PIECES

I really think they should beat everyone over the head with this in high school. When in doubt, break it down.

You can do this with bash and a few of the tools mentioned in your OP. It's clear that your professor doesn't want you to reinvent the wheel, you're supposed to learn how to use what's out there (and learn a little about packet introspection while you are at it). If you already know a scripting language that has more advanced text wrangling skills, you may want to skip bash and use it instead. Save yourself the heartache.

I would start by making a list of all the programs your professor mentioned in making the assignment, including any the prof mentioned in class. After doing that, I would look up ALL of the tools and see what they do. I would put snort somewhere close to the top of that list.

Google - it is your friend.

---

### Post by tx_tycoon on 2010-04-03
Thanks for the replies, I really appreciate it. But honestly, I dont even know how to begin making this thing, I am extremely green to linux, and, well, like i said, I dont even know what i'm doing. Any direction to even get started would be awesome, but if not, I completely understand. Ill appreciate the comments either way.

---

### Post by gunksta on 2010-04-03
Do you have access to a linux system?

---

### Post by tx_tycoon on 2010-04-05
I have access to a Fedora 4 system at school and I am in the process of trying to dual boot my pc with ubuntu / win7

---

