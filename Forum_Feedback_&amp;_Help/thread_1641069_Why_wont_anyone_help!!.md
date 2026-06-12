---
title: "Why wont anyone help?!?!"
date: 2010-12-08
forum: Forum Feedback &amp; Help
---

### Post by mristok on 2010-12-08
I have been interested in deploying an ubuntu server for some time now. But I need to be able to access computers on the network remotely, not **[COLOR=#ff0000]remote[/COLOR]** connection to the server itself. Can ubuntu (as is) support as a **[COLOR=#ff0000]remote[/COLOR]** access server to windows machines on the network? Is there a third party developer that supports this function? 

Also, I have an FTP server offsite, and am wondering the best and fastest file transfer way to keep the two synced.

Thanks ahead of time!

---

### Post by Quackers on 2010-12-08
You are asking questions on a specialised subject. Most people will not know the answers :-)
I'm sure somebody will be along to answer you, but you need to bear in mind that people around the world are on different clocks and therefore not necessarily awake when you are :-)

---

### Post by strixy on 2010-12-08
In regards to the title of this thread, "Re: Why wont anyone help?!?!"

I'm having trouble trying to figure out your request. Maybe you could rephrase your question? If you're coming from a Windows or Mac background, it might be helpful to explain what software you've used in the past to accomplish your goal.

As far as connections between computers, Ubunut offers plenty of options. You can look at creating a Samba share (similar to network sharing in Windows. Same as Mac), an SFTP server  is similar to FTP, SSH is another good example to get command line access to a server. For remote desktop tools look into RDP or VNC.

Maybe do a little research on each of the above and then try to expand on your question a little further? Good luck!

You may not be aware, but google.com/linux will filter your search to Linux topics.

---

### Post by lisati on 2010-12-08
Moved to "Forum feedback and help"

As has been suggested, your [other thread]("http://ubuntuforums.org/showthread.php?t=1639262") deals with a subject that not everyone might be able to help with.

---

### Post by coffeecat on 2010-12-08
@mristok, your thread is 2 days old and has disappeared off the radar. It's OK to bump it once a day in the hope that someone who can help will see it.

Good luck, but as others have said, yours is a specialist problem.

---

### Post by e79 on 2010-12-08
Strixy Wrote:
> In regards to the title of this thread, "Re: Why wont anyone help?!?!"
I'm having trouble trying to figure out your request. Maybe you could rephrase your question?

+ 1..the post is confusing...starting at :

Mristok Wrote:
> But I need to be able to access computers on the network remotely, not remote connection to the server itself.

..So do I undertand that you intend to work FROM the server console OR RDP session (still on the server) and THEN you want to RDP into other Windows machines on your network ? If so, you must first know that Ubuntu Server comes with no GUI at all. If you want one, you will have to install it ([https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)   in example).
Ubuntu Desktop on the contrary, that has a GUI, have an embedded Terminal Server Client to be able to RDP into Windows. I guess that this client could be installed on the server if you first install a GUI..but I never tried it...In any cases, if that was not the issue then I dont understand the question.

Mristok Wrote:
> Also, I have an FTP server offsite, and am wondering the best and fastest file transfer way to keep the two synced.
As for Synchronisation, maybe that 'RSYNC over SSH' would work for you, assuming that you installed both on the FTP server as well. You can always look at something like 'LFTP' ([http://lftp.yar.ru/](http://lftp.yar.ru/)) as well, can't hurt.

Hope this helps

---

### Post by e79 on 2010-12-10
I like how the OP doesn't even bother to answer our posts..... :?

---

### Post by lisati on 2010-12-11
> **e79 said:**
> I like how the OP doesn't even bother to answer our posts..... :?

Even on the OP's [support thread]("http://ubuntuforums.org/showthread.php?t=1639262"), which seems to have had some replies since this thread was started..... :)

---

