---
title: "desktop and appearance setting are lost"
date: 2009-07-11
forum: Desktop Environments
---

### Post by Valde_91 on 2009-07-11
Hi!

Since yesterday every time that I boot up my HP mini all my desktop and appearance setting are reset to default. For example normally I used a customized appearance setting (a mix between the dust, clearlooks and Highcontrast icons), but since yesterday every time that I restart my system the appearance is set back to human theme. Same for the desktop: I'm used to have a grey solid color in the background, but after a reboot I've the default Ubuntu image. Also the settings for some applets in the panel are reset to default. 

I don't know if this issue is related with some updates that I've made yesterday. Besides since a 1 month when I update my system I've an error message from the "menu" package that isn't installing properly. But when I've checked in the synaptic manager this package is correctly installed. But btw this bug is there before the setting problem with the gnome desktop, and seems not to cause any problem on my system.

I'm running intrepid on my jaunty

Bye Bye Valde_91 (sorry for my english!:D )

---

### Post by prshah on 2009-07-11
> **Valde_91 said:**
> all my desktop and appearance setting are reset to default.

I'm running intrepid on my jaunty


Check if the gnome-settings-daemon is running; open a terminal (Applications-Accessories-Terminal) and give the command```
ps -e | grep gnome-sett
```

btw, you can use Intrepid _OR_ Jaunty. You can't be running Intrepid _ON_ Jaunty. (Unless you are using a virtual machine...)

---

### Post by Valde_91 on 2009-07-12
Hi thanks for the suggestion!

I discover that the partition where ubuntu is installed was full (no free space left). I deleted some files in my home folder, reset all the configuration of the desktop and now is all working fine. 

I'm running jaunty on my machine,..I don't know why I don't have noticed the error when I have checked my message before posting it!:D:D 
This is the proof that this Murphy's law is correct : "Proof-read all e-mails three or four times before sending it. All errors are detected immediately after being sent" 

Bye bye valde_91

---

### Post by DonLuke on 2009-07-26
[QUOTE=Valde_91;7603210]Hi thanks for the suggestion!

I discover that the partition where ubuntu is installed was full (no free space left). I deleted some files in my home folder, reset all the configuration of the desktop and now is all working fine. [ QUOTE]

I had the same error but after freeing space the behaviour didn't change. What do you mean with "reset" the configuration?

---

### Post by Nikos.Alexandris on 2009-09-23
(
I accidentaly erased what I have posted _here_ before!
)

I (also) experienced loss of appearance settings only to find out that my /home/nik directory was full. I freed-up some space, re-set desktop settings and all is fine.

Idea submitted: [http://brainstorm.ubuntu.com/idea/21664/](http://brainstorm.ubuntu.com/idea/21664/)
Regards, Nikos

---

### Post by Nikos.Alexandris on 2009-09-23
> **DonLuke said:**
> [QUOTE=Valde_91;7603210]Hi thanks for the suggestion!

I discover that the partition where ubuntu is installed was full (no free space left). I deleted some files in my home folder, reset all the configuration of the desktop and now is all working fine. [ QUOTE]

I had the same error but after freeing space the behaviour didn't change. What do you mean with "reset" the configuration?

I think by "reset" it is meant to re-set the preferences (appearance and more) manually again (of course after having free space again). That's what I had to do. Free-up space, setup again stuff like background, links for places in nautilus, terminal profiles, etc.

---

### Post by alfu on 2009-09-26
Having a very similar problem.

A Youtube video I was watching (entitled Vista vs Ubuntu) with a rap song background wouldn't let me switch to another video, so I just shut down Firefox.  I suspect the poster of the video had inserted rogue Javascript code into his submission.

Next time I booted up I noticed my font size preferences were screwed up, along with missing options on the log out menu (and still won't come back even if I reset them).  Now, when I select the System/Preferences/Appearance option, the font sizes instantly come back, but the logout menu still has missing items.  No problem with space; the filesystem has 23GB extra space.  

Did I catch a virus from Youtube?  I suspect I should do a complete re-install which I hate to do because I have downloaded and installed several apps.

Reply to Nikos:  The /home directory is NOT a separate directory, it is a folder on the File System; the object's Properties lists a name of "/" and 25GB of free space.  Are you implying, Nikos, that had I mounted a separate partition (it would have to be logical) at the "/home" mountpoint, that I could do a Ubuntu system re-install and not destroy any user accounts? (Thanks in advance)

---

### Post by Nikos.Alexandris on 2009-09-26
> **alfu said:**
> ...
No problem with space; the filesystem has 23GB extra space.
...

Do you use a separate partition for your "/home"? Are you sure all of your partitions are NOT full?

---

### Post by Nikos.Alexandris on 2009-10-13
> **alfu said:**
> 
Reply to Nikos:  The /home directory is NOT a separate directory, it is a folder on the File System; the object's Properties lists a name of "/" and 25GB of free space.  Are you implying, Nikos, that had I mounted a separate partition (it would have to be logical) at the "/home" mountpoint, that I could do a Ubuntu system re-install and not destroy any user accounts? (Thanks in advance)

(
IMHO, I think it is better to reply by quotting in a new post than editing a post
)

The /home is by default within the filesystem. This does not mean that you can't make it to be a separate partition :-). I do have a separate partition for /home.

The advantage is that, yes, you can re-install the system and keep at the same time user-settings.

Phh... it's two weeks ago and I don't remember why I asked you about a separate partition :-p. I guess I thought you did have a separate partition and the reported free space  (23GB as you posted) was not referring to the /home.

Anyhow, hope you solved the problem already.
Cheers, Nikos

---

### Post by alfu on 2009-10-14
Thanks Nicos, but problem yet un-solved.

Before installing Ubuntu, I specifically set some logical partitions to  "/home" and "/user" mountpoints as choices with the popup menu in GPartEd.

However, the installer ignored these, and the installed Ubuntu OS desktop does not even acknowledge that they exist.

These directories exist as folders within "/", contrary to my intent.

---

### Post by Nikos.Alexandris on 2009-10-14
> **alfu said:**
> Thanks Nicos, but problem yet un-solved.

Before installing Ubuntu, I specifically set some logical partitions to  "/home" and "/user" mountpoints as choices with the popup menu in GPartEd.

However, the installer ignored these, and the installed Ubuntu OS desktop does not even acknowledge that they exist.

These directories exist as folders within "/", contrary to my intent.

Well, let's try the following:

What does the command "mount" report?
What does the command "df" report?

Both without any parameters.

---

