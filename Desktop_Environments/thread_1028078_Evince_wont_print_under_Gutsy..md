---
title: "Evince wont print under Gutsy."
date: 2009-01-02
forum: Desktop Environments
---

### Post by pgmer6809 on 2009-01-02
Hi:
Cant get Evince to print using a network attached printer under Gutsy.
Printer is lpd://192.168.2.50:LPT1
Printer works fine with all other apps.
Acroread, open office, abiword, firefox etc. etc.
But not with Evince (pdf doc viewer)
Anyone know why?

pgmer6809

---

### Post by stderr on 2009-01-02
I have no idea I'm afraid (maybe you might find a bug report on Launchpad?) however, we can probably circumvent the issue (if you haven't already).

Find out the port number - I suppose you could use nmap (sudo apt-get install nmap)

```
nmap 192.168.2.50
```

That should list the open ports - check for the name of the printer. Then you should, depending on the printer/printer server (if applic.), be able to do something like this:

```
lpr -H 192.168.2.50:PORT file.pdf
``` 
or
```
lpr -P PRINTERNAME file.pdf
```

---

### Post by pgmer6809 on 2009-01-04
I tried what you suggested, using lpr to send direct to the printer port, but it just hangs when i use the -H option. (I used nmap to find the printer port  as you suggested.)
when I lpr file.pdf the printer now starts; maybe this has something to do with CUPS being the 'printer' that lpr knows about.

In any case I think we are looking at the wrong thing here; the fact that all the other programs, even acroread, can print suggests to me that this is not a printer problem but an evince problem.

There must be some option or configuration in evince I am not getting.
Evince sees the printer OK, but it never sends the doc to the printer.

I suspect it has something to do with either CUPS or the fact that it is a network printer.

---

### Post by stderr on 2009-01-04
Can you verify that this happens with other PDFs too? 

If it isn't a PDF-specific problem, then maybe your CUPS logs may shed some light (/var/logs/cups). What actually happens - does it appear to send the job to print correctly? Can it see the network printer? Anything like high CPU util?

---

### Post by pgmer6809 on 2009-01-09
in response to stderr.
I looked at the /var/log/cups directory immediately after 'printing' the page in evince. The pdf and error and page files show zero size.
I also had the 'manage print jobs' applet running at the time, and nothing ever showed up in its window.

I then tried the same document using acroread.
The job shows up in the 'manage print jobs' applet, the page file /var/log/cups has some size to it now (nothing in the error or pdf files) and the job prints.

I could post some screeshots if I could figure out how to insert an image in a post.

---

### Post by pgmer6809 on 2009-01-09
Follow up.
Evince can see the printer fine.
It brings up the printer options screen and the name of the printer is there. It allows me to select the printer as the default printer.
I can even choose various options.
But when I print nothing shows up in the manage print applet, and the indicators on the printer do not show 'flashing busy' like they do when something actually prints.

Acroread on the other hand behaves the same as vim, or open office or anything else that actually succeeds in printing.
Stuff shows up in the manage print jobs applet, the busy indicator on the printer flashes and the printing actually gets done.

---

