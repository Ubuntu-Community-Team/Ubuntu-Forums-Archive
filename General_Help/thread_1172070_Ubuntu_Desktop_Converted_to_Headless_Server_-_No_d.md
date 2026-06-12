---
title: "Ubuntu Desktop Converted to Headless Server - No display via SSH VNC"
date: 2009-05-28
forum: General Help
---

### Post by Loan_Refi on 2009-05-28
I have been using Ubuntu 8.04 Hardy installed with;
Print Server
Drupal
VMWare - hosting 4 virtual OS such as Win03K, FreePBX, Vista,
File Sharing

I was using vncserver X11vnc for remote desktop to Ubuntu 8.04 thru SSH and worked great.  

I desided to make the machine headless so I removed the Monitor, Keyboard & Mouse but as soon as ran my usual command to login remotely I got the screen I normally get but its blank.

This is probably because I removed the monitor right?

So my question is how can I continue to use vncviewer to remote into Hardy 8.04 headless?

This is my command I run;

Step1
ssh -t -L 5900:localhost:5900 [www.example.com](www.example.com) -p 3022 'x11vnc -localhost -display :1'

Step2
vncviewer -x11cursor -geometry 900x700 -encodings "copyrect tight zrle hextile" localhost:0

---

### Post by dmizer on 2009-05-28
How about:

1) ssh -XC [www.example.com](www.example.com) -p 3022
2) vncviewer -x11cursor -geometry 900x700 -encodings "copyrect tight zrle hextile" localhost:0

The X switch forwards the remote X server and C gives you compression. That way you'll be using the vncviewer from the server rather than the local machine, but same results.

---

### Post by cybergalvez on 2009-05-28
I would use nx its easier and should work fine headless

---

### Post by dmizer on 2009-05-28
Actually, if it's only a print/www/vmware server, there are web tools to take care of all that stuff without the overhead of piping a complete desktop over ssh.

---

### Post by Loan_Refi on 2009-05-28
Thanks for the fast replies!

dmizer - 

I used your command "1) ssh -XC [www.example.com](www.example.com) -p 3022" but it doesn't work. That's okay I don't have a problem connecting with my command even in slow remote connections so I'll continue to use mine (ssh -t -L 5900:localhost:5900 [www.example.com](www.example.com) -p 3022 'x11vnc -localhost -display :1')

I read your links for suggestions 1,2,3,4,5 & 6 very nice!!  I have those things working well samba, vfstpd, etc.

Honestly the only reason why I need to get this Display to show up properly is because I'm not 100% confident using terminal yet.

I agree that a server should have no Desktop for performance reasons.  

Example - I have another server Setup to use Sendmail with Nail for Fax to email.  This is what I did; I plugged in a Serial Modem to my server, installed gtk-efax, and added a script to email received faxes received via analog phone line. For this I wouldn't know how to put the gtk-efax on standby to receive faxes. I need to start gtk-efax and click on standby cause if I don't it doesn't automatically go into standby when started.

I would love to just do all this in terminal but my experience is not there yet.

I have helped about 7 people convert from Wins to Ubuntu and I tell you once they open up port 22 on their firewall I have no problem helping them with issues they had. Of course the first thing I do is change the port 22 on firewall, Ubuntu & install fail2ban, x11vnc, tightvncserver vnc4server - Fast & easy.

