---
title: "help a noob with his server"
date: 2009-06-05
forum: General Help
---

### Post by creamcheeze77 on 2009-06-05
I was given a dell poweredge 860 recently, and outfitted it with ubuntu server 9.04 and samba, and i've been using it as a fileserver.  It's up and running great on my local network.  Basically, I want to be able to access it from remote locations (i.e.) the web, securely.  Seeing as I'm fairly inexperienced with Linux, what's the best program setup to do this with?  The machine I'm accessing it with is running Windows.  Thanks guys.

---

### Post by creamcheeze77 on 2009-06-05
oh, i forgot, SSH is also set up, if it matters, but apache/ web programs are not.

---

### Post by Soul-Sing on 2009-06-05
A fair/honest answer?
Reading, reading & reading. Lots of wiki and howto's.

---

### Post by albinootje on 2009-06-05
> **creamcheeze77 said:**
> Basically, I want to be able to access it from remote locations (i.e.) the web, securely. 

You want to access the files just for copying and editing ? 
And/or you want to maintain it (with a GUI) ?

For file access I suggest running ssh on the server, with WinSCP as the client in MS-Windows. 
(sudo apt-get install ssh)
Make sure that you use strong passwords, and use the AllowUsers option in sshd_config to restrict access to the account.
Running ssh on a different port than port 22 is also an idea.

For commandline administration you can use Putty in MS-Windows.

For clients see also here :
[https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo](https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo)

See also : [https://help.ubuntu.com/community/SSH/](https://help.ubuntu.com/community/SSH/)

---

### Post by Boondoklife on 2009-06-05
While I agree with Leoquant, I will point ya in two directions. You can look into ssh port forwarding and also VPN, either will give you the effect you are looking for.

---

### Post by mixmaster on 2009-06-05
Do you want read-only access or application level access or administration access?

ssh should be your main tool.  If you only want limited access you can set up the remote accounts to use rbash (restricted bash) which will confine them to certain directories and/or certain commands.

If you want to run apps you could set up accounts where the application is run immediately on login and the access is closed when the app is shut down.

For administrative access, use strong passwords, strict checking and rsa keys to restrict login.  Back door (unusual ip ports) may also be used.

---

### Post by albinootje on 2009-06-05
> **mixmaster said:**
> 
ssh should be your main tool.  If you only want limited access you can set up the remote accounts to use rbash (restricted bash) which will confine them to certain directories and/or certain commands.


Quite a while ago I read that rbash is not a good tool for "real" restrictions, (I thought it had to do with rbash users being able to export the full PATH anyway).. has that changed in the meantime ?

For restrictions on "application" level I would recommend scponly as quickest and easiest solution (although on the other hand applying chroot for scponly is a little cumbersome, but.. it does restrict access via scp and sftp only), or the chroot option from openssh itself.

See here for a howto : [http://ubuntuforums.org/showthread.php?t=1057657](http://ubuntuforums.org/showthread.php?t=1057657) but.. make sure the needed openssh version is used (Doesn't work for older openssh versions).

---

