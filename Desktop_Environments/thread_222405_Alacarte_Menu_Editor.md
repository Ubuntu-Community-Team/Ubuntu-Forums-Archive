---
title: "Alacarte Menu Editor"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Techman010 on 2006-07-24
When ever I add an entry to the alacarte menu editor, check it, and then click close, it doesn't show up.  When I go back into alacarte, it is not there.  Any suggestions?  I am using Ubuntu 6.06.

Thank you.

---

### Post by mempf on 2006-07-25
> **Techman010 said:**
> When ever I add an entry to the alacarte menu editor, check it, and then click close, it doesn't show up.  When I go back into alacarte, it is not there.  Any suggestions?  I am using Ubuntu 6.06.

Thank you.

Both my and a friend have this exact same issue.

Help needed.

Thanks

---

### Post by shawnrgr on 2006-07-26
i hate alacarte menu editor. it is for the birds. we need some bug fixes or lets get a new menue editor for ubuntu.

---

### Post by Techman010 on 2006-07-26
> **shawnrgr said:**
> i hate alacarte menu editor. it is for the birds. we need some bug fixes or lets get a new menue editor for ubuntu.


Yeah, I like the interface of alacarte, but it needs to work.

---

### Post by Uncle Spellbinder on 2006-07-26
Just my 2 cents...

I've been using Ubuntu Dapper Drake 6.06 LTS for nearly a month. Needless to say, tweaking things to my liking was first on my agenda. I used *Alacarte Menu Editor* from day one to get the menu "personalized" just right. I still tweak the menu periodically using *Alacarte*. Never had a problem. Excellent tool. In my case anyway.

---

### Post by Cosmik Debris on 2006-08-05
Try starting running alacarte from a terminal, you should get an error message.

I had the same problem, and the cause was that ~/.local and its subfolders were owned by root.
Just had to change the owner and it worked fine.

---

### Post by Anduu on 2006-08-05
I use Alacarte and for the most part it works very well....make sure you are using the latest version 0.9

Unfortunately it seems Alacarte may have been abandoned as the 3rd party Alacarte forum was closed and has since been deleted :(

Anywho if you don't have the latest version I still have the 0.9 deb hanging around...

Until something else comes along I will keep using it.

---

### Post by Techman010 on 2006-08-06
Cosmik Debris: That's my problem.  When I ran it in the terminal, it said that it couldn't access the ~/.local directory.

How would I change the ownership of the folder?  

I tried chown, and cd (just to access the folder) (with sudo) but was getting errors. (I'm have been using Ubuntu\Linux for about 2 weeks.) 

Thanks a lot.

---

### Post by Cosmik Debris on 2006-08-06
Try this :

cd ~
sudo chown -R user:group .local

(replace user with the username you used to login, and group with the name of the group your user belongs to)

---

### Post by Techman010 on 2006-08-06
That worked.  Thanks a lot.  Alacarte works perfectly now.

---

### Post by paulvandenberg on 2006-08-06
> **Anduu said:**
> 
Unfortunately it seems Alacarte may have been abandoned as the 3rd party Alacarte forum was closed and has since been deleted 

I think quite the opposite has happened. From what I understand, Alacarte has been officially made a part of GNOME for version 2.16. Perhaps the forum has been closed because it is no longer a third-party project.

Paul

---

### Post by saracen on 2006-08-07
Does anyone know where to get the deb for version 0.9 from?  The link on the project website is down...

---

### Post by Anduu on 2006-08-07
Here Ive uploaded a copy to my site...

[http://members.shaw.ca/anduu/ubuntufiles/alacarte_0.9-0ubuntu1~amaranth_all.deb](http://members.shaw.ca/anduu/ubuntufiles/alacarte_0.9-0ubuntu1~amaranth_all.deb)

---

### Post by Anduu on 2006-08-07
> **paulvandenberg said:**
> I think quite the opposite has happened. From what I understand, Alacarte has been officially made a part of GNOME for version 2.16. Perhaps the forum has been closed because it is no longer a third-party project.

Paul

Hmmm I was not aware of that...

Edit:I notice the one in synaptic is only 0.8...it was quite buggy for me.

---

