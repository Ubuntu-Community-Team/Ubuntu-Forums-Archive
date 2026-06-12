---
title: "A server just for web browsing."
date: 2013-10-31
forum: Desktop Environments
---

### Post by MrWestwood on 2013-10-31
Hello. I'm wanting to build a server that people can log onto via RDP, VNC or any other protocol I'm not aware of and use Firefox. I have lots of thin clients and would like to create a sort of Windows Terminal Ser=ver system but with Linux, Firefox and Thunderbird. Any starters would be a great help. 

Thanks

---

### Post by Lars Noodén on 2013-10-31
That wouldn't really be a server as much as a regular desktop with the package OpenSSH-server added, plus maybe a package for VNC or RDP.  You'll want to tunnel VNC or RDP over SSH so your machine stays safe.  Those protocols are not so secure and tunneling is a work-around to address that.  

Another option is just to forward X11 from your remote machine to your local one.

```

ssh -X -i /home/mrwestwood/.ssh/some_key_rsa mrwestwood@server.example.org firefox

```

That is the simplest to set up but can be annoying if there is a lot of latency in the connection.  Whether you tunnel VNC, RDP or just X11 be sure to use keys for authentication.

---

### Post by merlyn2748 on 2013-10-31
If you are looking for a Terminal Server solution you should check out LTSP.  It is installable from the 12.04 alternative install disk (change the mode with F4 on initial install) and it will provide a netbooting thin client environment.  LTSP has their own support forums and plenty of people who can help you.

---

### Post by dozynsleepy on 2013-10-31
That sounds like something  you could use freenx for.
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

What are your "thin clients" ?

---

### Post by Lars Noodén on 2013-10-31
Disregard my above comment about tunnelling.  I missed that you wanted to set up thin cients.  

To do thin clients, you should read up on Edubuntu, LTSP, Skolelinux, or K12LTSP.  Any of those will set up servers where applications are run, but the display occurs on the thin client.  However, usually you have two servers per location just in case one goes down.  Also, these days, gigabit ethernet is recommended.  You can do it with less though.  If you have only one server, then that's how it is.

---

### Post by MrWestwood on 2013-10-31
Thanks guys. So far we have a live disc that we have stripped down to just run Firefox and Thunderbird. I want to ideally allow as many users as possible at the same time as to log on via either RDP or VNC primarily. THe sticking thing is we have some thin clients that run rdp so we could change where they remote to. That's why I was wondering if it's possible to do it with VNC or rdp. LTSP is great but lately the IT department seem to just use those AXEL rpd/vnc machines as they're cheap and really all they need as users just RDP on to Windows server. I sort of want to replicate a windows server machine I guess. And have my clients log in to that via rdp or vnc.

Sorry for repeating myself.

---

### Post by MrWestwood on 2013-10-31
.> **Lars Noodén said:**
> That wouldn't really be a server as much as a  regular desktop with the package OpenSSH-server added, plus maybe a  package for VNC or RDP.  You'll want to tunnel VNC or RDP over SSH so  your machine stays safe.  Those protocols are not so secure and  tunneling is a work-around to address that.  

Another option is just to forward X11 from your remote machine to your local one.

```

ssh -X -i /home/mrwestwood/.ssh/some_key_rsa mrwestwood@server.example.org firefox

```

That is the simplest to set up but can be annoying if there is a lot of  latency in the connection.  Whether you tunnel VNC, RDP or just X11 be  sure to use keys for authentication.

Though this wouldn't help in my case. I do use tunneling from home to work. It's great what you can do with ssh -X

---

### Post by MrWestwood on 2013-10-31
> **merlyn2748 said:**
> If you are looking for a Terminal Server  solution you should check out LTSP.  It is installable from the 12.04  alternative install disk (change the mode with F4 on initial install)  and it will provide a netbooting thin client environment.  LTSP has  their own support forums and plenty of people who can help you.


Will this act as the "Windows server" side. I apologise for the simple terminology but's that all I have to compare it to. Or will it just do as ltsp does and require pxe boot?

---

### Post by MrWestwood on 2013-10-31
> **dozynsleepy said:**
> That sounds like something  you could use freenx for.
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

What are your "thin clients" ?

For this we will be using those AXEL rdp/vnc boxes.

---

### Post by MrWestwood on 2013-10-31
I believe it's xrdp I need. 

Many thanks foryour help.

---

