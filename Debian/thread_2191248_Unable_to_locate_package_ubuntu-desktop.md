---
title: "Unable to locate package ubuntu-desktop"
date: 2013-12-01
forum: Debian
---

### Post by ellissteve1313 on 2013-12-01
I have ran: 

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop

but still get that "Unable to locate package ubuntu-desktop"

how can i fix this?

---

### Post by Bashing-om on 2013-12-01
ellissteve1313; H1 Welcome to the forum .

Yeah, that situation is pretty senseless right now. Let's see if we can determine what is not going on.

1. Is your sources list file in a consistent state - for a current ubuntu repository ?
Post back the out put - between code tags - of terminal command:
```

cat -n /etc/apt/sources.list

```
//
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

2. And you do have a working internet connection - do you see ubuntu.com ?
```

ping -c3 ubuntu.com

```

3. and what returns from terminal code:
```

apt-cache policy ubuntu-desktop

```

That will get us started in the process of fault isolation for restoration.

[INDENT][INDENT]cause and effect
[/INDENT][/INDENT]

---

### Post by ellissteve1313 on 2013-12-01
1. Return: 

1 deb [http://ftp.debian.org/debian](http://ftp.debian.org/debian) squeeze main contrib non-free
2 deb [http://security.debian.org](http://security.debian.org) squeeze/updates main contrib non-free
3

2. PING ubuntu.com (91.189.94.156) 56(84) bytes of data.
64 bytes from vostok.canonical.com (91.189.94.156): icmp_req=1 ttl=50 time=44.1 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_req=2 ttl=50 time=44.0 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_req=3 ttl=50 time=43.8 ms

--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2011ms
rtt min/avg/max/mdev = 43.826/44.013/44.159/0.279 ms

3. Unable to locate package ubuntu-desktop

Thanks for the help

---

### Post by deadflowr on 2013-12-01
You're running debian?

i don't think the ubuntu-desktop metapackage was ever moved up to debian.

At least not through the regular repos.

---

### Post by ellissteve1313 on 2013-12-01
hmm

how would one get a GUI there?

---

### Post by overdrank on 2013-12-01
> **ellissteve1313 said:**
> hmm

how would one get a GUI there?

Maybe here 
[http://www.debian.org/doc/](http://www.debian.org/doc/)

---

### Post by deadflowr on 2013-12-01
Wasn't there an option to install a gui, like the gnome or xfce or something other desktops when you installed the system?

---

### Post by Iowan on 2013-12-01
Are you sure there isn't one there? My Raspbian PI boots to command line - needs (sudo) **startx** to launch the desktop.

---

### Post by ellissteve1313 on 2013-12-01
I did not install the system myself it was bought.

I am trying to download KDE and use startX but have had no success.

---

### Post by Bashing-om on 2013-12-01
ellissteve1313; Well,

Let's look and see what desktop you might have installed.
Terminal command:
```

echo $DESKTOP_SESSION

``` then we can advise better.

[INDENT]look first
[INDENT][INDENT][INDENT]before jumping
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ellissteve1313 on 2013-12-01
> **Bashing-om said:**
> ellissteve1313; Well,

Let's look and see what desktop you might have installed.
Terminal command:
```

echo $DESKTOP_SESSION

``` then we can advise better.
[INDENT]look first[INDENT][INDENT][INDENT]before jumping
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

I uninstalled debian and installed unbuntu 10.04-x86_64.

I then updated and downloaded - "sudo apt-get install ubuntu-desktop"

After half and hour it downloaded.

I then tried "startx", I get a long result that at then end says:

xinit: no such file or directory (errno 2): unable to connect to x server
xinit: no such process (errno 3): server error.

I tried installing "sudo apt-get install ubuntu-desktop" again.
and the outcome is "ubuntu-desktop is already the newest version"

What could be going on now?

---

### Post by Bashing-om on 2013-12-01
ellissteve1313; Well ...
Version 10.04 has reached End Of Life for the desk top.
Did you download the server edition ? .. In the server edition in order to have a desk top - not generally recommended - one must first install the xorg package.

Let's all quit chasing our tails -> what is it that you want to accomplish ??
What hardware are you attempting to install on .. the high end editions of ubuntu require high end hardware to run decently.
Otherwise, we are looking at other options to install.

[INDENT][INDENT]I am I am trying to help
[/INDENT][/INDENT]

---

### Post by deadflowr on 2013-12-01
Try restart/reboot.

10.04?
The desktop version went end of life a while ago.
Was this a server install?

Edit: Seems me and bashing-om are of the same mind again in a different thread, lol.

---

### Post by ellissteve1313 on 2013-12-01
Thanks for the replies and the help, they are appreciated.

I can upgrade to 13.04-x86 or 13.04-x86_64.

I was looking to browse the web and store a few downloaded files. I need the isolation of the VPS and the change of IP, this was my best way to do it as simpler options like VPN would not get it done.

---

### Post by ellissteve1313 on 2013-12-01
I upgraded to 13.04-x86 --- same problem when trying "startx"

---

### Post by Bashing-om on 2013-12-01
ellissteve1313; Oh me Oh my !

Ok .. the command "startx" is only applicable in some desktops and as well, in order to start any desktop; one must have a means to not only start that graphical layer, one must also have a means to access that layer.
So once more .. what desk top are we talking about ?? there are literally hundreds of desk tops out there !

Do you have xserver available in that install ? .. do you have the xorg package installed ??? .. and by the way .. what distribution and version are we now in reference to ?

@deadflowr - great minds think alike , but me --I am a goat head !


[INDENT][INDENT]if we do not know we can not help
[/INDENT][/INDENT]

---

### Post by deadflowr on 2013-12-01
> **ellissteve1313 said:**
> I upgraded to 13.04-x86 --- same problem when trying "startx"
Are you running the server edition or the desktop edition?

Also try running

sudo lightdm restart

or

sudo service lightdm restart

---

### Post by steeldriver on 2013-12-01
If you are trying to run a desktop on a VPS then the procedure will be somewhat different - you will still need 'desktop' packages on the VPS, but you will also need a VNC server to relay the X session and a VNC client on your local computer to display the session (unless you want to display individual applications via SSH using X forwarding) - something like this for example --> [https://panel.cinfu.com/knowledgebase/20/Grpahical-Desktop-LXDE-installation-in-VPS-with-Ubuntu-OS-for-a-low-RAM-VPS-plans.html](https://panel.cinfu.com/knowledgebase/20/Grpahical-Desktop-LXDE-installation-in-VPS-with-Ubuntu-OS-for-a-low-RAM-VPS-plans.html)

> **ellissteve1313 said:**
> Thanks for the replies and the help, they are appreciated.

I can upgrade to 13.04-x86 or 13.04-x86_64.

I was looking to browse the web and store a few downloaded files. [COLOR=#ff0000]**I need the isolation of the VPS and the change of IP**[/COLOR], this was my best way to do it as simpler options like VPN would not get it done.

---

### Post by ellissteve1313 on 2013-12-01
> **steeldriver said:**
> If you are trying to run a desktop on a VPS then the procedure will be somewhat different - you will still need 'desktop' packages on the VPS, but you will also need a VNC server to relay the X session and a VNC client on your local computer to display the session (unless you want to display individual applications via SSH using X forwarding) - something like this for example --> [https://panel.cinfu.com/knowledgebase/20/Grpahical-Desktop-LXDE-installation-in-VPS-with-Ubuntu-OS-for-a-low-RAM-VPS-plans.html](https://panel.cinfu.com/knowledgebase/20/Grpahical-Desktop-LXDE-installation-in-VPS-with-Ubuntu-OS-for-a-low-RAM-VPS-plans.html)

Thank you.

It looks like I got this working succesfully on the VPS

But I have not been able to download their TightVNC software to my linux based computer? Very frustrating...

I am now running ubuntu-13.04-x86_64 through a VPS.

How can I get this desktop?

---

### Post by steeldriver on 2013-12-01
If the local computer you want to display the desktop on is Linux based then there are plenty of native Linux VNC clients - the default one for Ubuntu is called Remmina. I'd only suggest using TightVNC as the viewer (client) if you're on Windows.

---

### Post by steeldriver on 2013-12-01
If the local computer you want to display the desktop on is Linux based then there are plenty of native Linux VNC clients - the default one for Ubuntu is called Remmina. I'd only suggest using TightVNC as the viewer (client) if you're on Windows.

BTW you REALLY should tunnel the connection over SSH - raw VNC is *not*secure and your VPS will likely be flooded with connection attempts if you leave the default VNC port open

---

### Post by ellissteve1313 on 2013-12-01
If I could get this to work on remmina that would be fantastic.

So I ran a"pt-get install xorg lxde-core remmina" - That looked to be succesful.

When I try to set a password though I get:

** (remmina:4017): WARNING **: Could not open X display

(remmina:4017): Gtk-WARNING **: cannot open display:

---

### Post by steeldriver on 2013-12-01
Huh? 

You **run **Remmina on your local machine, and use it to **connect to** the VNC server + lxde running on your VPS

There is no need to install Remmina on the VPS (in fact it's pointless, since there's no local display)

---

### Post by ellissteve1313 on 2013-12-01
> **steeldriver said:**
> Huh? 

You **run **Remmina on your local machine, and use it to **connect to** the VNC server + lxde running on your VPS

There is no need to install Remmina on the VPS (in fact it's pointless, since there's no local display)

I have tried numerous times to connect through remmina. Using the IP - username (root) and password.
Everytime get: "Unable to connect to RDP server ..."

How would I be able to connect through remmina?

---

### Post by ellissteve1313 on 2013-12-01
Mean VNC server, not RDM

---

### Post by steeldriver on 2013-12-01
If you are running tightvncserver on the VPS, then you should be connecting via the VNC protocol not the RDP protocol. Make sure you specify whatever display number you started the tightvncserver on in either :display or :port notation e.g. if you did

```
vncserver :1
```

on the VPS then enter the remote host into Remmina as either your.ser.ver.ip:1 or your.ser.ver.ip:5901

I strongly advise against running a VNC server as root - especially an open (untunnelled) one

---

### Post by ellissteve1313 on 2013-12-01
> **steeldriver said:**
> If you are running tightvncserver on the VPS, then you should be connecting via the VNC protocol not the RDP protocol. Make sure you specify whatever display number you started the tightvncserver on in either :display or :port notation e.g. if you did

```
vncserver :1
```

on the VPS then enter the remote host into Remmina as either your.ser.ver.ip:1 or your.ser.ver.ip:5901

I strongly advise against running a VNC server as root - especially an open (untunnelled) one

Oh great thankyou. I was missing the :1

I get a completley red screen. When I right click I am able to get into the 'computer'
I installed firefox in the terminal, how can I move it into a CD that I can access? 
Once I get this down, I will move on to securing it.

Thank you very much!

---

