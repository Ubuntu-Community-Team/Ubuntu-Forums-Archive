---
title: "Remote X session"
date: 2010-12-30
forum: Desktop Environments
---

### Post by Ckesey on 2010-12-30
I have a unix server I'm trying to connect being able to control the remote x session of a program. 

These are the steps i'm using on my Unbuntu 10.10:
1) xhost +
2) telnet to remote host
3) Once logged in i use the "setenv DISPLAY x.x.x.x:0.0 (x.x.x.x being my Ubuntu ip)
4) Then I issue the command in the telnet session that starts the program 

I get the error:
application-specific initalization failed: coudn't connect to display "x.x.x.x:0.0"

Any ideas of something on my Ubuntu I need to check???

I have an older fedora machine that runs these same commands and the x window application starts without issue.

---

### Post by Ckesey on 2010-12-31
Anyone have any suggestions?????

---

### Post by Ckesey on 2011-01-03
I think I answered my own question after lots of trial and error.

In the /etc/gdm/custom.conf i added the following.

[security]
DisallowTCP=false

[xdmcp]
Enable=true

After i restarted I was able to connect to the remote x applications.

---

### Post by zabrab on 2011-01-03
I know you solved this but ...
if you are connecting to the server using ssh rather than telnet
you can use 
"ssh -Y -l {YourLoginID} {YourServerName}"
This should automatically set up the DISPLAY= environment that you need ... and you will be using (secure) ssh rather than (open) telnet

---

