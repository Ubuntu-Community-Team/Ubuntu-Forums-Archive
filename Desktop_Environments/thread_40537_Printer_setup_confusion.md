---
title: "Printer setup confusion"
date: 2005-06-09
forum: Desktop Environments
---

### Post by Uta on 2005-06-09
I have tried for 2 days to setup up printing in my newly installed Kubuntu OS. Kubuntu was installed as a stand alone OS in a Dell C800 laptop, installation was without error; I have Internet connect,sound and video but can not get the printer setup. The situation is this; I have 4 computers accessing a single print server (Linksys Wireless G Print server) 3 computers are running Mac OS X and are able to print to the epson 880 printer via the print server without issue. The 4th computer the Kubuntu/Dell C800 listens on  192.168.0.100:631 (which is my print server's IP address) this is via CUPS and generates this error; unable to retrieve printer list, also Error: the IPP request failed for an unknown reason.Using a different setup, via 'Generic UNIX LPD Print System gets this error message: lpr: error - unable to print file: server-error-service-unavailable. Sooooo... Which setup should I use and if it is CUPS how do I configure it? Thanks in advance.

Also when I boot from the Live Ubuntu CD (PPC) on my iBook, I can print without error, I just enter the  IP of the print server and chose that's it's an Epson 880 and I have a functional printer...now why is this such a big complex issue in Kubuntu?

---

### Post by Uta on 2005-06-10
Since there hasn't been any comments or replies and I am still without printing...let me post additional error messages that might start some kind of comment: If I try to use the wizard to add a printer I get this message:An error occurred while retrieving the list of available backends:server-error-operation-not-supported.
The other error message when I first start up the print manager is that it can not retrieve the printer list? I have looked to see if Gimp-Print is installed and it is? Where are the printer's list? Additionally when I try to browse mylocalhost plus printer port (631) I also get an error message that the connection was refused? Help!

---

### Post by cwaldbieser on 2005-06-10
If you

```
$ ps -Al | grep cupsd
```

Does it show the cupsd daemon running?  If it is running, you should be able to browse to localhost:631-- unless it is maybe configured for another port for some reason?

---

### Post by Uta on 2005-06-10
As you suggested:  $ ps -Al | grep cupsd and absolutely nothing happened, it popped me back to the prompt? In Print Manager when I click on the pull down tab that says restart server, I get the error message: Unable to restart print server. Error message received from manager: Unable to find a running CUPS server.

Soooo what do I do to start the CUPS server? On boot up it says starting CUPS and then 'OK' so I thought it was running? mmm? What to do? Thanks in advance--

OK/I restarted the cupsd system and I got this message:
cupsds: Child exited with status 13!
what does that mean?

---

### Post by cwaldbieser on 2005-06-11
Well, it sounds like cupsd is bailing out for some reason and that is why you cannot print.  Try this:

```
$ sudo cupsd -f
```

That will run the CUPS daemon in the foreground (it won't stop until you hit CTRL-C or just close the terminal).  Hopefully, it will print out some useful information to the terminal instead of simply dying.  If it doesn't die, try printing something and see if that kills it.  Let us know the results.

---

### Post by Uta on 2005-06-11
First thank you for helping me with this issue...! 

When I ran the command you suggested I got this message.

/usr/lib/cups/backend/scsi: Permission denied
/usr/lib/cups/backend/serial: Permission denied

I thought as much, how do I set the permissions?

---

### Post by cwaldbieser on 2005-06-11
Well, since those two lines look like files:
```

$ ls -al /usr/lib/cups/backend/scsi

$ ls -al /usr/lib/cups/backend/serial
```

should show you the permissions.  The output will look something like:

```
-rw-r--r--  1 root root 8512 Mar 22 00:13 /usr/lib/cups/backend/serial
```

In my example, the first "root" means the file is owned by root.  The second "root" means the group the file belongs to is the root group.  The -rw-r--r-- means that the root user has read and write permissions to the file, anyone in the root group has read permissions to the file, and everyone else has read permissions to the file.

Now curiously, in that same directory on my machine, every other backend file besides those two has an entry like this:

```
-rwxr-xr-x  1 root root 19484 Mar 22 00:13 /usr/lib/cups/backend/ipp
```

Here, the x's in the permission mean that root, the root group, and everyone else have permissions to execute the backend.  I am not sure why those other two don't have the permissions, but the following commands will give it to them:

```
$ sudo chmod ugo+x /usr/lib/cups/backend/scsi
$ sudo chmod ugo+x /usr/lib/cups/backend/serial
```

Hopefully, that will take care of your problem.

---

### Post by Uta on 2005-06-11
Again thank you for your help...unfortunately I am still getting error messages. After I chmod the files I did check to see if the permissions had been changed and they were, did a restart opened up the Printer Manager and it tried to connect to the CUPS Server but could not, failed. I also tried to type in my browser the localhost:631 the the connect was refused? What to do? Could this be a Samba sharing issue and  should I not be chosing CUPS but rather LPD or the LPR?
Thanks...please don't give up, I'm not--
Stranger still...
I can access the print server from my linux laptop through a browser typing in it's IP(print server's IP) and print a test page? mmm... The Printer manager can't access it but a browser running from the Linux box can, now I'm really confused...

---

### Post by cwaldbieser on 2005-06-11
First, after you changed the permissions, were the error messages you were getting the same (the permission denied errors, that is)?

Second, unless you can get cupsd running, you will not be able to [http://localhost:631](http://localhost:631).  When cupsd is running, it is the program that serves the web page to you.  Basically, if cupsd is not running, you will not be able to use CUPS at all.

It makes sense, since you are able to browse to your print server without a problem.

Maybe you should try re-installing cupsys with apt-get (or whatever package manager you use).  It sounds like your CUPS installation got borked somehow, but I don't know how...

---

### Post by Uta on 2005-06-12
The error messages were not permission errors, but rather connection errors, failed. I have reinstalled CUPS and again had to reset the permissions on the scsi and serial backend files and then from the command line: sudo cupsd -f and it just popped me back to the command prompt. strange?
Somehow I don't think this is a CUPS problem directly. Reinstalling I didn't think would make a difference since I booted from a LIVE UBUNTU CD and had the same issue... so I think we need to look at ports/permissions? I know 631 is the typical port but it's not letting the print server info through, why? Another thought although no OS other than LINUX is running on this laptop is there some Dell motherboard defaults that would not allow open ports? What's strange is, I can see my iBook(mac) from LINUX but I can't see or access the LINUX laptop from the iBook? It's like it's IP is invisible. Any thoughts? The hardware I am using is a Linksys Wireles Print Server, with a static (assigned IP) of 192.168.0.100 that I am able to web browse to via the LINUX Laptop, to it's admin page... how can I trouble shoot 631 port?As I mentioned before from my iBook laptop I am to localhost:631 and get the cups page but not from the linux laptop (the linux laptop is connected via an ethernet cable) Thanks for your help--

---

### Post by cwaldbieser on 2005-06-12
Well, if you think it is the ports, do you have a firewall running (e.g. Guarddog, Firestarter, Shorewall, etc.).  If you telnet to localhost 631, you will get a "connection refused" error in 2 circumstances-- 1) The port is configured to actively refuse the traffic and rejects the packets rather that dropping them; 2) The port accepts the traffic but there is actually no process listening on that port.

