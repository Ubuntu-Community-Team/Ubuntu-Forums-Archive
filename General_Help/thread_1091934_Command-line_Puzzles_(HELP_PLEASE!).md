---
title: "Command-line Puzzles (HELP PLEASE!)"
date: 2009-03-09
forum: General Help
---

### Post by McMagic on 2009-03-09
My teacher has us doing a series of questions regarding terminal commands and DNS lookups. any help will be greatly appreciated!!

1. Write a command using 'ps', 'grep', 'awk' and 'kill' that will 
send the 'hangup' (HUP) signal to your currently running 'named' (BIND)process.

i know this has to follow this general form,

>>>for i in `ps auwx | grep BIND | awk '{print $2}'`; do sudo kill $i; done 

but this form sends a SIGINT signal, not a HUP.

2. My computer wants to perform a DNS lookup.  What type of Layer
Four (4) packet is used to perform this query, and to which port on the DNS
server will this packet be sent?

3. When a packet arrives at a gateway that is destined for an IP
address on the local area network and the gateway does not know which machine
owns that IP address, what protocol does the gateway use to find this
information?

4. Using lsof, write a command that will show me which regular files process 1 has open.

5. Write a BASH for loop that finds all files in a directory AND all subdirectories that end in '.html' and creates a copy of each file (in the same directory in which it is found) with an added prefix of 'backup.'.  For example,
   "./subdir1/subhtml1.html" would have a copy of
   "./subdir1/backup.subhtml1.html" created.
You must use the 'dirname' utility as well as other utilities for this task.

---

### Post by Joeb454 on 2009-03-09
Please don't post homework requests :)

From the Code of Conduct (emphasis mine):

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, **the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you.** Any such threads will be taken offline and warnings or infractions may be issued.

Thread Closed :)

---

