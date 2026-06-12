---
title: "Creating a simple way to share files over the internet"
date: 2006-06-26
forum: Desktop Environments
---

### Post by eXCeSS on 2006-06-26
Basically I'm looking to set up an ftp server my girlfriend can log into to get any number of directories that she wants. 

I've tried PureFTPd + PureAdmin but I would create users and they would just dissapear. ](*,) 

Are there any other FTP servers easy enough to set up that I could try?
Do I have any alternatives to send directories through the internets?

---

### Post by strattonbrazil on 2006-06-26
Well, I would do either of the following:

Setup a web server (like apache) and put the files I wanted to share in the /var/www/ directory.  Then put a web page with the links in that folder to.  That way to access the files, you could access the files remotely from any web browser.  

Another option that might be even easier is using scp.  scp uses your ssh daemon (which runs and is installed by default on most Linux machines).  

For example, I'm on another Linux machine and I want a file 'happy.txt' from a machine with IP address 154.23.23.13 and the file is in /home/someUser/.  From the remote machine, I would type in:

> scp [email]someUser@154.23.23.13:/home/someUser/happy.txt[/email] .

I would then be prompted for the user password for 'someUser' and the file (or files) would be copied to my directory.  For files (like you wanted), use the recursive parameter '-r'.  

> scp -r user_name@user_ip_or_user_domain_name:/path/to/what/you/want/* .

Hope that helps...  If you're trying to access it from a Windows machine, you can download a free scp utility from somewhere to do it.  This way is probably the most secure.

---

### Post by ohgod on 2006-06-26
I like vsftpd.  It's not too hard to setup:

[http://www.ubuntuforums.org/archive/index.php/t-91887.html](http://www.ubuntuforums.org/archive/index.php/t-91887.html)

---

### Post by eXCeSS on 2006-06-26
[QUOTE=strattonbrazil]words[/QUOTE]
So for that bottom method, I wouldn't really need to configure anything, just have her use an scp client and shed be able to grab stuff off me at will?

---

### Post by strattonbrazil on 2006-06-27
Right.  For scp you just need the client.  The thing that's kind of strange, though, is you can't actually browse files with scp.  It only copies.  If you look at the syntax I gave, it looks an aweful like the 'cp' copy command.  

What I usually do is login via SSH in one window to browse the files.  Then in the other window I use the 'scp' command for stuff I want to get.  There may even be a utility out there that combines the two, but I never have cared enough.

---

### Post by Endolith on 2008-05-10
> **eXCeSS said:**
> So for that bottom method, I wouldn't really need to configure anything, just have her use an scp client and shed be able to grab stuff off me at will?

But doesn't that allow people access to your entire filesystem?

---

### Post by Gordy on 2008-05-10
> **eXCeSS said:**
> Basically I'm looking to set up an ftp server my girlfriend can log into to get any number of directories that she wants. 

I've tried PureFTPd + PureAdmin but I would create users and they would just dissapear. ](*,) 

Are there any other FTP servers easy enough to set up that I could try?
Do I have any alternatives to send directories through the internets?

I would try SME Server. It has aal that you are asking for........

---

### Post by Endolith on 2008-05-10
Is there anything better than FTP?  I want to share files with a guy on OS X.  I thought of sshFTP, but that would give him access to my whole file system.  Are there any other alternatives that have free OS X clients?

---

### Post by Endolith on 2008-07-10
I got Pureadmin working.  See [http://ubuntuforums.org/showthread.php?t=684590#5](http://ubuntuforums.org/showthread.php?t=684590#5)

---