A firewall controls whether #1 is in effect.  I suppose CUPS could be configured to listen on a different port-- the /etc/cups/cupsd.conf configuration might have something about that.  Otherwise, the command:

```
$ ps -Al | grep cupsd
```

shows if the process is actually running.

Speaking of the config file /etc/cups/cupsd.conf, I found an interesting comment in mine:

> # RunAsUser: The RunAsUser directive controls whether the scheduler runs as the
# unpriviledged user account (usually cupsys). The default is No which
# leaves the scheduler running as the root user. However, the Debian package
# was prepared to work as user cupsys, which greatly reduces the impact of
# security holes.
#
# Note: Running as a non-priviledged user may prevent LPD and locally connected
# printers from working due to permission problems. The lpd backend will
# automatically use a non-priviledged mode that is not 100% compliant with RFC
# 1179. The parallel, serial, and usb backends will need write access to the
# corresponding device files.
#

RunAsUser Yes


You could try setting this to No and restart CUPS and see if it makes a difference.  If so, then you might just have to set some permissions (maybe add your user account to a printing group or change permissions on a device file) to get it working in non-root mode.

---

### Post by Uta on 2005-06-12
...it made no difference with your suggested change so I compared my cupsd.conf files (Mac OS and Kubuntu's) there were differences, the main one being browsing was off in Kubuntu and the port was not defined... so what I have now is that I am able to get to the print server by typing  localhost:631 in the browser and print a test page but I still can't get the darn Print Manager to let me configure or even initialize the CUPS server, strange? From my Mac I now see that there is an additional printer available to print to and it has the Linux box's IP...mmm?Additionally even though I updated to the lates KDE, there are big admin permission errors. Example I try to save a password and I get this error, "there was an error setting up inter-process communications for KDE. Authentication rejected...please check that the dcopserver program is running!" I can never get into the Admin features via a GUI interface? I thought the update was suppose to fix that? anyhoo back to printer woos... progressing along here, since CUPS is not getting initilized in the Print Manager I changed protocols, LDR(BDS)? and managed to print something from a text editor and then when I tried to do it again, nothing but as I restarted all the back logged print jobs started printing? Why can't I get the Cups server going and why can't I get Samba going via the GUI (again can't get administrator going via GUI).
Progress not prefection, right? I know I have thrown a lot out here to you but any help with starting the Cups server (the system finding it) and starting up the SAMBA server...thanks!

