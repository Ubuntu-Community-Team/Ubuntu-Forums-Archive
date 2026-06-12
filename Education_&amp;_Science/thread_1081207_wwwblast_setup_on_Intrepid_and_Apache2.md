---
title: "wwwblast setup on Intrepid and Apache2"
date: 2009-02-26
forum: Education &amp; Science
---

### Post by jpopesku on 2009-02-26
Hi all,
I’m hoping maybe someone here can help me out. 

I had installed wwwblast on Edgy a couple of years ago under Apache. When Apache2 came out, I upgraded. When Feisty and then Hardy and Intrepid came along, I upgraded. Everything was smooth sailing with my BLAST server.

Then the HDD crashed.

So I bought a new drive and installed a fresh version of (desktop) Intrepid, followed by the necessary updates:
```

sudo apt-get upgrade
```

Followed by: 
```

sudo apt-get install apache2
```

Then I downloaded the appropriate wwwblast from [ftp://ftp.ncbi.nih.gov/blast/executables/LATEST/](ftp://ftp.ncbi.nih.gov/blast/executables/LATEST/) (currently 2.2.19; I d/l wwwblast-2.2.19-x64-linux.tar.gz).

I followed the instructions in a howto from Andrew Perry's blog ([http://blog.pansapiens.com/2008/08/25/setting-up-wwwblast-on-ubuntu-apache/](http://blog.pansapiens.com/2008/08/25/setting-up-wwwblast-on-ubuntu-apache/)) making sure to preserve permissions (tar zxvpf).  But when I run a BLAST query, I get a Error 500 (Internal Server Error).

In my /var/log/apache2/error.log, it’s saying:
> 
No such file or directory: exec of ‘/var/www/blast/blast.cgi’ failed, referer: [http://localhost/blast/blast.html](http://localhost/blast/blast.html)

Premature end of script headers: blast.cgi, referer: [http://localhost/blast/blast.html](http://localhost/blast/blast.html)

Googling the error doesn’t really help as it just tells me that there’s a problem with the code, which I don’t think I can change (can I?!).  When I Google the error + wwwblast, nothing relevant comes up, so I'm guessing that it's not really the code, but rather some setting on my machine.  Apart from uncommenting the AddHandler for cgi in mime.conf (is that necessary?), the install is fresh.

The way (I think) the program works, is it takes input from blast.html, passes it blast.cgi, which, in turn, passes it to blast.REAL for actual processing.

Any help would be greatly appreciated; I really need to get this BLAST server up and running to finish off a project! Thanks in advance!

Specs:
- Ubuntu Intrepid Ibex 8.10 AMD64
- wwwblast 2.2.19 x64
- apache2

JP

---

### Post by jpopesku on 2009-02-26
Thanks to [http://lotomas.net/2008/07/20/instalando-blast-en-apache-20-y-ubuntu-804-hardy-heron/](http://lotomas.net/2008/07/20/instalando-blast-en-apache-20-y-ubuntu-804-hardy-heron/), I figured it out (although I can't read Spanish).

Basically, from what I gather, blast.cgi is called using csh.  So after a quick 
```
sudo apt-get install csh
```
it works!
JP

---

