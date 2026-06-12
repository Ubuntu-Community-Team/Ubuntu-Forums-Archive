---
title: "VNC when not logged in"
date: 2005-12-29
forum: Desktop Environments
---

### Post by crossfireit on 2005-12-29
I am reasonably new to linux but espcially new to Ubuntu, having said that what i have seen i like very much, seems like a great distro.

I am running a headless machine and Ubuntu does not seem to like my KVM. However i also do alot of work at home to the office which is where my linux box is. 

I have loaded the VNC server and can operate it from my windows machine but only if their is a user logged onto the linux machine all the time. As there are more than just one person using this machine i wish you be able to VNC into the computer and get the login screen so you can choose who you log in as. 

I would find it wierd if Ubuntu did not allow this but i cant work it out. 

I dont care about having mutilple people logged in, i just want to be able to VNC into the machine, log in and then log out. 

Thanks in advanced.

---

### Post by pharcyde on 2005-12-29
I'm assuming you have the vnc server start when you have a user login.  To have the server start at boot up create a script to launch the vnc server in /etc/init.d folder and use a program to change the run level of the script.  There may already be an existing script if you installed the vnc server using apt-get. If this is the case then just change the run level of the existing script to start during boot up.

try:
[B]
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
[/B]

After sysv-rc-conf is running change the vnc script to startup during boot.

---

### Post by stevea1210 on 2005-12-29
[http://ubuntuforums.org/showthread.php?t=76638&highlight=vnc+xdmcp]("http://ubuntuforums.org/showthread.php?t=76638&highlight=vnc+xdmcp")

The above thread may be what you're looking for.  When you vnc to the machine, you will be greeted with gdm to log into the box.

---

### Post by crossfireit on 2005-12-30
I have tried that post the you mentioned to no avail, when i reboot and do i netstat i see nothing listening on port 5091 so i can only assume that it is not running, however if i start something like vncserver and it says that it starts i still dont see it listening on the correct port. 

Should there be something there listening, i can only imagine it has to be.

---