---

### Post by cwaldbieser on 2005-06-12
Sorry, I don't see the attached file.  Am I missing something?

You can't really ping a port.  The closest thing you can do is to try to establish a connection (e.g. telnet to the port).  It requires that a process actually be listening on the server.  If the server is listening, but you can't connect, the port is being blocked at the kernel level.  The closest you can come to seeing this is with firewall software (unless you are into kernel debugging, I guess).  The lowest level user-space tool at your disposal is a command called iptables.  if you do:

```
$ iptables -filter -n -L --line-numbers
$ iptables -nat -n -L --line-numbers
$ iptables -mangle -n -L --line-numbers
```

You can see the packet filtering rules for each of the 3 main tables of packet filtering.  If you have trouble interpreting them, I can read the output, but I have only just started experimenting with writing my own.  Normally, I just use a nice firewall package.  I used guarddog for a while, and it was pretty nice, but I switched over to using firestarter recently (just a personal preference for some of the features).

Also, I was looking over something you wrote a while back and I wanted to clarify-- To the best of my knowledge, when your CUPS system on the Ubuntu machine tries to print to your print server using IPP, your Ubuntu server is connecting to port 631 on the print server.  Information does not flow back to port 631 on the Ubuntu machine from the print server.  Any information that does flow back will be over the same connection that was originally established.  IPP is a protocol built on top of HTTP, so it is more or less a request-response model.  It's just like when your browser contacts a web server.  The server listens on port 80, but your browser receives info back on some dynamically allocated port that isn't otherwise being used.  You may already be aware of this, but I just wanted to clarify.

Let's take a look at when you said:

> The error messages were not permission errors, but rather connection errors, failed.

I was not very specific about asking where these errors came from.  Did you get them when you ran the cupsd command from the console, or when you tried to do something from print manager?  If the latter case, what was the exact action you tried to perform?  Also, after you start up CUPS, try doing:

```
$ dmesg
```

and post the results here.  This command basically spits out the end of your system log, so cups related errors might have been logged there.

---

### Post by desdinova on 2005-06-12
Also a useful tip is to up the log level in cupsd.conf to debug, restart cups and watch the contents of /var/log/cupsd/error_log

---

### Post by Uta on 2005-06-12
looked in the error log and this seems to be the most repeated and telling in terms of the CUPS server:
E [12/Jun/2005:17:51:19 -0500] StartListening: Unable to bind socket for address c0a80064:631 - Cannot assign requested address.
I had attached my .conf file but then went tinkering after I noticed no listening port was defined...ok here it is for real this time-- THANK YOU!

---

### Post by cwaldbieser on 2005-06-13
It may take me some time to digest all the material in the config file.  In the meantime, I had a thought.  You mentioned you had an Ubuntu Live CD for PPC.  Do you have one for x86 as well?  If you had that or a Knoppix CD, you could see if you could print from your Dell using that.  If it worked, you could copy the config from that, back up your old config, and replace it with the working config.   You could even try using the config from the PPC Live CD, replacing all references to its IP address with 192.168.0.100.  Might be worth a shot.  The CUPs system is esentially desktop agnostic, so it doesn't matter if the config comes from Kubuntu or Ubuntu as far as I can tell.

