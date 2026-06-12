---
title: "log in without typing password"
date: 2009-01-05
forum: Desktop Environments
---

### Post by JohanSwe on 2009-01-05
I want to allow the users of this computer to log in without typing any password. The user accounts should have a password and the password should be used whenever necessary when the user is logged in (e.g. sudo).

Can I do this?

---

### Post by Tamlynmac on 2009-01-05
For each user.
Login Window Preferences/Security Tab/ (check) Enable Automatic Login

---

### Post by zika on 2009-01-11
*

---

### Post by overdrank on 2009-01-11
[Forums policy]("http://ubuntuforums.org/showthread.php?t=716201") on log-in-as-root tutorials
> Policy
Tutorials explaining how to enable the root account for a graphical login or** autologin **will not be supported on the forums and will be moved to the Jail. Although we believe people should have the freedom to run their computers however they want, we also believe in supporting Ubuntu's security model. You can find or post information elsewhere on the internet regarding graphical Ubuntu root logins; such tutorials do not have to be hosted on the Ubuntu Forums.

---

### Post by zika on 2009-01-11
it seems that I've been cautioned. I did not have any intention to break any kind of policy so I will be grateful if You could delete my message and I will not repeat my question again. 

this was a genuine question.

I was eager to see what went wrong (or did it in the first place) on my current install and by no means did I want any information that (I thought) could be seen as inappropriate.
[B]
*overdrank*[/B]*:we also believe in supporting Ubuntu's security model *

I **do** believe in the model and that is why I was asking that question. something is wrong and both sides could learn from this. the only machine I want to use that is my own in a room that is used only by me ... but, never mind. 

I will erase the contents of message and I hope admins will erase the message itself. Done. 

no hard feelings from my side and I hope the same stands for the other side .

***(why did You wait with the caution since I'm not the original poster of the thread?)***

---

### Post by lswb on 2009-01-11
Do you want the system to boot to a login screen where it asks for the user name, but doesn't wait for a password? Or do you want the system to boot directly into a user session without any gui login? Or maybe something else? Not sure exactly what you are asking for here.

---

### Post by zika on 2009-01-11
> **lswb said:**
> Do you want the system to boot to a login screen where it asks for the user name, but doesn't wait for a password? Or do you want the system to boot directly into a user session without any gui login? Or maybe something else? Not sure exactly what you are asking for here.
to **overdrunk**:now I'm not sure if I'm allowed to continue. I sure did not plan to, but it is now rude not to answer to *lswb* once he offered his help ... (since this is a legitimate option in a GUI I do not see what am I doing wrong but, I'm sure, You will correct me if I'm wrong) (also, since I'm the only one that is cautioned and there are other threads on this matter I am getting more and more confused ... in the other threads (for example:
[http://ubuntuforums.org/showthread.php?t=1033204&highlight=%2Fetc%2Fgdm%2Fgdm.conf]("http://ubuntuforums.org/showthread.php?t=1033204&highlight=%2Fetc%2Fgdm%2Fgdm.conf") 
[http://ubuntuforums.org/showthread.php?t=1011488&highlight=%2Fetc%2Fgdm%2Fgdm.conf](http://ubuntuforums.org/showthread.php?t=1011488&highlight=%2Fetc%2Fgdm%2Fgdm.conf)  
[http://ubuntuforums.org/showthread.php?t=970611&highlight=%2Fetc%2Fgdm%2Fgdm.conf](http://ubuntuforums.org/showthread.php?t=970611&highlight=%2Fetc%2Fgdm%2Fgdm.conf) 
[http://ubuntuforums.org/showthread.php?t=907590&highlight=%2Fetc%2Fgdm%2Fgdm.conf](http://ubuntuforums.org/showthread.php?t=907590&highlight=%2Fetc%2Fgdm%2Fgdm.conf))
specific files are mentioned (exactly one I've mentioned in my post that triggered for Your caution, I suppose) and ways how to manipulate with them... there are many threads where the problem of changing root password is discussed promoting the use of Live CD for that purpose e.t.c.)

to **lswb**:You've asked and I'll just answer. if its inappropriate, I will clear my message again.

at the very beginning I was able to make my machine go directly into my user on boot. it worked perfectly for some time. once I've been playing with apt-p2p and similar stuff I needed to kill before I've got into the X-session (at that time I did not want to remove them from the system, now I did that) it stopped working ... I thought that I was to blame with my tinkering so ...

now everything is (as much as I know, obviously not) as it was at the time before apt-p2p (it is gone since it used too much of my network and too much of my resources so I had to wait for it to finish what it was doing to do my own work ... ;( ). the only thing that is not back to 'normal' is the fact that, even though I have it set right in GUI, I have to log-on on every boot. not much of a problem since its only one or two times a day, but I just wanted to check if somebody knows the reason. I've looked at the appropriate 2 files and looked fro that option in them, everything is OK. bookkeeping is OK.

to **lswb: **I've written this post just because I felt that it would not be nice to You, once You offered Your help, to leave Your question unanswered. please excuse me for being so detailed about stuff that does not involve the problem You wanted to help me on.

---

### Post by lswb on 2009-01-11
I think there was some misunderstanding in the previous posts. I see nothing in your request that conflicts with forum policy.

If you want your system to login automatically to a users desktop, try
/Main Menu/System/Administration/Login Window/Security, check off the "Enable Automatic Login" box, and select the desired user.

---

### Post by zika on 2009-01-11
> **lswb said:**
> I think there was some misunderstanding in the previous posts. I see nothing in your request that conflicts with forum policy.
neither did I. glad we've agreed on that. I'm sorry if I've made any turbulence here with my question. 
> **lswb said:**
> If you want your system to login automatically to a users desktop, try
/Main Menu/System/Administration/Login Window/Security, check off the "Enable Automatic Login" box, and select the desired user.
I've tried that for numerous times. it doesn't work.it does not update the appropriate file accordingly, it add empty lines and put options in random order. I've edited /etc/gdm/gd.conf-custom numerous times but with no luck. once I've managed to get timed login but that is all. that file was full of empty lines and I've cleared it but that did not help. I've temporarily removed /etc/gdm/gdm.conf but that made any login impossible, so I've returned it back to its place. I'll try timed login once more and than give up because all the time for a couple of years I could save by not typing user-name and password is already spent ... ;) it worked several weeks ago but now its gone. never mind, if somebody comes with a different solution I'll be ready to test it.

**UPDATE: **I've found the culprit: **preload 0.6.3**. once it was removed from the loop everything works! still, there is a problem with the way how GUI updates the file /etc/gdm/gdm.conf-custom. it is not right. it adds blank lines in that file, leaves unnecessary lines with options that depend on removed options ... thank You all!

---

