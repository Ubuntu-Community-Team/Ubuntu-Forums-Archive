---
title: "X11 Forwarding doesn't work!"
date: 2008-05-02
forum: Desktop Environments
---

### Post by btboudreaux on 2008-05-02
This worked perfectly in Gutsy for 6 months. I did a fresh install of Hardy and made the same config changes in my ssh config file and now I can't get X forwarding to work.

It says, "cannot open display:"

Anyone else having issues?

Has anyone else gotten X Forwarding to work?

---

### Post by btboudreaux on 2008-05-05
Has anyone with Hardy gotten it to work?

---

### Post by warp99 on 2008-05-05
> **btboudreaux said:**
> Has anyone with Hardy gotten it to work?
Works fine on both my desktop an media server machines. I would check your /etc/ssh/sshd_config to make sure that X11 forwarding is enabled. After you enable the settings restart the server:
```
sudo /etc/init.d/ssh restart
```

---

### Post by btboudreaux on 2008-05-06
I've got the same config that worked for me in Gutsy. Yes I have X11 Forwarding enabled.

Are there any changes I may have missed in the config, or somewhere else?

---

### Post by sdennie on 2008-05-06
Does it work if you run:

```

xhost +name_of_remote_machine

```

---

### Post by btboudreaux on 2008-05-06
More of the same: "xhost:  unable to open display "localhost:10.0""

Any other secret settings?

---

### Post by sdennie on 2008-05-06
For the local host I believe you will need:

```

xhost +local:

```

---

### Post by rickh57 on 2008-05-06
It's worked fine for me, with the use of xhost +. I've used this in both a vmware image of Ubuntu 8.04 and in a new clean install of it on a desktop last evening.

---

### Post by btboudreaux on 2008-05-06
> **vor said:**
> For the local host I believe you will need:

```

xhost +local:

```

Same output.

According to the man pages, xhost + should allow everything.

Not sure why I'm having so much trouble. Like I said, I had no problems with this in Gutsy.

Here's my config if anyone can find anything wrong with it.

-----------------

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes
PasswordAuthentication no
UsePAM no

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
#X11UseLocalhost yes
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

AllowUsers Username

Subsystem sftp /usr/lib/openssh/sftp-server

Ciphers aes256-cbc

#UsePAM yes

---

### Post by btboudreaux on 2008-05-07
So installed openssh-server on my laptop just to test, and everything worked great. So I reinstalled on my desktop leaving in the default config file and I STILL get the same error!!! I'm starting to think this is something else that is messing with SSH. 

Also when I open certain things from the command line I get this:
 sudo gedit /etc/ssh/sshd_config
Usage:program_name [address][:port]Usage:program_name [address][:port]Usage:program_name [address][:port]Usage:program_name [address][:port]

My laptop doesn't do that.

I'm about to go insane trying to figure this out. I'm really close to abandoning Ubuntu. This has to be one of the buggiest releases ever. I may just go pure Debian. I mean, when I first installed it I was setting up my network settings, and it changed my hosts file. Then every time I tried to do "sudo" it kept telling me it couldn't resolve my host name. I fixed that quickly but still, bugs like that shouldn't be in a LTS release. Ubuntu is supposed to lead the way on the desktop but they won't do it with releases like this...

sorry... rant off.

---

### Post by sdennie on 2008-05-07
Have you tried manually setting the DISPLAY variable?  So, from the machine you are sitting at:

```

xhost +name_of_server
ssh name_of_server
export DISPLAY=name_of_client:0.0

```

That assumes you are running a single monitor on the client.  You may have to replace the ":0.0" with the output of running "echo $DISPLAY" from the client machine.

---

### Post by btboudreaux on 2008-05-07
> **vor said:**
> Have you tried manually setting the DISPLAY variable?  So, from the machine you are sitting at:

```

xhost +name_of_server
ssh name_of_server
export DISPLAY=name_of_client:0.0

```

That assumes you are running a single monitor on the client.  You may have to replace the ":0.0" with the output of running "echo $DISPLAY" from the client machine.

Thanks but, still nothing. "Cannot open display"

I installed it on my laptop and it works. I've compared every single setting and still nothing. I've reinstalled the ssh server.

I've had so many issues getting simple things to work in Hardy that were never issues before, at this point I'm looking into other distros. I've used Ubuntu since Dapper. It had a good run, but the quality of this LTS release is really disheartening.

---

### Post by skydive814 on 2008-07-02
got it working.  I was having the same "Cannot open display" until I installed xauth.  (sudo apt-get install xauth)  Once installed, I  logged in my ubuntu box and ran "xauth list" to create my ~/.Xauthority file

My guess is because I don't run X on the box, sshd isn't creating it when I log in.  My install was just a "LAMP" server.

let me know if this works for you guys.