I don't know if this will make a difference, but I noticed in the "Listen" section of the config, my own config is set as:

Listen 127.0.0.1:631

while yours is:

Port 631

From the man pages it is not obvious whether this means yours indicates 192.168.0.100:631 or 127.0.0.1:631.  However, my config does have a note:

> # NOTE 2: In order for the command-line and web interfaces to work, you
# must have at least one Port or Listen line that allows access from the
# local loopback address (localhost).

So maybe some small difference like that is the key.  If other thoughts come to mind, I will let you know.

---

### Post by Uta on 2005-06-13
Ok this is where it's at now, I can print under LPR but that's not such a great printing method... the big news is that I ran the Kubuntu Live CD on the Dell and was able to config the Printing Manager usings CUPS so that means (as you suggested earlier) that my installed CUPS Server is crippled/busted, etc... so how do I reinstall it. I had thought I had done that but I guess I didn't get a clean install. Please direct? Thanks in advance!

PS/Samba's next for trouble shooting...LOL!

---

### Post by Uta on 2005-06-13
I am very happy! This was the problem in short "Administrator Mode" for Kcontrol (sudo kcontrol) so I could set the address of the print server to 'Localhost' rather than the actual IP(which it was set to)...once I did that I was actually able to choose CUPS in the printing manager and add a printer...O, Joy! Thank you so much for helping me and this great forum which is a wealth of information!
(also I know this is old news but the update to KDE does not fix the Administrator Mode issue) the sudo kcontrol is though, a good work-around. Cheers! :-P

---

### Post by jobo on 2005-06-13
[QUOTE=cwaldbieser]
You can't really ping a port.  The closest thing you can do is to try to establish a connection (e.g. telnet to the port).  It requires that a process actually be listening on the server.[/QUOTE]

Just a short digression. This is true - about ping to ports, but there are tools available for detecting "open ports" in a jiff. Now, I could never find a use for them, so I'm clueless as to which to recomend, but ethereal is a complex tool. I suspect it might even be able to identify some standard services and the ports they run on - like cupsd ;)

---

### Post by jonsson on 2005-06-13
[QUOTE=Uta]I am very happy! This was the problem in short "Administrator Mode" for Kcontrol (sudo kcontrol) so I could set the address of the print server to 'Localhost' rather than the actual IP(which it was set to)...once I did that I was actually able to choose CUPS in the printing manager and add a printer...[/QUOTE]
I've been reading through this thread since I seem to have the same problem with my newly installed Kubuntu system. However, "sudo kcontrol" and choosing CUPS just gives me an endless wait while it's "Initializing manager..." ?  ](*,)

---

### Post by Uta on 2005-06-13
...after you sudo kcontrol, make sure you see that 'root' is the user not your chosen name that is displayed,then go to into Peripherals, then Printers, then into Print Manager,then configure manager, once there choose CUPS Server and under Host it should be 'Localhost' and for Port it should be 631 and I have, Use anonymous access chosen. This worked for me. Then you should be able to add a printer. I have a Linksys Wireless Print Server and finally I am PRINTING! Good Luck!

---

### Post by jonsson on 2005-06-14
Thanks, changing it to anonymous made it work.  :)

---

### Post by aliasd on 2005-06-19
[QUOTE=jobo]there are tools available for detecting "open ports" in a jiff........ ethereal is a complex tool. I suspect it might even be able to identify some standard services and the ports they run on - like cupsd ;)[/QUOTE]

A simple nmap would be sufficient to discover things like this.
A sample nmap with Version probing, to discover what is running, and on what ports on an ubuntu box:

```
root@skyeco02:~ # nmap -sV localhost

Starting nmap 3.75 ( http://www.insecure.org/nmap/ ) at 2005-06-19 15:51 EST
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1658 ports scanned but not shown below are in state: closed)
PORT    STATE SERVICE     VERSION
22/tcp  open  ssh         OpenSSH 3.9p1 (protocol 2.0)
25/tcp  open  smtp        Postfix smtpd
139/tcp open  netbios-ssn Samba smbd 3.X (workgroup: HNASP)
445/tcp open  netbios-ssn Samba smbd 3.X (workgroup: HNASP)
631/tcp open  ipp         CUPS 1.1

Nmap run completed -- 1 IP address (1 host up) scanned in 12.010 seconds
root@skyeco02:~ #
```

