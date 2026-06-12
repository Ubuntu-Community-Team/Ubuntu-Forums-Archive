---
title: "Setting Up A Server at Home for Remote Acess"
date: 2008-12-31
forum: General Help
---

### Post by JCoder on 2008-12-31
Hey im sorta an Ubuntu noob and have only recently started using it seriously.  I want to set up a server on my Ubuntu 8.10 machine that can have its file acessed anywhere but with the least technical problems.  I plan on only sharing the files on my external hard drive.  Im not sure to either use ftp or some apache module ive been reading about.  What would you guys recommend thanks.

---

### Post by captain_171 on 2008-12-31
what do u want to access them file on? like what computer and what kind of files are these and is this network or accost the internet
and do u wan to change these files

---

### Post by JCoder on 2008-12-31
I would want to access these files on a windows computer.  They would be .pdf's and word documents mainly.  From the client I would want to be able to upload files while also accessing them.

---

### Post by growlf on 2008-12-31
It depends a bit on what kind of access you will have at your remote sites.  Some do not allow the SSH tunneling (i.e. Microsoft) others do not allow HTTP tunneling either - and some let you free to do what ever (i.e. Starbucks).

Remember that security is at least of "some" importance here - so tunneling is probably preferred.  However, there are also web-based options depending on what kind of access YOU desire to the file system.

You could even do an rsync (or similar) mirroring solution if you need speed for local access more than anything (i.e. audio/visual file access).

Can you give some more details of the scenario?

---

### Post by JCoder on 2008-12-31
I would be using this to access my files from school.  For example if our robotics team wrote a good piece of code written that day I would want to upload it to my server from our Windows XP machine.  I think a ftp server I would be looking for because you can use it via command prompt.

---

### Post by JCoder on 2008-12-31
I found gproftpd and decided to try that but when I go to launch it nothing happens.
-this is the menu command 
su-to-root /usr/sbin/gadmin-proftpd

---

### Post by lintoon on 2008-12-31
I would look into setting up a vpn connection.  Nice and secure.
Windows has the client built in.  

Set up samba on your server to share the files you need.  Then access these files via your servers internal IP address when you are connected over your vpn.

Unfortunately I cannot advise you on which vpn server to go for because I have never done it in Ubuntu.  I do know it works in the windows world.

You would also have to set up port forwarding on your home router.

If you only want to view the files Remote Desktop is an option.  It's very simple to set up.

---

### Post by growlf on 2008-12-31
Ok.  So you have FTP (21) and probably HTTP (80) open to you, and you need r/w access.  If you are willing to use FTP you are obviously willing to accept some of the more cumbersome UI constraints that comes with it.

The Ubuntu desktop edition comes with a "share files" option (when you install the samba suite from synaptic) and you can create a SSH tunnel to allow seamless access to your Ubuntu box from your Windows computer - as you normally would in a windows enviro.  This does assume that you can pop port 22 (SSH) open in any firewalls between the two systems if they are not already open (many home routers do already allow this port).

On the other hand - qick, dirty and only somewhat less secure is the "personal FTP file share" solution that you mentioned.

The FTP solution is pretty easy on the Ubunto - sudo apt-get install vsftpd - it should be in your default repos in synaptic also.  There is a nice tutorial here:

[http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/](http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/)

and indepth info here:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup)



Remember, you can edit the vsftpd configuration file,                 **/etc/vsftpd.conf**, to                 change the default settings and that by default only anonymous FTP is                 allowed.  You WILL need to change that.

---

### Post by JCoder on 2008-12-31
Thanks for those tutorials.  When I try it on the server itself by entering 'ftp localhost' at the terminal it works fine but when I try it on my windows computer it says connected to (my servers ip adress) and then hangs.  It then says about a minute later connection closed by remote host but nothing appears on my server.  The rounter im using is a linksys di-624 and i forwarded port 21 on it to my server.

---

### Post by albinootje on 2008-12-31
> **JCoder said:**
> I would want to access these files on a windows computer.  They would be .pdf's and word documents mainly.  From the client I would want to be able to upload files while also accessing them.

I would recommend to forget about ftp, and use a combination of ssh and apache.
You can quite easily set up apache with password protected directories, and ssh is secure and flexible.

Ftp is an ancient protocol. It's fast, but can be a real pain to work with if it needs to go through firewalls. 
Apart from that it uses plain-text usernames/passwords by default which can be sniffed by others.
And ftp-servers where you allow uploads can be a potential security hazard.

I suggest the following :
1) Install openssh-server
```

sudo apt-get install ssh

```
2) Make sure your users on your machine don't use easy to guess passwords.
3) Install apache
```

sudo apt-get install apache2

```
4) Activate the public_html for apache :

[http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file](http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file) --> Step 2

5) Make parts of your public_html directory password protected if needed :
[https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

I really recommend this for ease and security reasons.

But of course it's possible that your school blocks port 22, and has 21 and 80 open.
Then you will need to have your ssh-server running on port 21 too.
That's not so difficult, ssh is really flexible, just edit /etc/ssh/sshd_config and add a new line under the line with "Port 22", so it would like :
```

Port 22
Port 21

```
Then restart the ssh-server :
```

/etc/init.d/ssh restart

```
Check whether it indeed runs on port 21 and port 22 now :
```

netstat -tan|grep 21
netstat -tan|grep 22

```

GL!

---

