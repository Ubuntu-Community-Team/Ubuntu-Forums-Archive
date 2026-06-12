---
title: "Resurrection of mono 1.1.12 question"
date: 2021-12-29
forum: Gaming &amp; Leisure
---

### Post by brewcrew on 2021-12-29
This question was asked some time ago but with no successful solution it seems.
I have downloaded mono-1.1.12.1_0-installer.bin.zip and unzipped OK.

I cannot install mono 1.1.12 using 
 
chmod +x  mono-1.1.12.1_0-installer.bin
then
./mono-1.1.12.1_0-installer.bin - nothing happens and 'mono -V' results in 'mono not found'

There is a very good reason for needing to install such an old mono, an essential program will not run under a higher version. It ran quite happily for several years, but a server rebuild necessitates reinstalling everything. 

Wine  5.1 has installed fine and has configured OK but needs mono to run a .exe daemon.

Assume I'm a total know nothing, because I am, but I have read and read until my eyes have crossed

Regds

---

### Post by spjackson on 2021-12-29
> **brewcrew said:**
> ./mono-1.1.12.1_0-installer.bin - nothing happens

Do you not get a setup window as attached?[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289711&stc=1[/IMG]

If not, check the MD5sum against what it should be [https://download.mono-project.com/archive/1.1.12.1/download/](https://download.mono-project.com/archive/1.1.12.1/download/)

What does 'file' say? It should be
```

$ file ./mono-1.1.12.1_0-installer.bin
./mono-1.1.12.1_0-installer.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, no section header

```

What platform are you trying to install it on?

---

### Post by brewcrew on 2021-12-29
Thanks for the response. I lease a bare bones server from a company in  Starsbourg so I have no GUI and I'm installing through STFP.  I have a  choice of two platforms either Centos or Ubuntu.

---

### Post by spjackson on 2021-12-30
```

./mono-1.1.12.1_0-installer.bin --help

```
lists some options. It looks like
```

./mono-1.1.12.1_0-installer.bin --mode text

```
should work for you if you have no gui. You might want to consider other options too.

---

### Post by TheFu on 2021-12-30
> **brewcrew said:**
> Thanks for the response. I lease a bare bones server from a company in  Starsbourg so I have no GUI and I'm installing through STFP.  I have a  choice of two platforms either Centos or Ubuntu.

You cannot install anything through sftp.  That is only a file transfer protocol.  

However, if you have ssh, you can run programs. It is possible to setup a GUI capability - to get it, just run 
```
sudo apt install xterm
```
That will install X/Client libraries.
Next, on your local Ubuntu system, use 
```
ssh -X remote-userid@remote-server-IP command
```
```
ssh -X  brewcrew@1.2.3.4  path-to-mono-install/mono-1.1.12.1_0-installer.bin
```
This will make an X11 client/server connection through an ssh tunnel from the remote system back to your local X/Server.
Because I'm not on the remote machine, I don't know the IP address nor the correct path to where you placed the mono-installer.

If it were me, I'd use the --mode text options for the installer over ssh.  That is easier and faster.

If you are stuck with a local Windows machine, I don't have a good answer. Perhaps check out x2go?  I use that over the internet and have from 5 continents when I needed to access my normal desktop back home. It also works over ssh, but that is built into the NX protocol on which it is based.  Having a working ssh BEFORE using x2go is required. Actually, I haven't used it without ssh-keys in about a decade, so I don't know if it works without that setup pre-configured. Setting up ssh-keys is easy. Just 2, short, commands.

---

### Post by brewcrew on 2021-12-30
Many thanks, there's a lot there and it may take me a little time to work through it. The idea of a GUI certainly appeals, I didn't know it was possible. I'm accessing the Linux server through a Windows 10 desktop (perhaps I should have said that earlier) so no local Ubuntu.

I've installed BitVise SSH (first tried WinSCP but it's really slow), and puTTy so we shall see how far I get.  Again 
thanks to all for the suggestions.

---

### Post by TheFu on 2021-12-31
> **brewcrew said:**
> Many thanks, there's a lot there and it may take me a little time to work through it. The idea of a GUI certainly appeals, I didn't know it was possible. I'm accessing the Linux server through a Windows 10 desktop (perhaps I should have said that earlier) so no local Ubuntu.

I've installed BitVise SSH (first tried WinSCP but it's really slow), and puTTy so we shall see how far I get.  Again 
thanks to all for the suggestions.