-sky

---

### Post by jaem on 2008-07-05
Works great for me - thanks.  I'm using Ubuntu Hardy Desktop x86.

---

### Post by cleam on 2008-08-16
Hello.

I have the exactly some problem.

export DISPLAY=name_of_client:0.0 after ssh login works well, but it's unusable when connecting outside the LAN. The 'name_of_client' host can be beyond the NAT and be unaccessible.

---

### Post by pumrum on 2008-09-30
::bump::

I'm having similar problems with Hardy (as the client). Here's the situation:

I've been using Gutsy for almost a year to connect to a Solaris 10 box running an X server. I type 'xhost +'  then 'ssh -X user@server'. When I type 'echo $DISPLAY' in the SSH session, it shows 192.168.1.1:0.0. I can then type 'firefox' and after a few seconds, a firefox X11 window will pop up. This is just one example, I use it for several X programs on the Solaris server.

I am now booting into a 8.04.1 Hardy Live CD (the latest available - I have also tried doing it on an install instead of the live CD, same results). I type 'xhost +' then 'ssh -X user@server'. I check my display variable in the SSH session and it's fine. However, when I go to run an X program, I get an X11 error. The actual error varies depending on the program I run, but they all boil down to the same root message:  "Gtk-WARNING **: cannot open display:"   or  "Exception in thread "main" java.lang.InternalError: Can't connect to X11 window server using '192.168.1.1:0.0' as the value of the DISPLAY variable."

Ive tried changing the display variable to:

--localhost:0.0
--localhost:10.0
--192.168.1.1:10.0

nothing seems to work. Any thoughts on how to fix this in Hardy? Any idea what broke going from Gutsy to Hardy? I'm going to try the same thing with the Intrepid Alpha 5 live CD (I'm not going NEAR alpha 6 because I used an Intel GigE card).

**EDIT**
I have tried the same procedure with Ubuntu 8.10 alpha5, and have gotten the same results. Any idea what's causing this? Is there a firewall built in that we need to disable now?

---

### Post by wingsrule on 2008-10-11
Hey everyone,

Related problem, I didn't want to start a new thread. Maybe someone can help me out.

Goal: I am on machine A. I need to open up a GUI program on machine C.

Now, machine C is behind a server B, so I cannot ssh -X to C directly. What I do instead is I ssh -X to B, get B's terminal, and then ssh -X to C. As far as console-only programs on A, this works. But X programs don't. I've echo'ed $DISPLAY on A and just get a blank line.

I also know that ssh -X from A to B works. I've tried that and successfully run SAS, Mathematica, etc.

I know that when C is inside the network (i.e. also behind B), I can ssh -X from A to C directly and X programs work. I've tried vlc.

X11 Forwarding is enabled on both B and C.

Any ideas? I know people have gotten this to work without manually messing around with $DISPLAY or doing something as dangerous as xhost, so if someone knows how to do this, I'd love the info.

Thanks in advance,
wingsrule

P.S. I can provide outputs of various conf files or commands if you really need them, but for security reasons, I'd rather not.

---

### Post by promodus on 2008-10-11
Whatever you're connecting to, make sure xauth is installed.

```
sudo apt-get install xauth
```

---

### Post by wingsrule on 2008-10-11
> **promodus said:**
> Whatever you're connecting to, make sure xauth is installed.

```
sudo apt-get install xauth
```

Good tip, but I checked and it's installed on all 3 computers. I also checked on B and it's using my ~/.Xauthority (I got the tip to check this from some other forum or thread).

Here's some additional info, if it helps.

A: Ubuntu Hardy with admin access, $DISPLAY returns ":0.0"
B: HP AIX with no admin access, $DISPLAY returns "serverb:10.0"
C: Fedora Core 9 with admin access, $DISPLAY returns ""

I also tried ssh-chaining it all in one line:

```
ssh -t -X userb@machineb 'ssh -X userc@machinec'
```

This still doesn't work i.e. $DISPLAY is still "" on machine C.

Thanks again for the efforts.

wingsrule

EDIT: fixed typo in $DISPLAY value for machine B.

---

### Post by Ocxic on 2008-10-11
"ssh -X [email]user@host.comp[/email]uter" That will enable X11 forwarding and you can just run the command.

---

### Post by wingsrule on 2008-10-11
Ok, I got it to work using a different machine for server B. It's on the same network, but it's an Ubuntu machine rather than an HP AIX.

More importantly, this new intermediary machine uses OpenSSH rather than the one made by SSH Communications Security (which was on the AIX machine). 

Incidentally, the X11 forwarding command on the proprietary SSH client is +X (TRUSTED) or +x (UNTRUSTED) rather than the -x or -X which disables forwarding. I didn't know that at first, so I thought using +X would fix it but it didn't. Also, private/public key passwordless login doesn't work for the proprietary SSH server either. Bastards...

