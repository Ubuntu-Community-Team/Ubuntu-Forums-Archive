---
title: "Connect to home computer"
date: 2010-11-29
forum: Desktop Environments
---

### Post by WeyOh on 2010-11-29
Hi,

I would like to connect to a computer (running 10.04) via the internet in order to perform different tasks, such as to provide assistance to the user. This would be something on a small scale. I had initially thought of achieving this strictly through VNC, but the Ubuntu help guide states that:

> Although VNC has some optional security features, you should not run VNC directly over an untrusted network like the Internet. Instead, you should set an SSH server up as discussed in the SSH guide and configure a VNC server that you can start in so-called once mode.

I then went on to read the guide on how to set up an SSH server, but it does sound like this method has various vulnerabilities.

An alternative way would be to do this through VPN, and then run the VNC as a local connection.

I was wondering if there is any other way (particularly a better way), or which of the two above I should choose. Finally, to top it all, does someone know of a good guide (apart from the ones on help.ubuntu.com) in order to set such solution up?

Thanks!

---

### Post by lombaardcj on 2010-12-06
Hi,

I would give OpenSSH a go combined with eBox.

Just follow the Ubuntu Server Guide and you will be doing well.

Any additional concerns you might have can be addressed by looking at the OpenSSH resources available at [http://www.openssh.org/](http://www.openssh.org/)

There is other alternative available, but I stick to what I know works.

Another thread explaining the use of SSH: [http://ww.ubuntuforums.org/showthread.php?t=1547967](http://ww.ubuntuforums.org/showthread.php?t=1547967)

---

### Post by 3Miro on 2010-12-06
Anything that allows remote access to a computer has vulnerabilities. SSH is the preferred method for remote administration under Linux, just read carefully on how to set it up correctly, it can be a potential risk.

---

### Post by pricetech on 2010-12-06
SSH is definitely the way to go.  If you need a GUI, use NX from nomachine dot com.

---

### Post by karthick87 on 2010-12-06
I personally prefer Team  viewer,it's a computer software package for  remote control, desktop  sharing, and file transfer between computers.  The software operates with   Microsoft Windows,Linux based OS & Mac  OS X, and is able to  function while the computers are protected by  firewalls and NAT  proxy....
  **Installing Team viewer:**
  For Ubuntu,you can download teamviewer [here]("http://www.teamviewer.com/download/teamviewer_linux.deb").  Once downloading is completed, you can install it easily by double   clicking the file.After installation you can find team viwer under the   Internet Menu.
  **Open the Team Viwer:**
  Applications -- >>Internet -->> Team Viwer
  [IMG]http://i.imgur.com/eWwZs.png[/IMG]
  Before establishing the remote desktop connection,you must know the   ID and Password of the remote system which is running Team Viwer.After   getting the ID and Password from your partner.Enter the ID and click   connect to partner, with in few seconds it will show a window prompting    for a password.Enter the password which you got from your partner and   click ok.
  Now you are connected to remote sytem.

---