If you want a GUI for this sort of thing, you cant go past nessus, although nmap will probably be able to do anything you need it to.

---

### Post by Uta on 2005-06-19
Thanks for the info, I did manage to get my cupsd server running.
Out of curiousity I tried your command in the root terminal and I got the error message, bash: nmap: command not found

I had entered: root@Kubuntu:~ # nmap -sV localhost

---

### Post by jonsson on 2005-06-19
[QUOTE=Uta]Thanks for the info, I did manage to get my cupsd server running.
Out of curiousity I tried your command in the root terminal and I got the error message, bash: nmap: command not found

I had entered: root@Kubuntu:~ # nmap -sV localhost[/QUOTE]

I don't think it is installed by default. IIRC that was one of the things I installed just after installing Kubuntu.

---

### Post by vtechstu on 2005-06-30
I'm having the same problem as Jonsson, though the way he fixed it doesn't seem to be working for me.  It still just  freezes there after selecting printers from the peripherals menu.  

After a while it unfreezes, and says to make sure cups is installed correctly.  What packages are involved to complete the install?  I've tried removing cups and re apt-getting it but nothing works!! Please help!

---

### Post by Uta on 2005-07-01
I do not know why your system is freezing, it could be unrelated to your printing issue. I can only share what got me up and running. Please read the earlier posts in this section, there is some good troubling shooting info to use, such as, is CUPS actually running?
 $ ps -Al | grep cupsd
If it is running, you should get a response to that command if it bounces you back to the command line, it might not be running and you'll have to trouble shoot why it isn't starting at boot time. If it is running, sudo kcontrol and go the Printers section (important to do this as 'root').
If you already have added a printer make sure it is selected and at the bottom of the dialog window you see: Print system currently used: CUPS (Command Unix Print System) and Server: Localhost:631.
My issue was I had entered the IP of the print server here not the localhost port. If that is set to port 631, see if from a browser you can access the cups server. [http://localhost:631/](http://localhost:631/) this should bring up the CUPS web page.
If you can get this far then try checking your panel settings; Properties
1) General, Printer name: your printer name you chose, Location: where it's at, Description: EPSON Stylus Color 880(my printer)
2) Interface, Printer type: Network Printer (socket), URL socket://192.168.0.100: (this is the IP of your print server, I have a wireless Linksys)
3) Driver, Manufacturer: Epson (whatever your manufactor's name is), Printer model: Stylus Color 880, Driver info Epson Stylus Color 880 - CUPS+Gimp-Print v4.2.7
4) Banners (no banners for me starting or ending)
5) Quotas (your choosing)
6) Users: All Users Allowed
***********************************
Again read the earlier postings in this section and if your problem turns out CUPS isn't running , try reading these posts (they're about SAMBA but can be applied to CUPS issues). 
[http://ubuntuforums.org/showthread.php?t=43330](http://ubuntuforums.org/showthread.php?t=43330)
Good Luck, Cheers!

---

### Post by alexanderfrey on 2005-07-03
Ok, a check whether cupsd is running yells the following:
alex@ubuntu:~$ sudo ps -Al | grep cupsd
4 S     0  6293     1  0  76   0 -  1438 -      ?        00:00:00 cupsd

cupsd seems to run, although when I enter cupsd in the terminal it says:
alex@ubuntu:~$ cupsd
cupsd: Child exited with status 13!


When I try to connect to [http://localhost:631/](http://localhost:631/)  nothing happens....
When I sudo kcontrol, it still waits for minutes and tells me to check whether cups is running....



Any ideas how to get up printing in kubuntu ?
By the way, under a live cd with ubuntu I was able to print very fine !


Thanks ,Alexander

---

### Post by Uta on 2005-07-03
Your errors are exacly as mine were. You need to post your cupsd.conf file, but first tell me if at the bottom of your printer dialog box you see this and if not what do you see?
"Print system currently used: CUPS (Command Unix Print System) and Server: Localhost:631"

---

### Post by jobo on 2005-07-09
Set permissions exactly like you would any other "file". 
For example chmod 755 /path/to/file This will leave it writable to owner, and readable & executable to group and others.

At least these permissions are not to stringent (tight).

J

---

