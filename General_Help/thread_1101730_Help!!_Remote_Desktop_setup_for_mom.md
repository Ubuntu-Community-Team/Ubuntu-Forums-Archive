---
title: "Help!! Remote Desktop setup for mom"
date: 2009-03-20
forum: General Help
---

### Post by jamesmoo2090 on 2009-03-20
first of, please have patience with me, im a total n00b and totally new with linux. 

my mom is retiring and moving out of the country (thanks totally craptastic US economy!). to keep in touch im giving her my laptop, since i will not be able to do any fixing or anything (windows), i decided to put ubuntu 8.10 .

using the web, i got mediabuntu installed; got skype working, and DVD decoding, wireless, video drivers, etc.

but there is one las thing i need to get working before she leaves: remote desktop

what i need is to be able to control her computer over the internet, kind of like teamviewer for windows is; she can see me moving her mouse and opening windows and such

im really confussed and dont know what to do, i installed and got working nomachineNX, I could use her laptop, but she did not see me moving her mouse and stuff, she could only see the folders i created on the desktop, but that was it.

please help me. thanks.

---

### Post by crashsystems on 2009-03-21
Remote desktop really requires a very good network connection on both ends. Also, you will need to have access to her IP address. If she is going to have a connection good enough to allow remote desktop viewing, then it will likely have a static IP address. I would recommend using SSH to create an encrypted tunnel to her laptop (see link below). When using SSH, I highly recommend setting up public key authentication, and disabling password authentication. Use the the command line over SSH for anything that does not absolutely require a graphical interface (installing software, editing config files, etc).

For SSH to work, you'll need to configure port forwarding somehow. If she has a wireless router, then you can often tell the router to forward various ports (such as SSH's 22) to addresses on the private network. Also, while you are configuring this, you can set the router to give the same IP address to the laptop each time, by telling it the MAC address of the laptop. The configuration works differently for each router, so you'll have to do some googling for the instructions.

If you can get the SSH and port forwarding set up, then you can enable Ubuntu's built-in VNC software, Vinagre (see link below). You can enable it by going to System/Preferences/Remote_Desktop. Make sure to enable password authentication on it.

Once you have port forwarding, SSH and VNC set up, you'll need to create the tunnel. To do that, you'll run:
```
ssh -D 9090 username@remote-address
```The '-D' parameter sets up application level port forwarding. '9090' sets a local port to forward through, though you can use anything that is above 1000. Go to System/Administration/Network_Proxy, and set the option to manual proxy configuration. Under socks host type "localhost" and then type 9090 for the corrisponding port (or whatever you used). This will allow you to open up the Remote Desktop Viewer on your computer, and connect to her machine just like you could if it were on the same network as you.


All about SSH: [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
Vinagre: [https://help.ubuntu.com/community/Vinagre](https://help.ubuntu.com/community/Vinagre)

---

### Post by Excedio on 2009-03-23
> **jamesmoo2090 said:**
> im really confussed and dont know what to do, i installed and got working nomachineNX, I could use her laptop, but she did not see me moving her mouse and stuff, she could only see the folders i created on the desktop, but that was it.

No Machine is not a true VNC Viewer. It creates a virtual desktop that looks identical the the what you would see at the other end except that you will not see an currently opened windows and they will not see you opening windows.

---

### Post by mb_webguy on 2009-03-24
Vinagre, the Remote Desktop Viewer that comes with Ubuntu, will do the job, but it's not something that should be enabled all of the time.  For intermittent tech support, however, it's fine.  Even with a password and encryption, it's not quite as secure as ssh or some other means of connecting to another computer.

Setup System->Preferences->Remote Desktop so that it requires a password, uses an alternate port, and requires encryption, but do not enable it.  Show your mom how to enable it (which now involves checking one checkbox).  Then, when your mother needs you to do something to her computer, all she needs to do is let you know she needs help, enable Remote Desktop, and possibly tell you her current IP address if she doesn't have a static IP (which she would need to do no matter how you were trying to connect to her machine).  As the last thing you do when helping her, you can disable Remote Desktop for her so she doesn't have to worry about someone else hacking into her computer.

---

### Post by elbarto_87 on 2009-04-05
> **mb_webguy said:**
> Vinagre, the Remote Desktop Viewer that comes with Ubuntu, will do the job, but it's not something that should be enabled all of the time.  For intermittent tech support, however, it's fine.  Even with a password and encryption, it's not quite as secure as ssh or some other means of connecting to another computer.

Setup System->Preferences->Remote Desktop so that it requires a password, uses an alternate port, and requires encryption, but do not enable it.  Show your mom how to enable it (which now involves checking one checkbox).  Then, when your mother needs you to do something to her computer, all she needs to do is let you know she needs help, enable Remote Desktop, and possibly tell you her current IP address if she doesn't have a static IP (which she would need to do no matter how you were trying to connect to her machine).  As the last thing you do when helping her, you can disable Remote Desktop for her so she doesn't have to worry about someone else hacking into her computer.


I have been wondering how to do the same thing. I got remote desktop working over my local network, but how is it possible to do it over the internet? My IP address comes up as  10.1.1.2 or something like that so what else extra do you need to know in order to find a unique machine?

---

