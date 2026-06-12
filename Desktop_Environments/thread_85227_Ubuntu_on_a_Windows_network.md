---
title: "Ubuntu on a Windows network"
date: 2005-11-02
forum: Desktop Environments
---

### Post by ivains on 2005-11-02
Hello everyone. I know this might sound familiar but to no avail I have not found my answer after surfing the web for a couple of weeks now.

I have just install Ubuntu for the first time on a spare system - no problems. 

Currently I have my system (WinXP 192.168.0.1) which connects to the web via dialup modem. I have 2 other systems (WinXP Obtain IP automatically) which connect thru my system via a switch.

I connected the Ubuntu system to the switch, now how can I go by accessing the web from Ubuntu thru the WinXP box?

Any help or a link would be gratefully appreciated.

Just to let you know this is my first attempt with Ubuntu or Linux. I want to learn. Ubuntu looks very good and if I can figure this, plus other issues out I'm switching all the way.

Thanks
:) Ivan

---

### Post by suRoot on 2005-11-02
Well, if you're using internet connection sharing on the XP box, it should just be a matter of setting the XP box as the default gateway on the Ubuntu box.

Few questions.  How are you getting an IP on the ubuntu box?

What's the LAN IP on the XP box?

What does the output of 'sudo route' produce?

---

### Post by jatos on 2005-11-02
When your ubuntu base is connected to the switch, run dhclient in the console and put the results if you have any more problems, though you may find after running this program your computer suddenly works on the internet.

I might add I using a network with an XP Home machine sharing the internet, and all I have to do to get on the net is to make sure that Ubuntu has autoconfigured itself using DCHP.

---

### Post by ivains on 2005-11-02
I went thru System -> Administration -> Networking -> highlighted Ethernet connection and selected Properties.

- Enable this connection is Checked
- Configuration -> Static IP address
- IP address -> 192.168.0.16
- Subnet mask -> 255.255.255.0
- Gateway address -> 192.168.0.1

The WinXP box TCP/IP is set to:
- IP address -> 192.168.0.1
- Subnet mask -> 255.255.255.0

What does the output of 'sudo route' produce? I'm at a lost here. Is this the same as the PING? If so I went to Applications -> System Tools -> Network Tools -> Ping and type in 192.168.0.1 and Packets received was 0.

---

### Post by jatos on 2005-11-02
No that is showing your pc's IP config. Anway setup your system to configure the IP via DCHP, after that your internet should work on your machine.

---

### Post by ivains on 2005-11-02
ok i will give it try and let you know the results... 

thanks
:) Ivan

---

### Post by NewWithoutClue on 2005-11-02
'sudo route' is a console command. enter it in a terminal session to get output ( like a 'dos prompt' )

w00t
Paul.

---

### Post by ivains on 2005-11-02
Thanks Jato!

I didn't realize it was that simple. It took me a bit to figure out that the Terminal window is like the command prompt. I type in "sudo dhclient" and it went on with its config. I have Net now! Now its time to see what Ubuntu can do...

Thanks a bunch!!!

:) Ivan

---

