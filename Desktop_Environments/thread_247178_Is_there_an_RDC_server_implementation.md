---
title: "Is there an RDC server implementation?"
date: 2006-08-30
forum: Desktop Environments
---

### Post by PryGuy on 2006-08-30
Good day, everyone!
I've switched my file server to Ubuntu Dapper everything's fine but I have one question: Is there a Remote Desktop Protocol Server so I could connect to Ubuntu from my Windows PCs. VNC is good but I don't feel like installing it 'cause it's easier to install  a RDP server on one Ubuntu PC rather then installing VNC on all the Windoze clients.

---

### Post by bernied on 2006-08-30
Does this help:
[http://www.gnomepro.com/tsclient/](http://www.gnomepro.com/tsclient/)
and
[http://www.rdesktop.org/](http://www.rdesktop.org/)

---

### Post by markius on 2006-08-30
Have a look at xrdp, it claims to allow you to RDP in to the Ubuntu machine from Windows.

[http://xrdp.sourceforge.net]("http://xrdp.sourceforge.net")

I had some problems getting it to work.  I'd be interested to hear how you get on.

M

---

### Post by PryGuy on 2006-08-30
Well, first of all, the link didn't open for me :(

---

### Post by bernied on 2006-08-30
[http://sourceforge.net/projects/xrdp](http://sourceforge.net/projects/xrdp)

---

### Post by PryGuy on 2006-08-30
sorry, already opened it and installed the deb file. But there's absolutely no info so I'm really lost. Is this a demon?

---

### Post by markius on 2006-08-30
The [http://xrdp.sourceforge.net]("http://xrdp.sourceforge.net") page has some documentation but the information is very limited.  The page seems to be working again.

It seems that xrdp runs as a wrapper around the vico/vnc server built into Ubuntu.

As I say, I had problems getting it to work although I'm very new to Ubuntu and Linux in general so I'm not discounting the possibility that I messed up the install somehow.

M

---

### Post by PryGuy on 2006-08-30
> **markius said:**
> It seems that xrdp runs as a wrapper around the vico/vnc server built into Ubuntu.
So does this mean that I should start the VNC server demon first?
> **markius said:**
> As I say, I had problems getting it to work although I'm very new to Ubuntu and Linux in general so I'm not discounting the possibility that I messed up the install somehow.I don't see how can you mess up the .deb installation. You just double click the file and press the install button.

---

### Post by markius on 2006-08-30
> **PryGuy said:**
> So does this mean that I should start the VNC server demon first?

I think so but I'm not 100% sure.

When you RDP in, you should see a basic login screen where you can put in your username and password.
Once you've done that xrdp tries to connect to port 5910 on localhost - I think that's VNC.

> **PryGuy said:**
> 
I don't see how can you mess up the .deb installation. You just double click the file and press the install button.

Sure the .deb installer was pretty straightforward.  But once it was installed, I couldn't get past the login screen.  It just timed out whilst trying to bring the VNC session up.

Let me know how you get on

M

---

### Post by PryGuy on 2006-08-30
I started the VNC server on the PC that I want to connect to, but still can't connect there neither from Windows nor from Ubuntu using the VNC protocol instead of RDP.

---

### Post by markius on 2006-08-30
Did you install a firewall on your Ubuntu machine?

---

### Post by PryGuy on 2006-08-30
No, why?

---

### Post by markius on 2006-08-30
I wondered if there might be a firewall blocking access to your Ubuntu machine.

If I have time I'll have another go at getting xrdp to work at the weekend - I've reinstalled Ubuntu several times since my last attempt... maybe something will be different this time.

---

### Post by PryGuy on 2006-08-31
It is strange why the program has not enough information to understand even how it works. 
> **markius said:**
> Once you've done that xrdp tries to connect to port 5910 on localhost - I think that's VNC.
Just thought of that. If it's an RDP server it should open up port 5910 not connect to port 5910. What do you think?

---

### Post by markius on 2006-08-31
> **PryGuy said:**
> Just thought of that. If it's an RDP server it should open up port 5910 not connect to port 5910. What do you think?

On Windows server RDP listens on port 3389.

Port 5910 is for VNC - it's an SSH tunneled version of port 5900.

I wonder if Ubunto/vino is enabling the SSH tunneled port by default?  Maybe that's why xrdp didn't work for me. :idea: 

Will definately be checking this out at the weekend!
M

---

### Post by sonicbs on 2006-09-05
Hi, I am also trying to make this xrdp work. I think I'm a little behind from what you managed to accomplish. I'm a Linux\Ubuntu newbie so, my question is very basic. I installed both the .deb package file, and after I couldn't make it work, I downloaded the tar ball, and compiled and installed the xrdp on my machine. But I didn't even know how to make the deaomon start. I saw there were a couple of .sh scripts in the xrdp directory, but how do I run such scripts? how do I make the deamon start with the boot process?
Thanks for the help, and hope you figure out this xrdp thing. Really akward, they didn't put a detailed install and usage on their sourceforege page.
S.

---