Cybergalves - I did install NX but I get a "Host not found" error which I posted here with no replies yet; [http://ubuntuforums.org/showthread.php?t=736509&page=9](http://ubuntuforums.org/showthread.php?t=736509&page=9)

****I followed all the steps again from beginning and I encounter 1 error when I enter;

ssh localhost

ssh: localhost: Name or service not known

I'm running this command remotely on the machine I want to control via SSH.

I'm guessing this is my main problem.

any help is appreciated***


Anyway my Display problem is probably due to the fact that I removed the Monitor and my command works but it gives me a gray color desktop.  I'm sure it would work if I add back the Monitor.

Any Suggestions??

---

### Post by dmizer on 2009-05-28
I understand the desire to avoid the terminal. But for VMware, you have a web interface: [https://help.ubuntu.com/community/VMware/Server#VMware%20Server%20MUI%20Component%20Installation%20(Optional,%20Source%20Install%20Only](https://help.ubuntu.com/community/VMware/Server#VMware%20Server%20MUI%20Component%20Installation%20(Optional,%20Source%20Install%20Only))
Just connect to your server via proxy, set your sox proxy in firefox, and you can browse to [https://localhost:8333](https://localhost:8333) to manage vmware.
For your print server: [http://localhost:631](http://localhost:631)
For your www/drupal server, there's ebox: [http://ebox-platform.com/](http://ebox-platform.com/) (available in the repos)

All of the above tools will give you as much functionality as you would get with a full desktop, and almost as much functionality as you would get from the CLI.

What doesn't work about the command I gave you? Did you get an error, or are you using SSH from a Windows machine?

---

### Post by Loan_Refi on 2009-05-28
I'm using your suggestions for VMware & Print already I did not know about ebox [http://ebox-platform.com/](http://ebox-platform.com/) but I'm on it!!

This is the error I get;

$vncviewer -x11cursor -geometry 900x700 -encodings "copyrect tight zrle hextile" localhost:0
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

---

### Post by Loan_Refi on 2009-05-28
Is ebox functionality similar to Webmin you think? I already have Webmin installed.

---

### Post by dmizer on 2009-05-28
Webmin has not been supported in Ubuntu for a while due to the fairly profound differences between Webmins config and what Ubuntu needs, so it tends to cause more problems than it solves. Ebox is being recomended as a replacement for Webmin. I have not used it, but I believe it should be functionally similar and even go beyond what you can do in Webmin.

According to that error, it simply looks like you don't have your vnc server configured correctly. Did you configure it via webmin? ;)

Edit:
There's a live CD for ebox if you'd like to test it without installing it: [http://ebox-platform.com/download/](http://ebox-platform.com/download/)

---

### Post by Loan_Refi on 2009-05-28
I did not configure vnc server via Webmin. 

What do I need to do to configure vnc server appropriately?

---

### Post by Loan_Refi on 2009-05-28
You guys are great!!!

I stumble across the fix to get my NX working.  I had a problem with permission rights to file /etc/nsswitch.conf

644 is the proper permission for that file.

Because I didn't have the right permissions I was not able to "ping localhost"

I'm now able to connect using NX Client and my display works great!

I'm not going to stop here though I'm going to fix the Display issue with VNC

dmizer - I installed ebox and looks good so I'll follow your suggestion to use ebox instead of Webmin.  My goal is to use Terminal so I'll continue to sharpen my skill to get better at it.

I'm also able to connect to VNC Server using your command;

vncviewer -x11cursor -geometry 900x700 -encodings "copyrect tight zrle hextile" localhost:1
The problem was "0" so I changed it to 1

What happens is that when I start the machine its set to login automatically but because there is no monitor its probably throwing a display error.  I still get a gray display but NX Client works good.

Thanks!

---

### Post by Loan_Refi on 2009-07-25
Okay I found the solution for VNC Headless Machine.  The reason i was getting no desktop is because all I need it to do is to add "**gnome-session &** to file /home/user/.vnc/xstartup

example;
#!/bin/sh

xrd $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
gnome-session &

I also fount a great application called **krusader** which allows me to copy files, folders & print between two remote computers while using vncviewer, this is done with "sftp". I like this app because of GUI, I know I can probably do it thru terminal too.

apt-get install krusader

NXClient from [www.nomachine.com](www.nomachine.com) is good too since it allows me to share my printers & folders.

VNC or NXClient are my solutions BUT, I Prefer VNCViewer! Fast, easy install via apt-get.!!:guitar:

---

