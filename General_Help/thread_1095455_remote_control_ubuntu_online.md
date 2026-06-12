---
title: "remote control ubuntu online"
date: 2009-03-13
forum: General Help
---

### Post by dellboy on 2009-03-13
i am looking for something like logmein that i can use from a mac or windows or even a Liunx computer to control  my ubuntu computer as if i was sat in front of it but i need it to be online based as a lot of the time a firewall or router will block me from  using a client to control  it. i need it to be an online website so it can be used  anywhere  i have a internet connection.
 free would be great but i am open on this one as long as it not high 

as i have this set up as a file server as well as a desktop computer so yes i am using the desktop version so at times i may need to change a few small things in the gui ;) 
thank you for your help:D

---

### Post by LegendofTom on 2009-03-13
I think what you are looking for is "webmin"

---

### Post by Tobywuk on 2009-03-13
There are two major, widley used protocals that can do this. these are

SSH and  VNC

ssh - Once you have install an ssh server (openSSH-server) on the system you wish to connct to all you have to do in the terminal is type 'ssh  username@ipaddress' hit return and you will effectivley be prompted with a terminal on the remote system on your local system. this is also much more powerfull, allowing you to use tunnels, scp for file transfers etc.. etc...   SSH clients are build into linux and OSX out of the box and on windows you will need a program called putty to connect to an SSH server.

VNC - A protocal, similer to microsoft remote desktop, that lets you effectivly see and controle a remote system. Cross platform, you will need VNC server software installed on the system you wish to controle and a VNC client on the system you wish to connect from and controle the server.  Im sure other users can help on the names of recommended software - I dont really use VNC.

Good luck!

---

### Post by dellboy on 2009-03-14
i don't think webadmin is the right thing. i am  here as i all ready have a file server set up with nettalk for my mac and other software so my Liunx computers and windows can see it on  my home based network only. i think what i am looking for is somthing like Tobywuk said i have used vnc before but i don't think its going to help me for where i may need to use it as they block the port that vnc uses. i could get around it by using ssh as i have a server set up where i can login to ssh to any server but i dont think you can see the gui with ssh can you ? its just command line  

cheers again guys for your help and i will keep webadmin in mind for when i need to set up a full running server :) saves me getting a nother box to do this
> **LegendofTom said:**
> I think what you are looking for is "webmin"

---

### Post by Tobywuk on 2009-03-14
If a firewall is blocking the VNC port you could just change the Port VNC uses to one that is open and works.

SSH is command line, although with the -x command you can use a GUI with a program your running.  

Another option is SSH Tunneling. If ssh Works then you can use this ssh connection and pass all your other traffic through it, including your VNC session.

---

### Post by dellboy on 2009-03-15
ok i have found a program called JollysFastVNC for my mac and using vnc for the rest of the computers but what i want to now at the moment JollysFastVNC is finding it as i am on the network but what host name would i use when i am not at my house ?

i tryped tpying in ifconfig but i am not sure if anyone of them ips are right :D

thank you again for your help

---

