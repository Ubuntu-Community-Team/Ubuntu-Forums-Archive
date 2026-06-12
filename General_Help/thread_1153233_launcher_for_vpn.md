---
title: "launcher for vpn"
date: 2009-05-08
forum: General Help
---

### Post by Karychy on 2009-05-08
Hello,

I am trying to create a desktop launcher for my vpn client.
To connect to the network, I have to type '(sudo) vpnclient_init start', and then 'vpnclient start (profile)'. The first thing is necessary only after rebooting the system, and although during the installation of the client I did choose to do this automatically at reboot, it doesn't seem to be happening.
So my current launcher calls the second command that connects to the network. Is there a way to make it call the first one too? Or its only one command per launcher, without pipes or any other ways to make it execute both commands?

~K.

---

### Post by spiderbatdad on 2009-05-08
I think you can do this by entering the launcher command as ```
bash -c <command> && <command>
```The problem with the use of sudo though is, your command will silently die. You can get around this by making a rule in /etc/sudoers to run that file w/out a password.
Not sure about the security issues involved with running your vpn as root.
Why are you not using the nm-applet to connect to your vpn?

---

### Post by jawana on 2009-05-08
hi 
if you are using 8.04 ,8.10 or 9.04 , you can do a left click on the your wireless or ethernet connection, you will get a drop down list choose vpn connection and set it up. once done left click choose vpn and then the actual connection.

that is it , your connection icon will change once vpn is established.

regards

kash

---

### Post by Karychy on 2009-05-08
Well, when I go to the VPN tab of Network Connections it's empty...
I do automatically connect to the network when in range, but the vpn client needs this vpnclient_init start each time...

What does the bash c thing mean? And what is this nm-applet and how can it help me get around typing those two commands each time I restart the computer?

---

### Post by spiderbatdad on 2009-05-08
the -c option tells the launcher to accept commands. Normally a path to an executable file is sufficient, but in the case of multiple commands, I believe you will need bash  -c. nm-applet is the internet connection icon you are familiar with.

So your launcher command would be something like:
```
bash -c 'sudo vpnclient_init start && vpnclient start profile'
```

To edit sudoers you should run ```
sudo select-editor
```and choose #3.
Then run command to edit file: ```
sudo nano /etc/sudoers
```
At the end of the file add:
```
Cmnd_Alias launcherCMD = <path to your sudo script>
ALL ALL=(ALL) NOPASSWD: launcherCMD
```

See here for more on sudoers:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

