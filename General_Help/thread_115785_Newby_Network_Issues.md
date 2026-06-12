---
title: "Newby Network Issues"
date: 2006-01-11
forum: General Help
---

### Post by Traveller54 on 2006-01-11
Hello All,

Please excuse if I am covering an old subject but I have spent days 'googling' and searching without luck:

Question: I installed 5.04 then upgraded to 5.10 I would now like to connect to a windows workgoup (home) network to gain printer support (on two winXP machines)
I have read and tried a whole bunch of stuff but all assume I am a Linux Boffin where in truth I feel like an idiot and that is from one who has been in the industry for over 30 years.

If you can point me to a basic turorial that does the trick it would be great or some for of step by step guide.
Many thanks in advance

---

### Post by Thirsteh on 2006-01-11
It'd be easier, in my opinion, if you quoted a tutorial you're having troubles with and then let us guide you through whatever steps you do not understand. Also, which is the computer with the printer, the Linux box or the windows box(es)?

---

### Post by deNoobius on 2006-01-11
I'm pretty new too, hello and welcome!  

[http://www.ubuntuforums.org/showthread.php?t=76647](http://www.ubuntuforums.org/showthread.php?t=76647)

Check out the "Customization Tips and Tricks" section of the boards.  It has a lot of these types of tips for setting up Ubuntu.  Also, consider using Automatix--it makes the initial setup a breeze. It is a very elaborate script that does a lot of setup and customization tasks automatically.  First, find the Automatix thread (I believe it is also in Customization Tips and Tricks) and read up on it.

---

### Post by Traveller54 on 2006-01-11
Ok the windies boxes have the printers and the linux box is actually a dual boot ubuntu/winXPSP2:
Apart from printers I would also like to share files.
They are networked via a switch.
I have installed samba and have worked through this article.
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba). I see the linux box on the windies workgroup but I get an error when trying to access the box before even being asked for user and pswd
Thanks

---

### Post by deNoobius on 2006-01-11
You have to set the user to "shared" in the smb.conf file.  See the article I pointed you towards above.  Also, make sure file sharing is on on the Windows box.

---

