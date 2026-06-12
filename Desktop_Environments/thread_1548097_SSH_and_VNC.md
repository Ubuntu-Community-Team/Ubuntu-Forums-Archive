---
title: "SSH and VNC"
date: 2010-08-07
forum: Desktop Environments
---

### Post by spillage2 on 2010-08-07
Hi all,

Not sure if this is the right forum for this but.....

I have set up ssh on one of my comps but cannot connect using ssh.

I can ssh and I can vnc but can't vnc through ssh.

Its late and driving me mad.

At the moment I am using the standard ports until I can connect.

Any ideas would be helpful.

Spill.

---

### Post by Brandon Williams on 2010-08-10
It would be easier to help if you were to provide greater detail about what you've tried.

On my system, I use ssh to open a tunnel to my vnc server by running the following on my client machine:
```
ssh -N -t -x -L5901:localhost:5901 vncserver
```

Having done this, I can open a vnc client session to my vnc server by running this command on my client machine:
```
vncviewer localhost:5901
```

---

### Post by endotherm on 2010-08-10
I tend to use:
```

vncviewer -via user@sshserver localhost:0

```
to access the first viewer on the ssh server.

---

### Post by spillage2 on 2010-08-10
Ok thanks for the info..at work now but will try tonight as soon as I get the chance.

Just starting to get to grips with linux and so far have not looked back..

---

### Post by spillage2 on 2010-08-10
ok back home now but getting this message.

home@home:~$ ssh -N -t -x -L5901:localhost:5901 vncserver
ssh: Could not resolve hostname vncserver: Name or service not known

---

### Post by hudsonl on 2010-08-10
> **spillage2 said:**
> ok back home now but getting this message.

home@home:~$ ssh -N -t -x -L5901:localhost:5901 vncserver
ssh: Could not resolve hostname vncserver: Name or service not known

It either can not resolve the hostname "vncserver" or ssh is not running on the server "vncserver"

Can you ping vncserver (is it able to resolve the hostname)
Is ssh server installed on the server "vncserver"

---

### Post by spillage2 on 2010-08-10
ssh is up and running fine. i have installed xtightvncviewer and also tried changing vncviewer to that.

although when i try 
vncviewer -via user@sshserver localhost:0
i get cannot open display?

---

### Post by endotherm on 2010-08-11
> **spillage2 said:**
> ssh is up and running fine. i have installed xtightvncviewer and also tried changing vncviewer to that.

although when i try 
vncviewer -via user@sshserver localhost:0
i get cannot open display?
go to System -> Preferences -> remote desktop, and confirm that your vnc instance is running on display 0. 

try ssh'ing into the box, and run:
'echo $DISPLAY'
does anything return?
you may also want to try :1 instead of :0, or even drop the display id entirely. 
let us know. 

here is some info i found related to your issue:
[http://fixunix.com/setup/18312-error-cant-open-display.html](http://fixunix.com/setup/18312-error-cant-open-display.html)
[http://ubuntuforums.org/archive/index.php/t-280529.html](http://ubuntuforums.org/archive/index.php/t-280529.html)

---

### Post by Brandon Williams on 2010-08-11
> **spillage2 said:**
> ok back home now but getting this message.

home@home:~$ ssh -N -t -x -L5901:localhost:5901 vncserver
ssh: Could not resolve hostname vncserver: Name or service not known

Did you use 'vncserver' as the hostname on the ssh command line? Or did you replace 'vncserver' with the real hostname or IP address of the server? I should have been more clear that 'vncserver' in my sample command line is just a placeholder for the real hostname of the machine.

---

### Post by obogobo on 2010-08-15
I am having the same issue.

When I type $DISPLAY over SSH on my Windows 7 laptop in PuTTY... nothing is returned. BUT when I type the same command in a terminal on Ubuntu... :0.0 is printed. What I think is happening (my Linux experience is not very extensive) is that OpenSSH is not running in an X session but Remote Desktop (VNC) is? Could this be the issue? Because I can remote desktop untunneled into my Ubuntu box just fine, and I can SSH into it equally as well... but when I try to combine the two: forwarding port 5900 on the Ubuntu box to 5901 on my Windows 7 PC and connect with VNC Viewer on localhost:1, the login box never appears and eventually I get an message saying  "The connection closed unexpectedly".

Does X need to be forwarded through SSH somehow? I'm not sure what to do from here haha

---

### Post by endotherm on 2010-08-17
> **obogobo said:**
> I am having the same issue.

When I type $DISPLAY over SSH on my Windows 7 laptop in PuTTY... nothing is returned. BUT when I type the same command in a terminal on Ubuntu... :0.0 is printed. What I think is happening (my Linux experience is not very extensive) is that OpenSSH is not running in an X session but Remote Desktop (VNC) is? Could this be the issue? Because I can remote desktop untunneled into my Ubuntu box just fine, and I can SSH into it equally as well... but when I try to combine the two: forwarding port 5900 on the Ubuntu box to 5901 on my Windows 7 PC and connect with VNC Viewer on localhost:1, the login box never appears and eventually I get an message saying  "The connection closed unexpectedly".

Does X need to be forwarded through SSH somehow? I'm not sure what to do from here haha
no you don't need to forward x or set up port tunneling via ssh if you use the 'vncviewer -via' command. it sounds like yours should be
```
vncviewer -via user@sshserver localhost:0.0
```. if that fails, drop the ":0.0" and try again.

---

### Post by obogobo on 2010-08-17
Are there any settings in sshd_config I need to change to get this to work? By the way on a clean install of Ubuntu 10.4, VNC over SSH works flawlessly, the notification even says that the desktop is being controlled by a user on itself so I know the tunnel is okay... After I install updates though something breaks

---

### Post by obogobo on 2010-08-17
It works through the tunnel from connections outside my house.... I feel dumb sorry for wasting anyone's time haha wow

---