Win10 is a huge liability to working well with Linux.  Things just aren't as easy.  It is sorta like how using all Apple stuff "just works" and trying to mix different vendors creates complexity and hassles.

PuTTY is only for ssh. No GUI.  Win10 has a built-in ssh these days, but I much prefer using a real Unix terminal for a number of reasons - mainly how select/paste "just works" which is partially replicated with PuTTY, but not in Windows10.

WinSCP is for transfers using sftp or scp.  These are great over the internet. On the same LAN, perhaps there are better methods, but from time to time, I'll use WinSCP from Windows where their isn't much other choice.  On Linux desktops, the file manager supports sftp://, so it is integrated that way - no extra tools needed.  Or just setup NFS, which makes remote storages work like local storage. NFS has been around and available ~ 40+ yrs?  It is very mature. CIFS/Samba is a poor substitute and doesn't provide native access. NFS is system-to-system, not user-to-system.  Normal, expected, Unix file permissions and ACLs are supported by NFS, unlike CIFS.

So, if you don't have an X/Server running on Windows (which most people wouldn't), then that leaves x2go for the best F/LOSS remote GUI access.  I ran x2go for a few years from a Windows7 desktop to connect into my daily use Linux desktop. It was fast and stable and secure, unlike the other options (cough ... RDP/VNC).  In the end, I simply missed the full integration that is provided by even the smallest, lightest, Linux desktops with real terminals and real X/Servers.  Windows just cannot compare. It just doesn't.  In 1990, MSFT made some smart business choices for lower-cost hardware. NeXT had gone a different way with hardware that was $10K+. Apple tried to make capable hardware that was a mix, but until they bought NeXT, it really wasn't a Unix workstation.  Without X (aka X11, X/Windows), the interface just doesn't behave correctly.  
X does have overhead. No denying that.  X is a client/server protocol and network agnostic. It doesn't care if the client  (X/client) is running on the same physical system as the server (X/Server) or on the other side of the planet. This is a sort point for many people, since they never considered that having the system running the program and the system displaying the program could be different. X has been doing that longer than I've been using Unix.  What's really funny is that Microsoft was part of the X/Consortium in the early years. Microsoft actually had a Unix-like OS before Windows or OS/2 existed. Hard to believe.  Their genius was in recognizing the business realities and acceptable price points for systems over the years.  I think MSFT is 20 yrs too late to the Unix-like OS world.  Win2000 really should have been when they started the Unix change. Too much NIH syndrome.

Have you run a Linux desktop in a virtual machine on your system?  Something light - say Xubuntu or Pop!OS or Mint?  Any of those will really open your eyes for how things integrate, I think, while removing all the oddness that is MS-Windows.

---

### Post by brewcrew on 2022-01-02
Many thanks for the information, I know it takes time and is much appreciated.
I'm astonished how fast Ubuntu installs on the remote server after changing from Centos, and the terminal in BitVise seems to work fine. X-Term is an eye opener and certainly makes life simpler but mono still blows me a raspberry. I thought maybe installing a dual boot on the PC would make life easier-it didn't! and still left me with the problem making a .exe file work on the server side. 

it demands Wine-Mono but that means the Mono is the latest version and won't work. Basically Mono 1.1.1... is .Netframework 1.1, quite why the latest version is incompatible I don't know.

I really thank you guys for all the advice but the reality is that I've bitten off far more than I can chew and I'm starting too far back as a Ubuntu user to take on this project. The annoying thing is that it is probably an easy solution but a I lack the depth of knowledge to see it.

Again thank for your time.

Brew

---

### Post by TheFu on 2022-01-02
I've had good and bad luck with mono.  I consider it like Java - both are to be avoided whenever possible for many reasons.

---

