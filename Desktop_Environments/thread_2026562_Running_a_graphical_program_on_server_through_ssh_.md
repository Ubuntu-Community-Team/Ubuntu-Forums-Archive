---
title: "Running a graphical program on server through ssh and not closing it when leaving?"
date: 2012-07-15
forum: Desktop Environments
---

### Post by Beto on 2012-07-15
Hi all. Here is my situation.

I have an ubuntu server which I only connect to through ssh.
I installed wine on it in order to run Metatrader (a trading platform). After some tweaking I managed to get it to run.

My problem is that I need to start the program from another ubuntu pc, use it and then keep it running even if the ssh connection is lost. Then I should be able to reconnect to the program.

How should I go to accomplish this. I read some tutorials on internet but couldn't find the right answer for me.

Right now I start the program with "ssh -X", but I can't let it running when the ssh connection is closed.

Any help would be greatly appreciated.

Regards,
--
Beto

---

### Post by sanderj on 2012-07-15
You can have a look at "nohup". First run 'man nohup'.

HTH

---

### Post by papibe on 2012-07-15
Hi Beto.

Since you are forwarding the application over ssh, the ssh connection **must** exist in order for the application to run.

Another solutions might be:
[LIST]
[*]If Metatrader has a non-gui server component that you can run on the remote machine, then you could leave that running there, and connect using a client over a predetermine port.
[*]Don't forward the application but run it in graphically on the local machine. Then you can use a remote GUI connection to connect to the desktop and check the application. You could use Ubuntu's remote desktop viewer for that (check [here]("https://help.ubuntu.com/community/Vinagre"), and [here]("http://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/")).
[/LIST]

I hope that helps, and let us know how it goes.
Regards.

---

### Post by markbl on 2012-07-15
Run metatrader in a local vnc server then connect to it remotely using a vnc client tunnelled over your ssh connection. If you want to run metatrader in the normal console ubuntu session, then perhaps use X11vnc to capture that session in VNC. Do "apt-get install X11vnc" and then read "man x11vnc" for all the verbose details, including how to use it via the ssh tunnel.

PS edit: if you do this, then login with a 2D desktop as 3D desktops perform poorly over VNC.

---

### Post by Beto on 2012-07-15
> **papibe said:**
> Hi Beto.

Since you are forwarding the application over ssh, the ssh connection **must** exist in order for the application to run.

Another solutions might be:
[LIST]
[*]Don't forward the application but run it in graphically on the local machine. Then you can use a remote GUI connection to connect to the desktop and check the application. You could use Ubuntu's remote desktop viewer for that (check [here]("https://help.ubuntu.com/community/Vinagre"), and [here]("http://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/")).
[/LIST]

I hope that helps, and let us know how it goes.
Regards.

I guess your answer is closest to what I need. But...
How would I start the application graphically on the local machine without being on the  local machine? I'd need to start the graphical server ('X')? how??? I'm lost.

Regards,

---

### Post by LewisTM on 2012-07-15
Use **xpra** in combination with GNU **screen**.
First start an Xpra server via ssh or at startup on the server
```
xpra start :7
```
Then log in by ssh and start your program through screen 
```
DISPLAY=:7 screen -q
<metaserver command> &
```
You program will have launched on display :7, which you can access locally by running this in a _second_ terminal.
```
xpra attach ssh:user@server:7
```
At any time you can detach from the screen session and logout by typing Ctrl-A then D D. The program will continue to run because screen does not terminate on logout. It will not have lost its connection to X since xpra, not ssh -X, holds it.
To reconnect to the screen session and do other things, you can log in by ssh and run
```
screen -R
```

I hope this is not too complicated. At least you can expect good performance and quite a bit of flexibility.

Cheers!

---

