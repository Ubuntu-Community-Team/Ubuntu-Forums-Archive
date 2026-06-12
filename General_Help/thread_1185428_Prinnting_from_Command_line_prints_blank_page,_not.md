---
title: "Prinnting from Command line prints blank page, not whats in the file."
date: 2009-06-12
forum: General Help
---

### Post by Coder68 on 2009-06-12
I am only a few hours into using Linux.
I am running Ubuntu 6.06 LTS (It is the only Ubuntu the runs on my Shuttle box correctly.) 
 
I installed a HP JetDirect Samsung 1430 printer and tested it from the GUI. It works perfectly. I printed file1 in my home dir, via the GUI, and it prints that fine.
 
If I use the command line to print the same file, the page just comes out blank. My default printer is set correctly. 
 

```
lpinfo -v | grep socket  returns: network socket 
```To print the file I use:
 

```
coder68@ubuntu:~/test$ lp file1
or
coder68@ubuntu:~/test$ lpr file1
```It sends the print job to the printer, but the page is blank. And yes, the file does have some text in it! :wink:
 
All I could find about blank pages were issues with an extra page or blank lines.
 
Any ideas what I am doing wrong? I tried this in the absolute beginners thread, but found no help. :(

Thank you,

C68

---

### Post by Coder68 on 2009-06-12
Bump.

Nobody has any ideas? :(

---

### Post by Coder68 on 2009-06-14
Bump! :(

---

### Post by ddrichardson on 2009-06-14
Can you cat to the port?```
cat file1 > /dev/lp0
```

---

### Post by HermanAB on 2009-06-14
Howdy,

If you want to print something then it has to be either a postscript or a PDF file.  You can make a postscript file using enscript.

See this: [http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)

---

### Post by ddrichardson on 2009-06-14
> **HermanAB said:**
> Howdy,

If you want to print something then it has to be either a postscript or a PDF file.  You can make a postscript file using enscript.

See this: [http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)
Not if you send it directly to the port.

---

### Post by Coder68 on 2009-06-14
ddrichardson,

Thank you for the reply!  When I run the code you offered up, I get Permission denied.

```

coder68@Ubuntu:~/test$ cat file1 > /dev/lp0
bash: /dev/lp0: Permission denied
coder68@Ubuntu:~/test$

```This would normaly lead me to belive that the device is not setup correctly, but it does print the file from the GUI.

Would the the fact it I am using a HP JetDirect change the way it prints from the command line?

C68

---

### Post by ddrichardson on 2009-06-15
Permission denied would mean you need to do it as sudo.```
cat file1 > /dev/lp
```

---

### Post by Coder68 on 2009-06-15
Thank you again, but that does  nothing for me.

```
root@Ubuntu:/home/coder68/test# cat file1 > /dev/lp
```I hit enter an nothing happens.  When I try lp file1  as root, it prints a blank page as well.

Could there be an issue with the command line and it not being in a proper postscript?

Thanks again for all your help!

C68

---

### Post by ddrichardson on 2009-06-16
It shouldn't be an issue, I'm not familiar with the printing system but that command is sending the file as a stream to the port.  I'd check lp is a port and not a symbolic link to the printer spool.

---

### Post by Coder68 on 2009-06-16
I am not sure how to do that.  

A hard link is a direct link to the item, right?
A symbolic link is a link to the hard link?

Thanks again!

C68

---

### Post by ddrichardson on 2009-06-17
```
ls -l /dev/lp
```If its a link then it'll have a "->" after it and the location of what it points to.

---

### Post by Coder68 on 2009-06-17
OK.

I am not sure how to look at my printer in command line.  When I do searches, everything talks about cups printing... not HP JetDirects.

C68

---

### Post by ddrichardson on 2009-06-18
Common Unix Printing System (CUPS) is not manufacturer specific, I'm not describing hot to access the printer, merely how to send data directly to the port it's attached to.

---

### Post by Coder68 on 2009-06-18
Oh, I see now.

Maybe this version Ubuntu does not working correctly. (6.06)  I mean it sends it to the printer, but a blank page spits out. A friend of mine has no issues doing this, but it is not Ubuntu.

Once I get my new laptop with Ubuntu 8.1 on it, I can test that theory.

Thanks,

C68

---

### Post by Coder68 on 2009-06-26
I have no idea what is wrong with my Ubuntu 6.06 box, but the lp file1 works perfectly on my new Dell 15n with Ubuntu 8.10.

Thanks for the help,

C68

---