Anyway, my access to this Ubuntu intermediary is only until the end of December, so I'd like to figure out how to do this using the AIX machine too, but at least temporarily, I got it working.

Does anyone have any experience with the proprietary SSH client? This is what 'ssh -h' outputs, for your reference:

```

ssh: SSH Secure Shell 3.2.9.1 (non-commercial version) on rs6000-ibm-aix
Copyright (c) 1995-2002 SSH Communications Security Corp
SSH is a registered trademark and Secure Shell is a trademark of
SSH Communications Security Corp (www.ssh.com).
All rights reserved.  See LICENSE file for usage and distribution terms.

Usage: ssh [options] [user@]host[#port] [command]

Options:
  -l login_name  Log in using this user name.
  -n             Redirect input from /dev/null.
  +a             Enable authentication agent forwarding.
  -a             Disable authentication agent forwarding.
  +x             Enable X11 connection forwarding (treat X11 clients as
                 UNTRUSTED).
  +X             Enable X11 connection forwarding (treat X11 clients as
                 TRUSTED).
  -x             Disable X11 connection forwarding.
  -i file        Identity file for public key authentication
  -F file        Read an alternative configuration file.
  -t             Tty; allocate a tty even if command is given.
  -v             Verbose; display verbose debugging messages. Equal to '-d 2'
  -d level       Set debug level.
  -V             Display version string.
  -q             Quiet; don't display any warning messages.
  -f[o]          Fork into background after authentication.
                 With optional 'o' argument, goes to "one-shot" mode.
  -e char        Set escape character; 'none' = disable (default: ~).
  -c cipher      Select encryption algorithm. Multiple -c options are 
                 allowed and a single -c flag can have only one cipher.
  -m MAC         Select MAC algorithm. Multiple -m options are 
                 allowed and a single -m flag can have only one MAC.
  -p port        Connect to this port.  Server must be on the same port.
  -S             Don't request a session channel. 
  -L listen-port:host:port   Forward local port to remote address
  -R listen-port:host:port   Forward remote port to local address
                 These cause ssh to listen for connections on a port, and
                 forward them to the other side by connecting to host:port.
  -g             Gateway ports, i.e. remote hosts may connect to locally
                 forwarded ports.
  +g             Don't gateway ports.
  +C             Enable compression.
  -C             Disable compression.
  -4             Use IPv4 to connect.
  -6             Use IPv6 to connect.
  -o 'option'    Process the option as if it was read from a configuration
                 file.
  -1[ti]         Choose ssh1-protocol fallback type. Mandatory argument. 'i'
                 means internal emulation, 't' means traditional (call ssh1
                 executable).
  -h             Display this help.

Command can be either:
  remote_command [arguments] ...    Run command in remote host.
  -s service                        Enable a service in remote server.

Supported ciphers:
  3des-cbc,aes256-cbc,aes192-cbc,aes128-cbc,blowfish-cbc,twofish-cbc,twofish256-cbc,twofish192-cbc,twofish128-cbc,des-cbc@ssh.com,cast128-cbc,arcfour,none
Supported MAC algorithms:
  hmac-md5,hmac-md5-96,hmac-sha1,hmac-sha1-96,hmac-sha256@ssh.com,hmac-sha256-96@ssh.com,hmac-ripemd160@ssh.com,hmac-ripemd160-96@ssh.com,none

```

---

### Post by pumrum on 2008-10-29
For those of you struggling with this in Hardy or Intrepid (I'm pretty sure this isn't necessary in Gutsy):

The default install of both Hardy and Gutsy are almost completely ready to act as X11 guests (that is, you log into a *nix server from your Ubuntu desktop, run a command, and a GUI program appears on your Ubuntu machine).

The only steps needed are:

[B]Enable TCP connections to Xserver (only need to do this once)
-System > Administration > Login Window
-Click the Security tab
-Uncheck 'Deny TCP connections to Xserver'
-Restart the Ubuntu computer[/B]


Enable xauth forwarding (do this only once per Ubuntu session)
-Open a terminal
-Type 'xhost +' and press Enter


Connect to the server (do this for every SSH session, obviously)
-Open a terminal
-Type 'ssh -X [email]user@server.domain.com[/email]' and press Enter


Hope this saves some frustration!

---

### Post by franco-2008 on 2008-10-31
Hi,
I had a similar problem and it was linked to /etc/hosts configurations file on the remote host, the row "127.0.0.1 localhost" was missing.
Look with `less /etc/hosts` and correct it if it is necessary.

Hi

---

### Post by fofftorrent on 2008-11-11
i have 3 machines. X11 forwarding works from Hardy->Hardy

but does not work from Intrepid->hardy

---

